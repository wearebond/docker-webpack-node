# Webpack Builds on Node v14

This image is intended to satisfy all of the prerequisites of our webpack build
processes designed to operate in a Node 14 environment. It is intended for use
in CI/CD pipelines and Github actions.

## Legacy Version Available

Note: the original Node 14 image shipped with NPM v6. This one has been updated
to use NPM v8 by default. If you need NPM v6 in your project, use:
`wearebond/webpack-node:14-legacy`

## Testing Changes Locally

> NOTE: M1 Macbook's require a special flag for building / running x86_64 images. Please use `--platform linux/x86_64` in build/run commands to ensure compatibility. On Intel-based Mac's this flag can be omitted. See: https://stackoverflow.com/a/69075554

To install new dependencies and test the image locally, you can follow these
steps:

1. Add new instructions to the `Dockerfile`
2. Build the image
```
docker build --platform linux/x86_64 --tag wearebond/webpack-node:14 ./14/
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
docker run --platform linux/x86_64 -it -v /path/to/sample-project:/www --entrypoint /bin/bash [[IMAGE_ID]]
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
docker push wearebond/webpack-node:14
```
