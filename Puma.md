# Puma with Capistrano and systemd
```service
   [Unit]
   Description=Puma HTTP Server for Rails
   After=network.target
  
   [Service]
   Type=simple
   WorkingDirectory=/var/www/html/project-name/current
   ExecStart="/home/dev/.config/systemd/scripts/puma-start.sh"
   Restart=always
  
  [Install]
  WantedBy=default.target
```
```bash
   #!/bin/bash -
  
   /home/dev/.rbenv/shims/bundle exec puma -C /var/www/html/project-name/current/config/puma.rb

```
```ruby
# config/deploy.rb
lock "~> 3.19.2"

set :application, "my-test"
set :repo_url, ENV['REPO_MY_TEST']

set conditionally_migrate, true

set :deploy_to, "/var/www/html/#{fetch(:application)}"
append :linked_files, "config/database.yml", 'config/master.key'
append :linked_dirs, "log", "tmp/pids", "tmp/cache", "tmp/sockets", "public/system", "storage"

set :keep_releases, 5

set :rbenv_type, :user
set :rbenv_custom_path, '/home/dev/.rbenv/'
set :rbenv_ruby, "3.4.2"

namespace :deploy do
  desc 'restart puma'
  task :restart_puma do
    on roles(:app) do
      execute :systemctl, '--user restart puma'
      # might not need
      execute "XDG_RUNTIME_DIR=/run/user/$(id -u) systemctl --user restart puma"
    end
  end
  after 'deploy:publishing', 'deploy:restart_puma'
end

# Uncomment the following to require manually verifying the host key before first deploy.
# set :ssh_options, verify_host_key: :secure

```
