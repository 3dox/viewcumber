require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "viewcumber"
    gem.summary = %Q{ Cucumber formatter for easily viewing each step of your scenarios }
    gem.homepage = "http://github.com/versapay/viewcumber"
    gem.authors = ["gregbell", "pcreux", "samuelreh"]
    gem.default_executable  = "viewcumber"
    gem.executables         = ["viewcumber"]
    gem.add_dependency "cucumber", ">= 1.1.4"
    gem.add_dependency "capybara", ">= 0.3"
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/test_*.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end

task :test => :check_dependencies

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "viewcumber #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

namespace :js do

  desc "Builds and flattens a release version of the Cappuccino viewer. Requires Cappuccino tools"
  task :build do
    `cd src && jake deploy`
    `rm -rf build`
    `flatten src/Build/Deployment/ViewCumber build`
  end
  
end
