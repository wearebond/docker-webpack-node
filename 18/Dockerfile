FROM node:18-buster

RUN apt-get update

# https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html
RUN apt-get install groff -y && \
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install

# For now, we use rclone because it contains a better diff engine than AWS CLI
RUN mkdir -p /opt/rclone && \
    echo "75cec3bb99c009d2e4383962fc0e89b8  /opt/rclone/rclone-v1.64.0-linux-amd64.zip" > /opt/rclone/checksum && \
    wget https://github.com/rclone/rclone/releases/download/v1.64.0/rclone-v1.64.0-linux-amd64.zip -P /opt/rclone && \
    md5sum -c /opt/rclone/checksum && \
    unzip /opt/rclone/rclone-v1.64.0-linux-amd64.zip -d /opt/rclone/ && \
    ln -s /opt/rclone/rclone-v1.64.0-linux-amd64/rclone /usr/local/bin/rclone

# ImageMagick and GraphicsMagick are dependencies of our Webpack build process
RUN apt-get install imagemagick graphicsmagick ffmpeg git-lfs -y
