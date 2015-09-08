# encoding: utf-8

require 'rubygems'
require 'bundler'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts 'Run `bundle install` to install missing gems'
  exit e.status_code
end
require 'rake'

require 'jeweler'
Jeweler::Tasks.new do |gem|
  gem.name = 'ruby-coding-standards'
  gem.homepage = 'http://github.com/theappbusiness/ruby-coding-standards'
  gem.license = 'MIT'
  gem.summary = 'Gem to check and apply TAB code policies'
  gem.description = 'Run check_code to check code against policies'
  gem.email = 'felix@whimsicaldoodles.com'
  gem.authors = ['Felix Hawkins', 'Peter Hinterseer']
  gem.extra_rdoc_files = ['LICENSE.txt', 'README.md', 'GEM.md', 'DESCRIPTION.md']
  # dependencies defined in Gemfile
end
Jeweler::RubygemsDotOrgTasks.new
