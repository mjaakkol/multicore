#
# Copyright (c) 2022 Nordic Semiconductor ASA
#
# SPDX-License-Identifier: LicenseRef-Nordic-5-Clause
#

cmake_minimum_required(VERSION 3.20.0)

 set(mcuboot_CONFIG_MCUBOOT_SIGNATURE_KEY_FILE \"${CMAKE_CURRENT_SOURCE_DIR}/priv.pem\")


find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
if (NOT SYSBUILD)
	message(WARNING
		" This is multi-image application that should be build using sysbuild.\n"
		" Add --sysbuild argument to west build command to prepare all the images.")
endif()

project(multicore)

target_sources(app PRIVATE src/main.c)
