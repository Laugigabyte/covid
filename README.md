# Covid Classification Improvement

Considering the low recall of the original model in the original paper, we're looking forward to improving the model via changing the backbone or the optimizer.

Firstly, we changed optimizers.

Model |Optimizer |Average Precision |Average Recall |Average F1 |Average Accuracy | Average AUC
------|-----|--------------|---------------|----------|-----------------|----------------
|Dense169|Adam|0.8396|0.8476|0.8436|0.8374|0.8999
| |AdaBound|0.8525|0.4952|0.6265|0.6946|0.7741
| |Yogi|0.8300|0.7905|0.8098|0.8079|0.8838
| |AdaMod|0.8173|0.8095|0.8134|0.8079|0.8858
| |PID|0.7632|0.8286|0.7945|0.7783|0.8737
| |QHAdam|0.8710|0.7714|0.8182|0.8227|0.8906
| |QHM|0.7642|0.7714|0.7678|0.7586|0.8520
| |RAdam|0.8000|0.7238|0.7600|0.7635|0.8630
| |Ranger|0.8165|0.8476|0.8318|0.8227|0.8884
| |RangerQH|0.8462|0.8381|0.8421|0.8374|0.8986
| |SGDW|0.7475|0.7048|0.7255|0.7241|0.8362
| |AccSGD|0.7788|0.7714|0.7751|0.7685|0.8536
| |RangerVA|0.7769|0.8952|0.8319|0.8128|0.8845
| |DiffGrad|0.8056|0.8286|0.8169|0.8079|0.8951
| |NovoGrad|0.8043|0.7048|0.7513|0.7586|0.8740
| |Lamb|0.8571|0.7429|0.7959|0.8030|0.8779
