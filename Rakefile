# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require_relative "config/application"

Rails.application.load_tasks

namespace :release do
  desc "Set version number (format: x.y.z)"
  task :version, [ :semver ] do |_t, args|
    unless args[:semver] =~ /^\d+\.\d+\.\d+$/
      abort "Invalid version format. Please use semantic versioning (x.y.z)"
    end

    File.write('.version', args[:semver])
    puts "Version set to #{args[:semver]}"
  end

  task :publish do
    sh "git checkout main"
    sh "git pull"
    sh "git tag v#{File.read('.version').strip}"
    sh "git push --tags"
  end

  task :changeset do
    sh "pnpm changeset"
  end
end
