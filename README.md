# rails-chromedriver-docker-compose
setup docker-compose including Rails & postgresql & chromedriver 

## motivation

I want to be E2E test using Capybara with docker-compose  
For that need to install chromedriver. 

## environment

```shell script
ruby: 2.7.0
rails: 6.0.2.1
postgresql: 12.2
chromedriver: 80.0.3987.106
```

## getting started rails new

```shell script
$ docker-compose up --build

# rename current directory to Rails App name
$ cd ..
$ mv rails-chromedriver-docker-compose/ <APP_NAME> 

# Create Rails project in the current directory
$ docker-compose run app rails new . --database=postgresql
```

## When using RSpec

add config block to `rails_helper.rb`

```ruby
  config.before(:each, type: :system) do
    driven_by :selenium, using: :headless_chrome, screen_size: [1920, 1080],
                         options: { args: %w[headless disable-gpu no-sandbox disable-dev-shm-usage] }
  end
```
