name: Build Kernel via build.sh

on:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout source
        uses: actions/checkout@v4

      - name: Install dependencies
        run: |
          sudo apt-get update -y
          sudo apt-get install -y \
            gcc-aarch64-linux-gnu \
            gcc-arm-linux-gnueabi \
            build-essential \
            bc bison flex libssl-dev \
            make git wget curl unzip \
            device-tree-compiler cpio \
            python3 xz-utils zip

      - name: Run build.sh
        run: |
          chmod +x build.sh
          ./build.sh

      - name: Upload outputs
        uses: actions/upload-artifact@v4
        with:
          name: KernelOutputs
          path: |
            arch/arm64/boot/Image.gz
            arch/arm64/boot/dtbo.img
            SPESND.zip
