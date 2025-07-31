Update Dockerfile.alpine.armv7 and patches.json with the version you want to build (should match the latest in the @yao-pkg/pkg release)
`docker build --build-arg HOST_ARCH=x86_64 --build-arg PKG_FETCH_OPTION_a=armv7 --build-arg PKG_FETCH_OPTION_n=node22 --build-arg PKG_FETCH_OPTION_p=alpine --platform linux/arm/v7 --file ./Dockerfile.alpine.armv7`
`docker image ls` - get the hash of the scratch image created (or from the logs of previous command)
`docker create --replace --name temp-container <image hash>`
`docker cp temp-container:/ dist/`
Copy binary files from dist folder to release assets in wave-dds/pkg-fetch