require "bundler/gem_tasks"
require 'rake/testtask'

$LOAD_PATH.unshift File.expand_path("../lib", __FILE__)
require "measured/version"

task default: :test

desc 'Run the test stuite'
Rake::TestTask.new do |t|
  files = ARGV[1..-1]
  files = "test/**/*_test.rb" if !files || files.length == 0

  t.libs << "test"
  t.libs << "lib/**/*"
  t.test_files = FileList[files]
  t.verbose = true
end

task tag: :build do
  system "git commit -m'Released version #{ Measured::VERSION }' --allow-empty"
  system "git tag -a v#{ Measured::VERSION } -m 'Tagging #{ Measured::VERSION }'"
  system "git push --tags"
end
