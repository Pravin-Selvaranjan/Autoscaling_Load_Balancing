# Creating a service to automate running a service in Linux

- `cd /etc/systemd/system`
- Create a file named [servicename.service] and add the following
 ```
[Unit]
Description=<description_about_your_service>

[Service]
User=<user_such_as_root>
WorkingDirectory=<directory_of__your_script such as /home/unixcop>
ExecStart=<script_which_needs_to_be_executed>
Restart=always

[Install]
WantedBy=multi-user.target
```

- `sudo systemctl daemon-reload`
- `sudo systemctl start [your_new_service].service`
- `sudo systemctl status unixcop.service`
- To enable on every reboot
- `sudo systemctl enable unixcop.service`