require './app.rb'
require 'resque/tasks'

task "resque:setup" do
  ENV['QUEUE'] = '*'
end

desc "Alias for resque:work (To run workers on Heroku)"
task "jobs:work" => "resque:work"

namespace :deploy do
  desc 'Deploy the app'
  task :production do
    app = "github-publisher"
    remote = "git@heroku.com:#{app}.git"

    system "heroku maintenance:on --app #{app}"
    system "git push #{remote} master"
    system "heroku maintenance:off --app #{app}"
  end
end
