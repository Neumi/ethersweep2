# ethersweep
Ethernet + UDP + Json motor controller. Based on open source soft- and hardware.
Version2 has an built in AS5600 magnetic encoder for position feedback, the option for an END-stop for homing and an E-stop -just in case.
The controller uses 8.5V to 12V from an XT60 connector.


## What it does
Ethersweep is a simple to use ethernet connected stepper motor driver. It lets you use JSON formatted string to controll stpper motors via Ethernet. 

## How to get started:
Connect ethersweep to your network via ethernet and to a +12v power source.
Once connected it serarches for an IP address on the network using DHCP. When an IP is found, the controller shows it on the display and its ready to use.

Now you can use the Python script to control the motor.

![PCB raw B](/images/animation.gif)
![PCB raw B](/images/3d_board_back.png)
![PCB raw B](/images/3d_board_front.png)
![PCB raw B](/images/board.png)
![PCB raw B](/images/ethersweep2_1.jpg)
![PCB raw B](/images/ethersweep2_2.jpg)

## ALL YOU NEED TO DRIVE A STEPPER MOTOR WITH PYTHON:

```python
import socket
import json

UDP_SEND_IP_MOTOR = "192.168.1.185"  # ethersweep IP (depends on DHCP)
UDP_SEND_PORT = 1337


def drive_motor(steps, speed, direction, stepmode, motor_ip):
    json_data = json.dumps({'steps': steps, 'speed': speed, 'direction': direction, 'stepmode': stepmode})
    message = json_data.encode()
    sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    sock.sendto(message, (motor_ip, UDP_SEND_PORT))


drive_motor(100, 9500, 1, 32, UDP_SEND_IP_MOTOR)
```

## Video:
[![LINK TO VIDEO](https://img.youtube.com/vi/CZqzoTy67dk/0.jpg)](https://www.youtube.com/watch?v=CZqzoTy67dk)

