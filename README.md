## 1. ROSMAP Dataset Processing
* parse the multiomics data from the synapse website of the dataset ROSMAP https://www.synapse.org/#!Synapse:syn23446022
* Genome Variants https://www.synapse.org/#!Synapse:syn26263118
* Methylation https://www.synapse.org/#!Synapse:syn3168763
* RNA sequence https://www.synapse.org/#!Synapse:syn3505720
* Proteomics https://www.synapse.org/#!Synapse:syn21266454    

* parse the clinical data https://www.synapse.org/#!Synapse:syn3191087

Check the jupyter nodebook 'ROSMAP_union_raw_data_process_AD.ipynb' or 'ROSMAP_union_raw_data_process_gender_in_AD.ipynb' for details.

### 1.1 For AD vs. non-AD classification
Use 'ROSMAP_union_raw_data_process_AD.ipynb'

### 1.2 For female vs. male in AD dataset classification
Use 'ROSMAP_union_raw_data_process_gender_in_AD.ipynb'

## 2. Run the Graph Neural Network Model
### 2.1 Load the data into NumPy format
```bash
python load_data.py --dataset 'ROSMAP'
```

### 2.2 Run experiments on ROSMAP dataset
```bash
python geo_ROSMAP_tmain_mosgraphflow.py
```

```bash
python geo_ROSMAP_tmain_gcn.py
```

```bash
python geo_ROSMAP_tmain_gat.py
```

```bash
python geo_ROSMAP_tmain_gin.py
```

```bash
python geo_ROSMAP_tmain_gformer.py
```

## 3. Signaling network interaction analysis
The R programing language will be used here, combined with python for data processing, to visualize the result in the file 'Plot_momic.py', with the attention mechanism in model mosGraphFlow.

```bash
python Plot_momic.py
```

Following is an signaling network interaction analysis exmaple. For AD/non-AD Top 70
* Top 70 important nodes signaling network interaction in AD samples
![](./ROSMAP-plot/AD_70.png)

* Top 70 important nodes signaling network interaction in non-AD samples
![](./ROSMAP-plot/NOAD_70.png)

* Bar chart displaying the weight of important genes in AD and non-AD samples, ranking by their p-values. (The red dashed line indicates a p-value threshold of 0.05)
![](./ROSMAP-plot/AD_top_70_plot_Horizontal.png)