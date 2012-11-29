---
layout: post
title: "How to Solve a 403 Nginx File Download Permission Error"
date: 2012-11-28 18:20
comments: true
categories: 
---
Once the basic functionality of our [assignment.io](http://assignment.io) website was implemented, one of the features that we wanted to implement was file upload and download.  The basic upload functionality was surprisingly easy to implement using a gem called [CarrierWave](https://github.com/jnicklas/carrierwave).  The Github page has a pretty thorough walk-through, but if you’re looking to display the content on your website there is a [Railscast](http://railscasts.com/episodes/253-carrierwave-file-uploads) on the file upload process.  Both will walk you through the steps of setting it up, and it took us about 20 minutes.  

File download was a bit more complex.  While an individual user would only upload one file to be associated with an assignment, the person who assigned the assignment would probably want a way to download all of the submitted work at once.  For this, we implemented a gem called [RubyZip](https://github.com/aussiegeek/rubyzip). If you’re writing a rails app, you don’t need to require ‘rubygems’, but you DO need to require ‘zip/zip’ in your application.rb file.  

The RubyZip documentation(http://rubyzip.sourceforge.net/) is pretty dense, but thorough.  With a few modifications, we passed it an array of files, specified the file names, and created a file tree structure so that when the user downloaded the files,  they were organized by submitter and named appropriately.  

{% codeblock [Submission Model Code] [lang:ruby] %}
def self.zip_files(submissions)
    zipfile_name = "#{Rails.public_path}/download/assignments/assignment_#{submissions.first.user_assignment.assignment.id}.zip"
    File.delete(zipfile_name) if File.exists?(zipfile_name)
    zip_file = Zip::ZipFile.open(zipfile_name, Zip::ZipFile::CREATE) do |zipfile|
      submissions.each do |submission|
        # Two arguments:
        # - The name of the file as it will appear in the archive
        # - The original file, including the path to find it
        file = submission.submitted_file
        if file.path
          filename = file.path.gsub(/.+\/[^\/]/,'')
          zipfile.add("assignment_#{submissions.first.user_assignment.assignment.id}/#{submission.user_assignment.user.name}/#{filename}", file.path) if file.url
        end
      end
    end
    zipfile_name
  end
{% endcodeblock %}


Everything worked on our local host, but when we deployed to our server we got an Nginx 403 permissions error. {% img right /images/chmod/nginx.png  'Nginx Error' 'Nginx Error' %}
Once we SSH’ed into the server, we saw that the file was being created, but while the owner of the file was allowed to read and write the file, no one else could do anything with it.* 

{% img left /images/chmod/permissions.png  'Bad Permissions' 'Bad Permissions' %}

Much like you can run chmod in your bash window, Ruby also contains a chmod command.  By adding one line to our code,  we modified our permissions and allowed the user to download the file appropriately. 

{% codeblock [Submission Model Code with permissions] [lang:ruby] %}
def self.zip_files(submissions)
    zipfile_name = "#{Rails.public_path}/download/assignments/assignment_#{submissions.first.user_assignment.assignment.id}.zip"
    File.delete(zipfile_name) if File.exists?(zipfile_name)
    zip_file = Zip::ZipFile.open(zipfile_name, Zip::ZipFile::CREATE) do |zipfile|
      submissions.each do |submission|
        # Two arguments:
        # - The name of the file as it will appear in the archive
        # - The original file, including the path to find it
        file = submission.submitted_file
        if file.path
          filename = file.path.gsub(/.+\/[^\/]/,'')
          zipfile.add("assignment_#{submissions.first.user_assignment.assignment.id}/#{submission.user_assignment.user.name}/#{filename}", file.path) if file.url
        end
      end
    end
    File.chmod(0775, zipfile_name)
    zipfile_name
  end
{% endcodeblock %}

Returning to the server, you can see that the permissions were appropriately modified, and the user can now download the Zip file of all the files for an assignment.
{% img left /images/chmod/goodpermissions.png  'Good Permissions' 'Good Permissions' %}
The built-in site functionality works as well.




*[This is a great explanation of file permissions in Unix.](http://www.dartmouth.edu/~rc/help/faq/permissions.html) For purposes of simplicity, I've abstracted away the routing and controller functionality that calls the above method.*