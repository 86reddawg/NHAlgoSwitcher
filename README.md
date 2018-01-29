This script creates an algo switcher for Nvidia cards used with Nicehash.  It is intended for headless linux machines.
All programs run in screen, so you can remote in and check on the status of everything.
Each GPU has it's own benchmarks, overclock settings, and miner programs for the most flexibility, which I'm, assuming increases profitability

Currently, I'm calling the program through a script every 2 minutes through cron with:
*/2 * * * * /path/to/miner/script

The bash script file calls the tuffminer python program and dumps the output to a log file.  Example script file:
/path/to/tuffmine >> /path/to/logfile


This program relies on having an instance of nvidia-settings running all the time in a fake xorg window, with one instance per GPU.
See the example xorg config file and duplicate it for each GPU (just change the pci bus location).  It must reside in /etc/X11/
See the example gpuboot script for initially setting up the environments, which I call from cron with the @reboot option

Don't forget to use nvidia-smi to set persistence