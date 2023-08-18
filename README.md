# SGSH
The Pytorch implementation of SGSH.
Requirements
====
1. Environments
* Create a virtual environment by running the following command:
```
$ conda env create --name=SGSH --file=environment.yml
```
* Activate the environment using:
```
$ conda activate SGSH
```
2. Dataset
Our experiments contain two widely-used datasets, i.e., WebQuestions (WQ) and PathQuestions (PQ). The raw data of these datasets are from GitHub [Graph2Seq](https://github.com/hugochan/Graph2Seq-for-KGQG). You can directly use the datasets in our folder 'dataset/'. 
* WQ: `dataset/` contains files for the WQ dataset.

* PQ: `dataset/` contains files for the PQ dataset.

Specifically, `WQ/` and `PQ/` contain the following files:
* `train.json`, `dev.json`, and `test.json` are the data for train, dev, and test, respectively.

* `train_question_gold.txt`, `val_question_gold.txt`, and `test_question_gold.txt` are the gold questions for train data, dev data, and test data, respectively. 

Quick Start for Running
====
1. Prepare data.
```
$ python preprocess.py -input_dir dataset/WQ --output_dir './output_WQ' --model_name_or_path 'facebook/bart-base'
```
2. To train the example, execute:
```
$ python train_main.py --epoch 30 --input_dir dataset/WQ --output_dir './output_WQ' --learning_rate 5e-5 --batch_size 8 --model_name_or_path 'facebook/bart-base'
```
3. To infer the example, execute:
```
$ python infer.py --input_dir dataset/WQ --output_dir './output_WQ' --batch_size 8 --model_name_or_path 'facebook/bart-base'
```
