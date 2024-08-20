server setup documentation
-
apt upate / upgrade
apt install xfce
apt install xfce xfce4-goodies tightvncserver

vncserver
vncserver -kill :1
nano ~/.vnc/xtartup
startxfce4
vncserver

nano /etc/systemd/system/vncserver.service

[Unit]
  Description=TightVNC server
  After=syslog.target network.target
  [Service]
  Type=forking
  User=root
  PAMName=login
  PIDFile=/root/.vnc/%H:1.pid
  ExecStartPre=-/usr/bin/vncserver -kill :1 > /dev/null 2>&1
  ExeStart=/usr/bin/vncserver
  Exestop=/usr/bin/vncserver -kill :1
  [Install]
  WantedBy=Multi-user.target

  systemctl daemon-reload
  systemctl enable --now vncserver

port 5901 - default



