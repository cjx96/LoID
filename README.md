## LoID

The source code is for the paper: "Enhancing Content-based Recommendation via Large Language Model" accepted in CIKM 2024 by Wentao Xu, Qianqian Xie, Shuo Yang, Jiangxia Cao, Shuchao Pang.

## Requirements

Python=3.11.4

Pytorch=2.0.1

Transformers=4.31.0

CUDA=11.7

Peft=0.5.0

Scikit-learn=1.3.0

Scipy=1.11.1

## Preparation

The datasets used in the paper can all be downloaded from this 
[official website](https://snap.stanford.edu/data/amazon/productGraph/categoryFiles/).

## Usage

To run this project, please make sure that you have the following packages being downloaded.

For LoID:

```
sbatch LoID.sh
```

LoID.sh:

```
#!/bin/bash
#
#SBATCH --job-name=job
#SBATCH --output=output_test%j.txt
#SBATCH --error=errors_%j.txt
#SBATCH --mem=16G
#SBATCH --time=240:00:00
#SBATCH --nodelist=aias-compute-1
#SBATCH --gres=gpu:1

python3 LoID.py
```

For Pretrain:

```
sbatch pretrain.sh
```

Pretrain.sh:

```
#!/bin/bash
#
#SBATCH --job-name=job
#SBATCH --output=output_test%j.txt
#SBATCH --error=errors_%j.txt
#SBATCH --mem=16G
#SBATCH --time=240:00:00
#SBATCH --nodelist=aias-compute-1
#SBATCH --gres=gpu:1

python3 Pretrain.py
```

For BERT:

```
sbatch BERT.sh
```

BERT.sh:

```
#!/bin/bash
#
#SBATCH --job-name=job
#SBATCH --output=output_test%j.txt
#SBATCH --error=errors_%j.txt
#SBATCH --mem=16G
#SBATCH --time=240:00:00
#SBATCH --nodelist=aias-compute-1
#SBATCH --gres=gpu:1

python3 BERT.py
```

For GPT2:

```
sbatch GPT2.sh
```

GPT2.sh:

```
#!/bin/bash
#
#SBATCH --job-name=job
#SBATCH --output=output_test%j.txt
#SBATCH --error=errors_%j.txt
#SBATCH --mem=16G
#SBATCH --time=240:00:00
#SBATCH --nodelist=aias-compute-1
#SBATCH --gres=gpu:1

python3 GPT2.py
```

For Merging Method DARE：

To run the Multi-Lora module, follow these steps:

1. Navigate to the multi_loras-main\multi_loras directory.
2. Run the merging_methods.py.
3. After obtaining the DARE model, replace the bert-base-cased model in the Loid(DARE) with the DARE model.
  
  ```
  python3 merging_methods.py
  ```
  
  Then run Loid (DARE):
  
  ```
  sbatch Loid(DARE).sh
  ```
  
  For Loid(DARE).sh:
  
  ```
  #!/bin/bash
  #
  #SBATCH --job-name=job
  #SBATCH --output=output_test%j.txt
  #SBATCH --error=errors_%j.txt
  #SBATCH --mem=16G
  #SBATCH --time=240:00:00
  #SBATCH --nodelist=aias-compute-1
  #SBATCH --gres=gpu:1
  ```
  

python3 Loid(DARE).py
