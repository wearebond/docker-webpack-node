FROM node:10-buster

# ImageMagick and GraphicsMagick are dependencies of our Webpack build process
RUN apt-get update && apt-get install imagemagick graphicsmagick ffmpeg -y

# https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html
RUN apt-get install groff -y
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip
RUN ./aws/install
