Multicore Hello World application
#################################

This is based on Nordic remote core example and modified to provide an boilerplate code
how set project up to build both cores at the same time in proper way with BT functionality.

Overview
########

The project is using MCUBoot on both images and sharing the same license key :file:`priv.pem`.

BT settings must be shared between the netcore- and multicore-images to ensure seamless co-operation between
the images.

* :file:`Kconfig.sysbuild` - This file is used to add Sysbuild configuration that is passed to all the images.
  ``SB_CONFIG`` is the prefix for sysbuild’s Kconfig options.
* :file:`sysbuild.cmake` - The CMake file adds additional images using the :c:macro:`ExternalZephyrProject_Add` macro.
  You can also add the dependencies for the images if required.

