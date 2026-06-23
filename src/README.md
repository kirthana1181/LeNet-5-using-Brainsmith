# Steps to run the flow

### 1. Enter into the project directory

A similar message as to the one shown below shall be displayed which ensures that the project directory which was initialized in brainsmith has been activated and is being accessed.

    (brainsmith-py3.11) kirthanar@KirthanaR:~/brainsmith$ cd ../brainsmith_projects/lenet/
    direnv: loading ~/brainsmith_projects/lenet/.envrc
    direnv: loading ~/brainsmith_projects/lenet/.brainsmith/.brainsmith/env.sh
    direnv: export +BSMITH_BUILD_DIR +BSMITH_DEPS_DIR +BSMITH_DIR +BSMITH_PROJECT_DIR +FINN_BUILD_DIR +FINN_DEPS_DIR +HLS_PATH +LD_LIBRARY_PATH +LD_PRELOAD +NETRON_PORT +NUM_DEFAULT_WORKERS +OHMYXILINX +PLATFORM_REPO_PATHS +VITIS_PATH +VIVADO_IP_CACHE +VIVADO_PATH +XILINX_LOCAL_USER_DATA ~PATH

Note: upon creating a new project directiry, in-order to activate the environment within the new directory, run _'direnv allow'_ which ensures that all the brainsmith commands being run within the directory are linked to our Brainsmith compiler and the command line identifies them as the commands linked to the compiler software's operations.

### 2. Running desired commands

With reference to the location of these files saved in our device, we are running the following command, which results in the creation of the input raw ONNX file, as well as the transformed ONNX Model, which is later called through its file-path, defined in the python build scripts ('clean_path' which saves the transformed/cleaned ONNX Model & 'model_path' which saves the raw ONNX file generated before the FINN transforms are applied).
In here, our file path is:
    
    /home/kirthanar/brainsmith_projects/lenet/src

Therefore, the command we run in order to generate the raw and cleaned ONNX models,, followed by the Brainsmith build:

    python model_imp.py --blueprint lenet.yaml --output <output-directory-path>

Usually the onnx file can be generated seperately and be saved in a desired file location, which can be defined within the python script we have written to build or import the model, quantize it (using brevitas and qonnx libraries), and produce the quantized ONNX/QONNX models.
These ONNX files of the model are then seperately sourced from the file paths to execute the compiler's build flow using the smith command:

    smith dfc <cleaned_onnx> <blueprint file> --output-dir <output-files-directory-path>

This command is defined within the model build script through the brainsmith libraries, using brainsmith explore_design_space function.

### 3. Accessing the resulting output files

When the compiler is executing the build flow, the targetted output directory is displayed as shown:

<img width="1407" height="778" alt="Screenshot from 2026-06-23 11-04-57" src="https://github.com/user-attachments/assets/bb460bb5-c3b3-453e-9d02-757c7e1c2ec4" />

Within this folder, all the intended output files, for every build step in the workflow are being saved here.

<img width="1447" height="586" alt="Screenshot from 2026-06-23 11-31-22" src="https://github.com/user-attachments/assets/962b523d-da8a-4b45-b359-616d57854d5f" />

In the image shown here, the output directory is '_results_run12_', which further consists of the log file which records the build flow ('_brainsmith.log_'), the onnx files (since, they've been mentioned to be saved in this file path within the model build script) and root folder stores all the intermediate build steps file within a folder nested in it, called '_intermediate_models_'. Under the root folder, the input and output onnx files are also stored by the file name: '_input.onnx_' and '_output.onnx_'. The estimate reports are stored within '_reports_' and the final stitched IP is stored within the folder named '_stitched_ip_'. 

<img width="1680" height="242" alt="Screenshot from 2026-06-23 11-50-59" src="https://github.com/user-attachments/assets/f54970e1-031f-47a4-a0c9-f0944015b5d7" />



# Key points before implementing

1. We generate the input ONNX Model, by building the intended model using Brevitas functions, for every layer of the Model.
2. Upon running the python script for model build or model import, the Quantized ONNX file gets generated which is used as the input ONNX file to Brainsmith to produce the RTL.
3. The blueprint file is used to run the compiler to build our model's stitched IP(our targetted output, as stated within the blueprint file).
4. This runs the automated flow of RTL generation till the final steps (which is the “measure_rtl_sim_performace”) which produces the stitched IP as the final output as per the target output mentioned in the blueprint file (here, 'lenet.yaml'). The target/output type could be either of these : 'generate_estimate_reports', 'rtl', or 'bitfile'. 



