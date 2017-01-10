# Info and priliminary setup 

Current GPUs on linux (0 = TITAN X, 1 = GTX 1080, 2 = GTX 1080)

Current GPUs on Windows (2 GTX 1080s: IDs are N/A, 1 GTX 1070: ID is N/A, 1 GTX 970: ID is N/A)

**Before being able to use any deep learning libraries** you will need to make sure that your CUDA environment variables are set. To do this simply add (verify they exist) the following lines to your ~/.bashrc file
* export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
* CUDA_ROOT=/usr/local/cuda

# List of helpful commands

* $ export CUDA_DEVICE_ORDER="PCI_BUS_ID"
  * this will make it so that CUDA and nvidia-smi device ID's match so when you set CUDA_VISIBLE_DEVICES the ID you choose is the same ID that nvidia-smi is showing. 

* $ export CUDA_VISIBLE_DEVICES="" 
  * this makes it so that CUDA **CANNOT** see **ANY** devices, to select a device to use simply enter its ID (0-2)
    * $ export CUDA_VISIBLE_DEVICES="0,1" 
      * This would use GPUs 0 and 1 (TITAN and first 1080)

**If using Python you can also set visible devices in code:**
* os.environ['CUDA_VISIBLE_DEVICES'] = '0'
  * this is esspeically handy since you can have your device set per script rather than having to change globally everytime.

      
* $ unset CUDA_VISIBLE_DEVICES
  * This will allow CUDA to see **ALL** GPUs
  * This command is the same as:
    * export CUDA_VISIBLE_DEVICES ="0,1,2"
  
  
* $ watch -n 0.5 nvidia-smi
  * This will show all GPUs in nvidia-smi (instead of just first one). Will also update every 0.5 seconds
  
* $ nvidia-smi -L 
  * This will list all GPUs visible by the system (useful for debugging added GPUs - is **NOT EFFECTED BY CUDA_VISIBLE_DEVICES**)
  
* $ history
 * This command will show all previous commands with a number.
 * To run a previous command type !# (where # is number of command)
 * To re-run last previous command type
   * $ !!
   
```import tensorflow as tf
from keras.backend.tensorflow_backend import set_session
config = tf.ConfigProto()
config.gpu_options.per_process_gpu_memory_fraction = 0.4
set_session(tf.Session(config=config))```


# Use Sublime Text remotely <3

On local machine (your computer perform the following):
* In Sublime Text, open Package Manager (Ctrl-Shift-P on Linux/Win, Cmd-Shift-P on Mac, Install Package), and install rsub
* Append the following string to your ssh connection (nothing in this string changes):
  * -R 52698:localhost:52698
  * Full connection string should look like:
    * ssh -p port-num username@server-ip -R 52698:localhost:52698
* TIP (to make ssh connecting on linux a breeze add an alias command for the above connection string)
  * $ echo "alias sshlab='full-connection-string'" > ~/.bash_aliases && source ~/.bashrc
    * then all you have to do is type sshlab and you will connect to the lab server
    
    
On remote machine (lab server run the following):
* $ echo "alias subl='rsub'" > ~/.bash_aliases && source ~/.bashrc

Now as long as you already have Sublime Text open locally simply type `subl filename` and it will allow you to edit!
  
 
  

