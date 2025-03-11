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
