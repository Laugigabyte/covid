# Covid Classification Improvement

Considering the low recall of the original model in the original paper, we're looking forward to improving the model via changing the backbone or the optimizer.

Hyperparameters are as follows:


Training Epoch |Test Epoch |Learning Rate |Batch size 
------|-----|--------------|----------
200|10|0.0001|10

Firstly, we chose pretrained Dense169 as our backbone and changed optimizer.

|Optimizer |Average Precision |Average Recall |Average F1 |Average Accuracy | Average AUC
-----|--------------|---------------|----------|-----------------|----------------
|Adam|0.8396|0.8476|0.8436|0.8374|0.8999
|AdaBound|0.8525|0.4952|0.6265|0.6946|0.7741
 |Yogi|0.8300|0.7905|0.8098|0.8079|0.8838
 |AdaMod|0.8173|0.8095|0.8134|0.8079|0.8858
 |PID|0.7632|0.8286|0.7945|0.7783|0.8737
 |QHAdam|0.8710|0.7714|0.8182|0.8227|0.8906
 |QHM|0.7642|0.7714|0.7678|0.7586|0.8520
 |RAdam|0.8000|0.7238|0.7600|0.7635|0.8630
 |Ranger|0.8165|0.8476|0.8318|0.8227|0.8884
 |RangerQH|0.8462|0.8381|0.8421|0.8374|0.8986
 |SGDW|0.7475|0.7048|0.7255|0.7241|0.8362
 |AccSGD|0.7788|0.7714|0.7751|0.7685|0.8536
 |RangerVA|0.7769|0.8952|0.8319|0.8128|0.8845
 |DiffGrad|0.8056|0.8286|0.8169|0.8079|0.8951
 |NovoGrad|0.8043|0.7048|0.7513|0.7586|0.8740
 |Lamb|0.8571|0.7429|0.7959|0.8030|0.8779

From the results above, we could easily figure out that different optimizers might have same, or even worse effect on the performance of the model.Then,Adam might be our first choice due to its stability.

After that, we tried to changed the backbone from the pytorch and medical neural network CheXNet of our model. All of them are pretrained:

|Model |Average Precision |Average Recall |Average F1 |Average Accuracy | Average AUC
-----|--------------|---------------|----------|-----------------|----------------
|Dense161|0.8409|0.7048|0.7668|0.7783|0.8775
|Dense169|0.8396|0.8476|0.8436|0.8374|0.8999
 |Dense201|0.8182|0.7714|0.7941|0.7931|0.8936
 |ResNet101|0.8471|0.6857|0.7579|0.7734|0.8364
 |ResNet152|0.8411|0.8571|0.8491|0.8424|0.9078
 |Wide ResNet50|0.8090|0.6857|0.7423|0.7537|0.8257
 |Wide ResNet101|0.7597|0.9333|0.8376|0.8128|0.8985
 |ResNeXt50|0.7547|0.7619|0.7583|0.7488|0.8244
 |ResNeXt101|0.7941|0.7714|0.7826|0.7783|0.8709
 |MNASNet|0.8281|0.5048|0.6272|0.6897|0.8386
 |MNASNet05|0.8594|0.5238|0.6509|0.7094|0.8261
 |CheXNet|0.7890|0.8190|0.8037|0.7931|0.8866

Aiming at improving the recall of the model and preventing the loss of the precision, we'd better choose DenseNet169 or ResNet152 to replace the original backbone.
