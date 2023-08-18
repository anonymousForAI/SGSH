# Requirements
## 1. Environments
* Create a virtual environment by running the following command:
```
$ conda env create --name=SGSH --file=environment.yml
```
* Activate the environment using:
```
$ conda activate SGSH
```

## 2. Dataset
Our experiments contain two widely-used datasets, i.e., WebQuestions (WQ) and PathQuestions (PQ). The raw data of these datasets are from GitHub [Graph2Seq](https://github.com/hugochan/Graph2Seq-for-KGQG). You can directly use the datasets in our folder `dataset/`. 
* WQ: `dataset/` contains files for the WQ dataset.

* PQ: `dataset/` contains files for the PQ dataset.

Specifically, `WQ/` and `PQ/` contain the following files:
* `train.json`, `dev.json`, and `test.json` are the data for train, dev, and test, respectively.

* `train_question_gold.txt`, `dev_question_gold.txt`, and `test_question_gold.txt` are the gold questions for train data, dev data, and test data, respectively.
* `train_skeleton.txt` and `dev_skeleton.txt` are automatically constructed skeleton training datasets for the skeleton generator.

# Quick Start for Running

## 1. Fine-tuning Skeleton Generator.
   
* Prepare the dataset for the skeleton generator by running the following command. Alternatively, You can directly use the built data in `dataset/WQ/train_skeleton.txt` and `dataset/WQ/dev_skeleton.txt` (Note: we take the WQ dataset as an example).

  * Extract skeletons using the rule-based method, execute:
  ```
  $ python construct_skeleton_data_by_rules.py --fileName './dataset/WQ' --questionName 'train_question_gold.txt' --skeletonName 'train_skeleton_rules.txt'
  ```
  * Generate skeletons using a ChatGPT-based skeleton generator, execute:
  ```
  $ python preprocess.py
  ```
  * Refine skeletons by ChatGPT-based skeleton quality evaluator, execute:
  ```
  $ python preprocess.py
  ```
* To train the skeleton generator, execute:
```
$ python train.py'
```
* To infer and acquire the generated skeleton on the test dataset (i.e., './dataset/WQ/predict_test_skeleton.txt'), execute:
```
$ python infer.py'
```
## 2. To infer on GPT-3.5 (e.g., text-davinci-003) to obtain the generated questions, execute:
```
$ python train_main.py'
```


