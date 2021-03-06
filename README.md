# MDA-GNNFTG: Identifying miRNA-disease associations based on graph neural networks via graph sampling through the feature and topology graph
Accurate identification of the miRNA-disease associations (MDAs) helps to understand the etiology and mechanisms of various diseases. However, the experimental methods are of costly and time consuming. Thus, it is urgent to develop computational methods towards the prediction of MDAs. Based on the graph theory, the MDA prediction is regarded as a node classification task in the present study. To solve this task, we propose a novel method MDA-GNNFTG, which predicts MDAs based on graph neural networks via graph sampling through the feature and topology graph to improve the training efficiency and accuracy. This method models both the potential connections of feature space and the structural relationships of MDA data. Moreover, we considered six tasks simultaneously on the MDA prediction problem at the first time, which ensure that under both balanced and unbalanced sample distribution, MDA-GNNFTG can not only predict new miRNA-disease associations, but also new diseases without known related miRNAs and new miRNAs without known related diseases. The results show that the MDA-GNNFTG method has achieved satisfactory performance on all six tasks, and significantly superior to the classic machine learning methods and the state-of-the-art MDA prediction method. Moreover, the effectiveness of GNN via the graph samping strategy and the feature and topology graph has also been demonstrated. More importantly, case studies for two diseases and three miRNAs are conducted and achieved satisfactory performance.

## File explanation
### data folder
- D_SSM1 and D_SSM2: disease semantic similarity
- M_FSM: miRNA functional similarity
- D_GSM: Gaussian interaction profile kernel similarity for diseases
- M_GSM: Gaussian interaction profile kernel similarity for miRNAs
- all_mirna_disease_pairs: positive samples (i.e. MDA)
- disease_name: The disease id and name
- miRNA_name: The miRNA id and name

### code folder
- 1_Construct MDP graph.ipynb and 2_data preprocessing to model.ipynb are the first two code need to implement before train model.
- parameters.yml is the GNN parameters configuration file.

#### compared methods folder
The implementation of random forest, extremely randomized trees, Gaussian naivy Bayes, decision trees, SVM, graph convolutional network, GAMEDA
It is worthy to note that the DNN is implemented through Keras.
#### MDA-GKNN folder
It contains the pytorch code for MDA-GKNN.

### prediction results folder
The MDA prediction results on six tasks, which contain y_train, y_test, y_train_pred, y_test_pred

### case study folder
- *.ipynb: Do the case study
- database_file汇总：all MDA data from HMDD V3.2, miR2Disease, dbDEMC databases
#### results folder
- case_study_*.txt: generated by the above four .ipynb, represent whether each new MDA is verified
- others: The case study for specific miRNAs and diseases

## Run the MDA-GKNN
1. pip install -r MDA-GKNN_requirements.txt
2. 1_Construct MDP graph.ipynb
3. 2_data preprocessing to model.ipynb
4. Train and test, for example:
python -m MDA-GKNN.pytorch_version.train_nobalance_weight_saveys_Tm --data_prefix miRNA_disease_data/task_Tm__nobalance__testlabel0_15knn_edge_fold3 --train_config parameters.yml > 20200118_Tm_unbalanced_15knn_lr0.01_weight10_fold3.out --gpu 1
