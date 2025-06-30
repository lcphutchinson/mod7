# Module 7 - Dockerizing the QR Code Generation App

A module of is601 Web Systems Development, by Keith Williams

This module serves as an introduction to containerization using Docker, and makes use of a simple QR Generation script to demonstrate remote execution with and without volume mounting. 

## Reflection Component

I had an elementary grasp of Docker prior to this module, having completed one online course on this same subject matter prior to the start of term. As such, Docker Desktop was already installed on my system and configured for use with my WSL. That being said, I have confronted a configuration error in my attempts to deploy and run the docker image that I have not yet remedied, and instead have only temporarily solved:

When mounting a volume to the local directory './qr_codes', remote execution of main.py encounters a permissions error: 

```bash
docker run -v ./qr_codes:/app/qr_codes lcphutchinson/is601_qr_codegen
2025-06-30 19:51:31,486 - ERROR - An error occurred while generating or saving the QR code: [Errno 13] Permission denied: '/app/qr_codes/QRCode_20250630195131.png'
```

This error occurs only while mounting with the `-v` option, and has not been remedied by any adjustments I have made to the permissions commands executed in the Dockerfile. Thusfar, my only successful remedy is to execute a `sudo chmod a=rwx` on the qr_codes directory prior to execution. Any insight into what might be causing this behavior would be greatly appreciated, as my preliminary research has yeilded no answers.

## Screenshots

### Successful Manual Build and Run

![Screenshot 2025-06-30 150934](https://github.com/user-attachments/assets/fcd5faa4-3300-4108-853e-2e632d613cf0)

### Successful Docker Compose Run

![Screenshot 2025-06-30 150709](https://github.com/user-attachments/assets/8fe64845-89ed-4a03-a543-de649a628aeb)

### Successful Github Actions Run

![Screenshot 2025-06-30 152619](https://github.com/user-attachments/assets/184dfc45-f73b-47f7-a688-26b507c17fa5)

## Generated QR Codes

### My Github Repository

![Github Repo](/qr_codes/QRCode_20250630185337.png "My QR Code Link")

### My DockerHub Image

![Docker QR Image](/qr_codes/QRCode_20250630185357.png "My QR Code Link")

