# Steps

## Command to run the flow

With reference to the location of these files saved in our device, we are running the following command, which results in the creation of the input raw ONNX file, as well as the transformed ONNX Model, which is later called as per the file-path whcih is mentioned within these python scripts ('clean_path' which saves the transformed/cleaned ONNX Model & 'model_path' which saves the raw ONNX file geenrated before the FINN transforms are applied).
In here, our file path is:
    
    /home/kirthanar/brainsmith_projects/lenet/src

Therefore, the command we run in order to generate the raw and cleaned ONNX models,, followed by the Brainsmith build:

    python model_imp.py --blueprint lenet.yaml --output <results-folder-path>
