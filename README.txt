# (c) Copyright 2020 Xilinx, Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.


                      XILINX U30 H.264 and HEVC Transcoder Solution
			 U30_Transcoder_Release_v0.9 - 12/2/2020

#############################################################################################
################################     TABLE OF CONTENTS    ###################################
#############################################################################################

* COMPONENTS

* OVERVIEW

* INSTALLATION INSTRUCTIONS

* INSTRUCTIONS TO RUN A SINGLE FFMPEG PROCESS

* INSTRUCTIONS TO RUN MULTIPLE FFMPEG PROCESSES

#############################################################################################
###################################     COMPONENTS     ######################################
#############################################################################################
The release directory includes the following:
============================================================================================
FILE/FOLDER                        | SUMMARY
============================================================================================
flash_image                        | This folder contains the file used to flash the U30
                                   | boards with
--------------------------------------------------------------------------------------------
xsa                                | This folder contains the driver file used by XRT to
                                   | interface with the board
--------------------------------------------------------------------------------------------
install.sh                         | Installation script
--------------------------------------------------------------------------------------------
*.deb                              | Installation packages
--------------------------------------------------------------------------------------------
ReleaseNotes.txt                   | Release notes for U30 transcoder solution
--------------------------------------------------------------------------------------------
README.txt                         | This file
--------------------------------------------------------------------------------------------


#############################################################################################
######################################  OVERVIEW  ###########################################
#############################################################################################
This release package enables loading and execution of the Xilinx H.264 and HEVC transcoder 
solution U30 FPGA.


#############################################################################################
##############################  INSTALLATION INSTRUCTIONS  ##################################
#############################################################################################
1. Install the packages
   source install.sh
2. Cold boot the computer
3. Run "sudo su"ù and provide the administrative password
4. Setup the environment
   source /opt/xilinx/xrt/setup.sh
5. Get the list of devices
   xbutil list
   It will print out a lot of information, at the bottom will be something like this:

   [0] 0000:e0:00.0 xilinx_U30_xdma_1_1(ID=0x5ea44206) user(inst=143)
   [1] 0000:df:00.0 xilinx_U30_xdma_1_1(ID=0x5ea44206) user(inst=142)

   There may be more depending on the number of cards installed. Each line is one device,
   there are two devices per card so there should be an even number of devices.
6. Search for the device ID. In the first device listed in this example it is e0:00.0
7. Run the following command with the device ID. (note that the end of the device ID needs
   to be ".1"ù instead of the ".0"ù shown in "xbutil list"ù)
   xbutil flash -m flash_image/BOOT*.bin -d e0:00.1
8. Repeat steps 6 and 7 for each device
9. Cold boot the computer


#############################################################################################
#####################  INSTRUCTIONS TO RUN A SINGLE FFMPEG PROCESS  #########################
#############################################################################################
1. Source XCDR by running "source /opt/xilinx/xcdr/setup.sh"ù
2. Run the ffmpeg command line 


#############################################################################################
####################  INSTRUCTIONS TO RUN MULTIPLE FFMPEG PROCESSES  ########################
#############################################################################################
1. Source XCDR by running "source /opt/xilinx/xcdr/setup.sh"ù
2. Run the launcher command line "/opt/xilinx/launcher/bin/launcher <a text file containing
   a list of source files> <a transcode parameter file, samples can be found in
   /opt/xilinx/launcher/scripts/run_params/>"
 
