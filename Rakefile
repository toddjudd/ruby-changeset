# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require_relative "config/application"

Rails.application.load_tasks

namespace :release do
  desc "Set version number (format: x.y.z)"
  task :version do
    # run changeset to bump version in package.json and create changelog
    sh "pnpm changeset version"
    # read the new version from package.json
    version = JSON.parse(File.read('package.json'))['version']

    File.write('.version', version)
    puts "Version set to #{version}"
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
