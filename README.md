# mjpeg_streamer
mpjeg_streamer for rpi camera computer vision and octprint using the python3-picamera2 library

This is a small modification to the example mjpeg_streamer from the raspberry pi camera2 code: https://github.com/raspberrypi/picamera2/blob/main/examples/mjpeg_server_2.py

The modification is to also allow a single snapshot url which is useful for tasks such as creating timelapse videos.

I have also added a .service file which allows this to launch at startup.

This is aimed at being a simple helper script for the octoprint community.

To use:
1. Install the raspberry pi camera2 python libraries: sudo apt install python3-picamera2
2. Clone this repository.
3. Run via: python3 mjpeg_server_octoprint.py
4. Access the mjpg stream in your browser via: http://YOURIPADDRESS:8080/stream.mjpg or access a single snapshot via http://YOURIPADDRESS:8080/single

To run at startup: 
1. Edit the file webcamd.service and change the ExecStart=... line so that it points at the location you created the python file.
2. copy webcamd.service to /etc/systemd/system/
3. reload systemd: sudo systemctl daemon-reload
4. enable the service: sudo systemctl enable webcamd.service
5. start the service: sudo systemctl start webcamd.service.
