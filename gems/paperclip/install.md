Paperclip
=========
Paperclip is intended as an easy file attachment library for ActiveRecord. ImageMagick must be installed.

ImageMagick
===========

Paperclip must have access to ImageMagick. To ensure that it does, on your command line, run:

```
which convert
```
 (one of the ImageMagick utilities). This will give you the path where that utility is installed. For example, it might return /usr/local/bin/convert.

Then, in your environment config file, let Paperclip know to look there by adding that directory to its path.

In development mode, you might add this line to config/environments/development.rb):

Paperclip.options[:command_path] = "/usr/local/bin/"
