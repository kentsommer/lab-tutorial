# List of Useful commands for working with CUDA / Multi-GPUs on lab machine
* $ export CUDA_VISIBLE_DEVICES="" 
  * this makes it so that CUDA cannot see ANY devices, to select a device to use simply enter its ID (0-2)
    * $ export CUDA_VISIBLE_DEVICES="0,1" 
      * This would use GPUs 0 and 1 (TITAN and first 1080)
          
* $ history
  * This command will show all previous commands with a number.
  * To run a previous command type !# (where # is number of command)
  * To re-run last previous command type
    * $ !!
  
  
* $ watch -n 0.5 nvidia-smi
  * This will show all GPUs in nvidia-smi (instead of just first one). Will also update every 0.5 seconds
  

