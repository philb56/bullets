See https://github.com/rspec/rspec-rails

```
# Add to Gemfile:
group :development, :test do
  gem 'rspec-rails', '~> 3.7'
end

#install by running:
bundle install

#Initialize the spec/ directory:
rails generate rspec:install

#run test
rspec
```
