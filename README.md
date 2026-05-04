# OFDM Live Video Streaming using GNU Radio and USRP

This project shows live webcam video transmission over an OFDM-based wireless link using GNU Radio and USRP.

## Overview

In this setup, webcam video is captured using FFmpeg, converted into MPEG-TS packets, and sent over UDP to the GNU Radio transmitter.  
The transmitter processes the stream using OFDM modulation and sends it through USRP hardware.  
At the receiver side, the signal is demodulated, decoded, and forwarded again over UDP for video playback.

## Files

- `tx_video_live.grc` - GNU Radio transmitter flowgraph
- `rx_video_live-2.grc` - GNU Radio receiver flowgraph

## Tools and Hardware

- GNU Radio
- USRP
- FFmpeg
- Linux
- Webcam

## FFmpeg command

```bash
ffmpeg -f v4l2 -framerate 10 -video_size 640x360 -i /dev/video0 -c:v mpeg1video -b:v 200k -f mpegts "udp://127.0.0.1:1235?pkt_size=188"
```

## Working principle

1. Capture live webcam video using FFmpeg.
2. Send the video stream over UDP to the GNU Radio TX flowgraph.
3. Modulate the stream using OFDM and transmit through USRP.
4. Receive the signal at the RX side using another USRP.
5. Demodulate and recover the video stream.
6. Forward the recovered stream over UDP for playback.

## Notes

- The FFmpeg UDP port must match the UDP input port used in the TX flowgraph.
- TX and RX sample rate, bandwidth, and carrier settings must be aligned.
- This project is useful for practical SDR-based wireless multimedia transmission experiments.

## Author

Md Arif
