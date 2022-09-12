# Openlane Automated Installation
This script builds openlane and all its dependencies on an Ubuntu (only) System.

# Contents
- [Steps to build Openlane](#steps-to-build-openlane)
- [Steps to run Openlane](#steps-to-run-openlane)
- [Acknowledgments](#acknowledgments)
 
# STEPS TO BUILD OPENLANE

1. `git clone https://github.com/Realmachas/OpenLane_Automated_Installation.git`
2. `sudo -i` #switch to root user (or have root user password ready).
3. Change directory to where openlane_build_script folder was cloned. `cd /path/to/openlane_build_script`
4. Execute the script as below:

        - `chmod 775 Openlane_script.sh`
        - `./openlane_script.sh`

5. This script would create following directory structure:

 ```bash  
 Desktop/
 ...
  └── work
    └── tools 
        └── openlane_working_dir
         |__ Openlane
                       
```              
 
# STEPS TO RUN OPENLANE

1. Go to /path/to/openlane (i.e., ~/work/tools/openlane_working_dir/Openlane)
2. There are two ways of invoking openlane. The easiest of the two would be:
   - `make mount`

   The second way would be to explicitly specify the path to PDK_ROOT and OPENLANE_IMAGE_NAME and invoking docker with these inputs
   - `export PDK_ROOT=<absolute path to where skywater-pdk and open_pdks reside>`
   - `export OPENLANE_IMAGE_NAME=<docker image name>`
   - `docker run -it -v $(pwd):/openlane -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) $OPENLANE_IMAGE_NAME`
   
3. **Note:** If you face "permission denied" during docker invocation in setup or in above step, do refer below link to resolve:
   - [Fix Docker Permission Denied Issue](https://stackoverflow.com/questions/48957195/how-to-fix-docker-got-permission-denied-issue)

4. `./flow.tcl -design spm`
(the above flow.tcl command will run RTL2GDS flow for design named "spm". Same can be done for other designs which are present in ~/work/tools/openlane_working_dir/Openlane/designs)

5. Refer to: https://github.com/efabless/openlane for detailed instructions.

# ACKNOWLEDGMENTS

[efabless OpenLane team](https://github.com/efabless/openlane)
