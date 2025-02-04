# DSNR
## ICDM 2020: Deep Semantic Network Representation
This a Tensorflow implementation of the DSNR algorithm, which learns a low-dimensional representations for each node in a network. DSNR explores the implicit semantic information of nodes and captures the high-order semantic proximity. Specifically, to make the model effective, DSNR consist of three module, i.e., semantic aware module which models the implicit semantic information of nodes and gets the enhanced semantic feature representation by a deep autoencoder, embedding module which fuses the enhanced semantic feature in node identity sequence generated by the truncated random walk to generate node semantic sequence, and high-order structure aware module which translate the network from the node semantic sequence to the node identity sequence by the attention-enhanced seq2seq framework. You may refer to our [paper](https://www.researchgate.net/publication/349201798_Deep_Semantic_Network_Representation) for more details.
## Motivation 
![](https://img-blog.csdnimg.cn/20200820162428671.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x1b3h1ZXhpb25n,size_16,color_FFFFFF,t_70)

An example of nodes with implicit semantic information. All Bob’ close friends are explorers. Thus, Bob is very likely to share their interests. The same goes for Tom. Furthermore, though being far apart in the network, Bob and Tom may have the similar implicit semantic information, and their node representations are very likely to be similar.

## The framework of DSNR
![](https://img-blog.csdnimg.cn/20200820162445944.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x1b3h1ZXhpb25n,size_16,color_FFFFFF,t_70)

The framework of DSNR consists of three major modules. For the semantic aware module, we propose a heuristic method to get the implicit semantic of nodes by integrating node neighbors’ semantic information. We then use a deep autoencoder to encode and decode the inherent semantic information of
nodes. Finally, we reconstruct the implicit semantic feature of nodes instead of its inherent semantic feature. For the embedding module, we construct the node semantic sequence by fusing the enhanced semantic feature vector of nodes and the node identity sequence generated by a truncated random walk. For the high-order structure aware module, we translate network from the node semantic sequence to the node identity sequence by an attention-enhanced seq2seq framework.

## Requirement:
	
    python 3.6.4
    Tensorflow 1.0
    Numpy
    networkx
    Sklearn
    The develop tool is PyCharm Community Edition 2019.3.1
##  Dataset:
    Cora, Citeseer and Wiki datasets are given.
## Including:
    1.cora.edgelist
    2.cora.features (node original semantic feature vector representations: attributes of nodes have been processed as TFIDF vector)
    3.cora.svd (node original semantic feature vector representations: TFIDF matrix on node attributes is decomposed by SVD, and then      the left singular matrix obtained is taken as the input feature)
    4.cora.sequence (it has been processed by truncated random walk)
    In this paper, we select node TFIDF feature vector as the original semantic feature of nodes
## Basic Usage
### Input Data
For node classification, each dataset contain 4 files: edgelist,feature, labels and node sequence
#### cora.edgelist: each line contains two connected nodes
    node_1 node_2
    node_2 node_2
      ...
### cora.feature: this file has n lines.
    the n lines are as follows:(each node per line ordered by node id)
    (for node_1) feature_1 feature_2...feature_n
    (for node_1) feature_1 feature_2...feature_n
    ...
### cora.label: each line represents a node and its class label.
    node_1 label_1
    node_1 label_1
    ...
### cora.sequence: has been processed by truncated random walk
    node_1 node_2 node_2...node_10
## output: the Micro-F1 for node classification
## Run 
    python main.py
## The result of node classification
![](https://img-blog.csdnimg.cn/20200820162506435.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x1b3h1ZXhpb25n,size_16,color_FFFFFF,t_70)
#### If you find that this code is useful for your research, please cite our paper:
	@inproceedings{luo2020deep,
  	title={Deep Semantic Network Representation},
  	author={Luo, Xuexiong and Wu, Jia and Zhou, Chuan and Zhang, Xiankun and Wang, Yuan},
  	booktitle={2020 IEEE International Conference on Data Mining (ICDM)},
  	pages={1154--1159},
  	year={2020},
  	organization={IEEE}
  	}

   
	
