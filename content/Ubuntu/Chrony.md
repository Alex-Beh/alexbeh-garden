### Overview

1. start & stop chrony service

2. check status

   ```
   sudo systemctl status chronyd.service
   # show last 20 lines
   journalctl -n 20 -u chrony
   ```

3. Run chrony manually with custom command [mostly for sync]

   ```
   sudo chronyd -d 'server 10.252.252.100 iburst'
   ```

### chronyc tracking

Expected output:

```
administrator@A31-003324021:~$ chronyc tracking
Reference ID    : 0AFCFC64 (10.252.252.100)
Stratum         : 5
Ref time (UTC)  : Tue Sep 12 12:21:26 2023
System time     : 0.000000102 seconds slow of NTP time
Last offset     : +0.000109387 seconds
RMS offset      : 0.000109387 seconds
Frequency       : 78.816 ppm fast
Residual freq   : +0.002 ppm
Skew            : 1.982 ppm
Root delay      : 0.086848132 seconds
Root dispersion : 0.025397623 seconds
Update interval : 64.3 seconds
Leap status     : Normal
```

### chronyc sources -v

查看ntp_servers

```
MS Name/IP address         Stratum Poll Reach LastRx Last sample               
===============================================================================
^* 10.252.252.100                4   6    77    39   -231us[ -388us] +/-   66ms
```

### Sample Configuration

#### **Server**

```
pool ntp.ubuntu.com        iburst maxsources 4
pool 0.ubuntu.pool.ntp.org iburst maxsources 1
pool 1.ubuntu.pool.ntp.org iburst maxsources 1
pool 2.ubuntu.pool.ntp.org iburst maxsources 2

# This directive specify the location of the file containing ID/key pairs for
# NTP authentication.
keyfile /etc/chrony/chrony.keys

# This directive specify the file into which chronyd will store the rate
# information.
driftfile /var/lib/chrony/chrony.drift

# Uncomment the following line to turn logging on.
#log tracking measurements statistics

# Log files location.
logdir /var/log/chrony

# Stop bad estimates upsetting machine clock.
maxupdateskew 100.0

# This directive enables kernel synchronisation (every 11 minutes) of the
# real-time clock. Note that it can’t be used along with the 'rtcfile' directive.
rtcsync

# Step the system clock instead of slewing it if the adjustment is larger than
# one second, but only in the first three clock updates.
makestep 1 3

# Configure this host to act as the NTP source for the rest of the devices in this robot
local stratum 10
allow 192.168.131/24
```

#### **Client**

```
pool ntp.ubuntu.com        iburst maxsources 4
pool 0.ubuntu.pool.ntp.org iburst maxsources 1
pool 1.ubuntu.pool.ntp.org iburst maxsources 1
pool 2.ubuntu.pool.ntp.org iburst maxsources 2

# Add the robot's primary PC as an NTP source
#server 10.252.252.100 offline minpoll 8
server 10.252.252.100 iburst

# This directive specify the location of the file containing ID/key pairs for
# NTP authentication.
keyfile /etc/chrony/chrony.keys

# This directive specify the file into which chronyd will store the rate
# information.
driftfile /var/lib/chrony/chrony.drift

# Uncomment the following line to turn logging on.
#log tracking measurements statistics

# Log files location.
logdir /var/log/chrony

# Stop bad estimates upsetting machine clock.
maxupdateskew 100.0

# This directive enables kernel synchronisation (every 11 minutes) of the
# real-time clock. Note that it can’t be used along with the 'rtcfile' directive.
rtcsync

# Step the system clock instead of slewing it if the adjustment is larger than
# one second, but only in the first three clock updates.
makestep 1 3
```

Reference: [Configuring NTP](https://docs.clearpathrobotics.com/docs/ros/networking/ntp/)