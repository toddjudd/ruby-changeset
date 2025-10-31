# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require_relative "config/application"

Rails.application.load_tasks

namespace :version do
  desc "Set version number (format: x.y.z)"
  task :set, [ :semver ] do |_t, args|
    unless args[:semver] =~ /^\d+\.\d+\.\d+$/
      abort "Invalid version format. Please use semantic versioning (x.y.z)"
    end

    File.write('.version', args[:semver])
    puts "Version set to #{args[:semver]}"
  end
end
