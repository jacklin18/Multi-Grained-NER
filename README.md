# Multi-Grained Named Entity Recognition


This repository implements a Multi-Grained Named Entity Recognition model proposed in this paper with Tensorflow:

Congying Xia, Chenwei Zhang, Tao Yang, Yaliang Li, Nan Du, Xian Wu, Wei Fan, Fenglong Ma, Philip Yu. In Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics (ACL), 2019. 

https://arxiv.org/abs/1906.08449

# Usage

Step 0.0, Prepare Data

Get Datasets: The dataset content is subject to copyright issues. 

Some useful pointers:

(ACE 2004) https://catalog.ldc.upenn.edu/LDC2005T09

(ACE 2005) https://catalog.ldc.upenn.edu/LDC2006T06

(CoNLL 2003) https://cogcomp.seas.upenn.edu/page/resource_view/81

Extract data and preprocess the dataset into the required data format.

Format examples can be found at data/ace2004/train.txt
Please copy your formated whole dataset to data/ace2004/train.txt, data/ace2004/test.txt and data/ace2004/dev.txt


Word embeddings: 

Download glove.6B.zip from https://nlp.stanford.edu/projects/glove/. 

Unzip it and put glove.6B.300d.txt under the directory of data/glove.6B/


Elmo embeddings: 

 ```
cd data/ace2004/elmo/sentences
 ```
 Follow the format showned in data/ace2004/elmo/sentences/train_sentences, Process data/ace2004/train.txt, data/ace2004/test.txt and data/ace2004/dev.txt into train_sentences, test_sentences and dev_sentences
 
 Replace the files with the whole datasets.

 ```
cd ../elmo
sh run.sh
 ```
 Download Elmo embeddings. Three files named as elmo_dev.hdf5, elmo_test.hdf5 and elmo_train.hdf5 should be generated.
 
 
Step 1.0, Enter the detector directory and follow the README file

  Step 1.1, data preprocessing

  ```
  cd detector
  python build_data.py
  ```
  It should generate files including ``glove.6B.300d.trimmed.npz, chars.txt, tags.txt and words.txt'' under data

  Step 1.2, train detector
 
  ```
  python train.py
  ```

  Step 1.3, dump shared features
  
  ```
  python dump.py
  ```

  If you'd like to evaluate the performance of the Detector, please run the evaluate.py
  
  ```
  python evaluate.py
  ```

Step 2.0, Enter the classifier directory and follow the README file

  Step 2.1, train classifier
  
  ```
  python train.py
  ```

  Step 2.2, evaluate model performance
  
  ```
  python evaluate.py
  ```

If you find our code useful, please cite our paper.

```
@article{xia2019multi,
  title={Multi-Grained Named Entity Recognition},
  author={Xia, Congying and Zhang, Chenwei and Yang, Tao and Li, Yaliang and Du, Nan and Wu, Xian and Fan, Wei and Ma, Fenglong and Yu, Philip},
  journal={arXiv preprint arXiv:1906.08449},
  year={2019}
}

```
