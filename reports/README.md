## Reports Generated

| Reports generated                    | Purpose                                                                                                                                                                                                         |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `estimate_layer_cycles`              | Represents the number of cycles taken by each of the output ONNX nodes.                                                                                                                                         |
| `estimate_layer_resources`           | Represents the amount of hardware resources required specific to the output ONNX nodes, with the target hardware resource.                                                                                      |
| `estimate_layer_config_alternatives` | Represents the resource-estimation alternatives for each hardware node belonging to the output ONNX graph, i.e., possible implementations of each layer.                                                        |
| `estimate_network_performance`       | Summarizes the estimated end-to-end performance, highlighting key performance parameters.                                                                                                                       |
| `op_and_param_counts`                | Summarizes the number of MAC operations for every hardware node in the output graph, and the number of weight parameters specific to each node.                                                                 |
| `rtlsim_performance`                 | Generated as a result of the step `measure_rtl_sim_performance`, summarizing the key performance parameters such as total number of clock cycles, throughput, stable throughput, frequency, total runtime, etc. |

## RTL Simulation Performance Parameters

| Parameters                                         | Significance                                                                                                 |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| `"N_IN_TXNS": 8192`                                | Number of input AXI-stream transactions accepted by the accelerator.                                         |
| `"N_OUT_TXNS": 8192`                               | Number of output AXI-stream transactions produced by the accelerator.                                        |
| `"cycles": 4194331`                                | Total number of simulated clock cycles from after reset/start of the test until the RTL simulation finished. |
| `"N": 1`                                           | RTL simulation batch size.                                                                                   |
| `"latency_cycles": 4194330`                        | Latency for the first complete inference output, measured in clock cycles.                                   |
| `"interval_cycles": 4186138`                       | Computation/drain interval after the input stream has been accepted.                                         |
| `"TIMEOUT": 0`                                     | Indicates whether a timeout occurred because generation took longer than expected.                           |
| `"UNFINISHED_INS": 0`                              | Indicates whether there are any missing input transactions.                                                  |
| `"UNFINISHED_OUTS": 0`                             | Indicates whether there are any missing output transactions.                                                 |
| `"RUNTIME_S": 284`                                 | Total on-machine time to generate/run the RTL simulation, measured in seconds.                               |
| `"runtime[ms]": 20.971655000000002`                | Simulated runtime for the batch, derived using cycle count and the assumed clock frequency.                  |
| `"throughput[images/s]": 47.68340886782659`        | Throughput per batch, measured in images per second.                                                         |
| `"fclk[mhz]": 200.0`                               | Assumed accelerator clock frequency, which can be customized.                                                |
| `"stable_throughput[images/s]": 47.68340886782659` | Throughput when streaming is underway. When `N = 1`, this is the same as `throughput`.                       |
