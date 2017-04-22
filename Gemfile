source 'https://rubygems.org'
ruby '2.4.1'

def github_url(repo, options = {})
  userpass = ''
  unless options[:username].nil?
    userpass = options[:username]
    unless options[:password].nil?
      userpass = "#{userpass}:#{options[:password]}"
    end
    userpass = "#{userpass}@"
  end
  "https://#{userpass}github.com/#{repo}.git"
end

def apartmentlist_url(repo, options = {})
  if options[:public]
    url_opts = {}
  else
    encoded_password = URI.encode(ENV['ALGEMS_PASSWORD'])
    url_opts = { username: 'algems', password: encoded_password }
  end
  github_url("apartmentlist/#{repo}", url_opts)
end

gem 'haml'
gem 'pg'
gem 'puma'
gem 'rack-timeout'
gem 'rails'
# can be removed once https://github.com/sinatra/sinatra/issues/1055 has been
# included in the latest stable version
gem 'sinatra', '2.0.0.beta2'

# Gems used only for assets and not required
# in production environments by default.
group :assets do
  gem 'bootstrap-sass'
  gem 'sass-rails'
  gem 'uglifier'
end

# Gems used only for production
group :production do
  # Heroku recommends this gem to make deployments easier. It does two things:
  # makes Rails serve static assets, and outputs logs through stdout
  gem 'rails_12factor'
end

group :development do
  gem 'foreman'
end

group :development, :test do
  gem 'better_errors'
  gem 'binding_of_caller'
  gem 'factory_girl_rails'
  gem 'faker'
  gem 'pry-byebug'
  gem 'pry-rails'
  gem 'rspec-rails'
  gem 'shoulda-matchers'
  gem 'simplecov', require: false
  gem 'timecop'
end

group :test do
  gem 'rails-controller-testing'
  gem 'webmock'
end
