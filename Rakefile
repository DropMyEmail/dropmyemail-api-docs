require 'rubygems'
require 'bundler/setup'

# configuration variables
deploy_dir = '_site'

desc "deploy public directory to github pages"
task :deploy do
  puts "## Deploying branch to Github Pages "
  system "git checkout master"
  system "git branch -D gh-pages"
  system "git checkout --orphan gh-pages"

  # removes unneeded files
  ignore_dir = Regexp.new(deploy_dir)
  Dir["#{File.dirname(__FILE__)}/**/*"].select do |f|
    (f =~ ignore_dir).nil?
  end.each do |f|
    File.unlink(f) unless File.directory?(f)
  end
  system "ls -l"
  system "cp -r #{deploy_dir}/* ."
  system "rm -r #{deploy_dir}"
  system "git add ."
  system "git add -u"
  puts "\n## Commiting: Site updated at #{Time.now.utc}"
  message = "Site updated at #{Time.now.utc}"
  system "git commit -m \"#{message}\""
  puts "\n## Pushing generated #{deploy_dir} website"
  system "git push origin gh-pages --force"
  system "git checkout master"
  puts "\n## Github Pages deploy complete"
end
