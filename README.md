# Poppler for ARM64 build on AWS Lambda

This repo provides a solution for building Poppler, the PDF rendering library, on AWS Lambda with an ARM64 architecture. The steps below explain how to build the latest compatible version of Poppler (22.12.0) using CMake 3.16. Alternatively, you can directly download the pre-built package.zip and use it as a layer in your Lambda function.

## Usage

Follow these steps to build Poppler for your specific version needs:

1. Set up an EC2 instance with ARM64 architecture.
2. Install Docker and clone this repository.
3. In the cloned repo, modify the `POPPLER_VERSION` variable in the `Dockerfile` to your desired version.
4. Run the following commands in the terminal:

```
docker build -t poppler .
docker run --name poppler -d -t poppler cat
docker cp poppler:/root/package.zip .
```

5. Download the generated `package.zip` file, which can be used as a layer for Poppler in your Lambda function.

**Note:** For building Poppler with an x64 architecture, you can follow the same procedure.

## Credits

This repository is based on [this Stack Overflow post](https://stackoverflow.com/a/69658575).