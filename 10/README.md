# Webpack Builds on Node v10

This image is intended to satisfy all of the prerequisites of our webpack build
processes designed to operate in a Node 10 environment. It is intended for use
in CI/CD pipelines and Github actions.

## Testing Changes Locally

To install new dependencies and test the image locally, you can follow these
steps:

1. Add new instructions to the `Dockerfile`
2. Build the image
```
docker build --tag wearebond/webpack-node:10 ./10/
```

3. Clone your sample project somewhere locally for testing
```
git clone git@github.com:wearebond/sample-project.git
```

4. Find the image ID
```
docker images
```

5. Run the image with your sample project mounted
```
docker run -it -v /path/to/sample-project:/www --entrypoint /bin/bash [[IMAGE_ID]]
```

6. Install and build your project inside the virtual machine
```
cd /www
npm ci
npm run build
```

7. Verify the build succeeds and produces the output you expect

## Update Docker Hub

Once you're satisfied with your new image, publish to hub.docker.com using:

```
docker push wearebond/webpack-node:10
```
