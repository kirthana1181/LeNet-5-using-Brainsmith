Key points and steps in order to run the automated flow in Brainsmith
1. We generate the input ONNX Model, by building the CNN using Brevitas functions, for every
layer of the ML Model.
2. Upon running the python script, the Quantized ONNX file gets generated which is used by
Brainsmith to construct the RTL.
3. Then with reference to the blueprint yaml file, which we have created in the external folder,
we run them using the command:
“smith dfc &lt;final_inp_onnx-file path&gt; &lt;blueprint&gt;.yaml --output-dir &lt;destination_results&gt;”
(smith dfc onnx/lenet_clean.onnx lenet.yaml –output-dir ./results_run1)
4. This runs the automated flow of RTL generation till the final steps which is the
“measure_rtl_sim_performace”) i.e. stitched IP
