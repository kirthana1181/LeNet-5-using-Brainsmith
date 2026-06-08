## Key points and steps in order to run the automated flow in Brainsmith
1. We generate the input ONNX Model, by building the CNN using Brevitas functions, for every
layer of the ML Model.
2. Upon running the python script, the Quantized ONNX file gets generated which is used by
Brainsmith to construct the RTL.
3. Then with reference to the blueprint yaml file, which we have created in the external folder,
we run them using the command:

       smith dfc <cleaned_inp_onnx-file path> <blueprint.yaml> --output-dir <destination_results>

The command we used to run with respect to the ONNX file location and the desired location of the resulting files in our case is as shown:
(smith dfc onnx/lenet_clean.onnx lenet.yaml –output-dir ./results_run1)

4. This runs the automated flow of RTL generation till the final steps (which is the “measure_rtl_sim_performace”) which produces the stitched IP as the final output as per the target output mentioned in the blueprint file (here, 'lenet.yaml'). The target/output type could be either of these : 'generate_estimate_reports', 'rtl', or 'bitfile'.
