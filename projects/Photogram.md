#run
* rails new Photogram

* then install:

rspec-rails
capybara
factory_bot_rails

* build basic test
creating_new_posts_spec.rb

* generate controller for posts
bin/rails g controller posts

* install haml gem

* add haml files for new and index

* install simple_form gem

* set up form at new and add @posts to new controller

* create Post model
bin/rails g model Post caption:string

* migrate DB
bin/rails db:migrate RAILS_ENV=test
bin/rails db:migrate RAILS_ENV=development

* install ImageMagick for use with paperclip

* gem "paperclip", "~> 5.2.1"

```
Paperclip is now compatible with aws-sdk >= 2.0.0.

If you are using S3 storage, aws-sdk >= 2.0.0 requires you to make a few small
changes:

* You must set the `s3_region`
* If you are explicitly setting permissions anywhere, such as in an initializer, note that the format of the permissions changed from using an underscore to using a hyphen. For example, `:public_read` needs to be changed to `public-read`.

For a walkthrough of upgrading from 4 to 5 and aws-sdk >= 2.0 you can watch
http://rubythursday.com/episodes/ruby-snack-27-upgrade-paperclip-and-aws-sdk-in-prep-for-rails-5
```

* add has_attached_file to Post model
```class Post < ActiveRecord::Base  
  has_attached_file :image, styles: { :medium => "640x" }
  validates_attachment_content_type :image, :content_type => /\Aimage\/.*\Z/
end
```

* rails migration generator
bin/rails g paperclip post image

* db migrate

* db migrate failed - add version number 4.2 to AddAttachmentImageToPosts
class AddAttachmentImageToPosts < ActiveRecord::Migration[4.2]


* New tries action: create. So add create to Post controller

* Create tries action: show. So add show to Post Controller

* add view logic to show.html.haml
= image_tag @post.image.url(:medium)
= @post.caption

* test passes

* Add new test to validate presence of image

* change model to validate this

* Add flash logic at application.html.haml
-flash.each do |name, msg|
  = content_tag :divves , msg, class: [:alert, alert_for(name)]

* add flash helper alert_for to application_helper

* the image tag in Post New view produces an error if a file is not chosen, even if made optional. I changed the message in the view.

* tests pass

* add FactoryBot - note example shows factoryGirl - I just c/Girl/Bot

* add factory bot config to rails_helper
config.include FactoryGirl::Syntax::Methods

* Add Post factory to spec/factories/post.rb

* New test for show page - fails

* Add database cleaner

* Get show page test to work
