require "rubygems"
require "rake"
require "rake/clean"
require "rdoc/task"

task :default => ["build"]
CLEAN.include [ 'pkg', 'rdoc' ]
name = "rye"

$:.unshift File.join(File.dirname(__FILE__), 'lib')
require name
version = Rye::VERSION.to_s

begin
  require "jeweler"
  Jeweler::Tasks.new do |s|
    s.version = version
    s.name = name
    s.rubyforge_project = s.name
    s.summary = "Run SSH commands on a bunch of machines at the same time (from Ruby)."
    s.description = "Run SSH commands on a bunch of machines at the same time (from Ruby)."
    s.email = "delano@solutious.com"
    s.homepage = "https://github.com/delano/rye"
    s.authors = ["Delano Mandelbaum"]
    s.add_dependency 'annoy'
    s.add_dependency 'sysinfo',         '>= 0.7.3'
    s.add_dependency 'highline',        '>= 1.5.1'
    s.add_dependency 'net-ssh',         '>= 2.0.13'
    s.add_dependency 'net-scp',         '>= 1.0.2'
    s.add_dependency 'docile',          '>= 1.0.1'

    s.signing_key = File.join('/mnt/gem/', 'gem-private_key.pem')
    s.cert_chain  = ['gem-public_cert.pem']
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

RDoc::Task.new do |rdoc|
  rdoc.rdoc_dir = "rdoc"
  rdoc.title = "#{name} #{version}"
  rdoc.generator = 'hanna'
  rdoc.main = 'README.rdoc'
  rdoc.rdoc_files.include("README*")
  rdoc.rdoc_files.include("LICENSE.txt")
  rdoc.rdoc_files.include("VERSION")
  rdoc.rdoc_files.include("bin/*.rb")
  rdoc.rdoc_files.include("lib/**/*.rb")
end

