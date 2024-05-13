# Multicore Hello World application with Bluetooth LE

This example was developed to address the gap in the existing samples that didn't provide clear
boilerplate code for making custom application and netcore images while supporting BT LE in nRF5340.

With this example, the developer should be able to set a working structure to get the development going.
There are multiple ways to accomplish the same task so the reader should not think this as the only way
to accomplish the task. Having said that the example is aiming to adopt the latest best practices but
as the best practices are a moving target, anybody with more up to date approach to enhance the codebase
should not be shy to suggest pull requests to improve the sample.

## Overview
This sample supports multi-image builds as well as flashing both cores 'as-is' from VS. The sample has been
tested with nRF Connect SDK 2.5.0.

Multi-image requires using sysbuild so when configuring the project. File *sysbuild.conf* is used for pushing
configuration parameters from the top image to the netcore. Most cases one should be able to perform core specific
configurations through prj.conf but eg. forcing the build system to include MCUBoot in netcore requires the parent
image configuration through the file.

## Bootloader
The project is using MCUBoot on both images. Both application and netcore
assets have child_image folder for configuring mcuboot. This example has nothing special around MCUBoot for being
multicore. Both MCUBoots share the keyfile *priv.pem* in the root.

## Bluetooth
The example have minimal BT configuration to enable connecting and also included Device Information Service (DIS) as basic
service to test.

Some BT settings must be shared between the netcore- and multicore-images to ensure seamless co-operation between
the images. This is more related to the lower-layer parameters. It is not clear what are all the parameters that should be
shared and thus the current implementation only includes an educated guess.

