source 'https://rubygems.org'

gem 'rake'
gem 'pact_broker'
if Gem.win_platform?
  gem 'sqlite3', force_ruby_platform: true
else
  gem 'sqlite3'
end
gem 'puma'
gem "padrino-core", ">= 0.16.0.pre3" # Required for the pact_broker UI.
gem "pact-support"
# required for ruby 3.4 (removed from std gems)
gem "mutex_m"
gem "csv"