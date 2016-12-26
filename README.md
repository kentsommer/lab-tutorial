# List of Useful commands for working with CUDA / Multi-GPUs on lab machine

Current GPUs on linux (0 = TITAN X, 1 = GTX 1080, 2 = GTX 1080)

Current GPUs on Windows (2 GTX 1080s: IDs are N/A, 1 GTX 1070: ID is N/A, 1 GTX 970: ID is N/A)

* $ export CUDA_VISIBLE_DEVICES="" 
  * this makes it so that CUDA **CANNOT** see **ANY** devices, to select a device to use simply enter its ID (0-2)
    * $ export CUDA_VISIBLE_DEVICES="0,1" 
      * This would use GPUs 0 and 1 (TITAN and first 1080)
      
* $ unset CUDA_VISIBLE_DEVICES
  * This will allow CUDA to see **ALL** GPUs
  * This command is the same as:
    * export CUDA_VISIBLE_DEVICES ="0,1,2"
  
  
* $ watch -n 0.5 nvidia-smi
  * This will show all GPUs in nvidia-smi (instead of just first one). Will also update every 0.5 seconds
  
* $ nvidia-smi -L 
  * This will list all GPUs visible by Nvidia (useful for debugging added GPUs - is **NOT EFFECTED BY CUDA_VISIBLE_DEVICES**)
  
  
  
* $ history
 * This command will show all previous commands with a number.
 * To run a previous command type !# (where # is number of command)
 * To re-run last previous command type
   * $ !!
  
 
  

