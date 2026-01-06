# Cisco DMP 4400

![Cisco DMP 4400 image](img/4400.JPG)

## How configure a Cisco 4400 Digital Media Player to show remote multicast rtsp video flows.

### My 4400 Firmware Release Version is 5.2

### Factory reset

If you don't have the admin password you can factory reset the 4400

- connecting it to a dhcp enabled neteork
- powering up it
- waiting boot complete
- press the back reset button until the system reboot
- connect the 4400 to a hdmi video and read the dhcp asigned tcp/ip address
- connect to it in https with a flash player enabled browser ( see down )
- user: admin
- password: default

### Install an enabled flash player browser

- install Pale Moon 32 bit windows browser ( I used 33.9.1 )
- install windows flash player, installer is on resources folder.
- connect to https://your_4400_ip

### Play rtsp multicast file

- inslall ffmpeg
- Start the multicast file send in cmd

ffmpeg -re -i "yourfile.mkv" -localaddr 192.168.2.5 -f mpegts -vcodec libx264 -acodec aac "udp://239.1.2.3:4567?ttl=8"

- in the localaddr param replace 192.168.2.5 with your interface ip
- in your 4400 browser interface / Display Actions /Video multicast insert
  - Multicast Group IP Address: 239.1.2.3
  - port Number: 4567
- the hdmi attached tv should play video e audio
  
