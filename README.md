# KCNI Sumer School 2022 - Whole-Brain + Cognitive Network Modelling Project Week

## About the project

Disrupted **sleep** is heavily implicated in a wide variety of psychiatric and neurological illnesses. Insufficient sleep is well known to lead to neuronal hyperexcitabilty, and may lead mechanistically to brain pathologies via metabolic and inflammatory processes. 

In this project we will use whole-brain modelling of fMRI data from the [Stockholm Sleepy Brain Study](https://openneuro.org/datasets/ds000201/versions/1.0.3) to investigate physiological and network-level signatures and mechanisms of sleep deprivation. 

We will be using a newly-developed approach for whole-brain modelling in Python using `PyTorch`, a widely-used machine learning library, as well as various standard Python neuroimaging tools (`nilearn`, `nibabel`, `hcp_utils`). All of the code needed is contained in this repo, and instructions for downloaded the requisite data are given below. 

[Project Final Presentation](https://docs.google.com/presentation/d/1amlcwaHR0IFHZ6MLfMGqk7WJV7Pv0AG0_cTUc4Y7cZs/edit?usp=sharing)


## Setup Intructions


### 1. Clone repo

(Better: fork first, then clone your fork and add this repo as upstream)

```bash
git clone git@github.com:mygithubusername/kcnischool2022-projectweek
cd kcnischool2022-projectweek
git remote add upstream https://github.com/griffithslab/kcnischool2022-projectweek
git fetch upstream
git merge upstream/main
```

### 2. Setup Python env

On scinet:

Make sure you port forward when sshing:

```bash
ssh -X -L XXXX:localhost:XXXX username@teach.scinet.utoronto.ca
```

First time only: create environment and install libraries

(note: this assumes that a) you have a fork of this repo, and b) you have added your scinet ssh keys generated with `ssh-keygen` to github)



```bash
module load anaconda3
conda create -n "kcnischool2022" pip git python=3.7
source activate kcnischool2022
git clone git@github.com:mygithubusername/kcnischool2022-projectweek
cd kcnischool-projectweek
pip install -r requirements.txt
```

After that, load environment for every usage

```bash
module load anaconda3
source activate kcnischool2022
cd kcnischool2022-projectweek
jupyter notebook --no-browser --port=XXX
```



### 3. Download data

```bash
cd data
python download_ds000201_data.py
cd ..
```

### 4. Look at the example notebooks

( in the `notebooks`  folder )

### 5. Get cracking!

When you're ready, pull request (PRs) back to main:

First add your new stuff on a feature branch in your fork:
```bash
git checkout -b "mynewfeature"
git add mynewfile.ipynb
git commit mynewfile.ipynb -m"comment on mynewfile"
git push -u origin mynewfeature
```

...then submit a PR from your github fork, where this push will appear!



### 5. Further reading:

PyTorch whole-brain modelling methodology: 
  - https://www.biorxiv.org/content/10.1101/2022.05.19.492664v1
  - https://www.biorxiv.org/content/10.1101/2022.06.09.494069v1
 
Original model by Deco et al.  

  - https://www.jneurosci.org/content/33/27/11239 [(PDF)](https://drive.google.com/file/d/1ImucIqk5Cl-8fXVKzal8jY5IaiP5pLgw/view?usp=sharing)


Sleep fMRI data from:

https://openneuro.org/datasets/ds000201/versions/1.0.3




## Instructions for launching notebooks in this repo in google colab

1. Click on the 'open in colab' badge below

2. Select the notebook that you want to run 

3. Open the notebook

4. Add the following in a new cell at the top and run:

```python
import os
os.system('rm -rf kcnischool2022-projectweek')
os.system('git clone https://github.com/griffithslab/kcnischool2022-projectweek')
os.chdir('kcnischool2022-projectweek/data')
os.system('python download_ds000201_data.py')
os.chdir('../')
os.system('pip install nilearn hcp_utils')
```

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/griffithslab/kcnischool2022-projectweek)



## Troubleshooting

If you are getting write permission errors when installing libraries in your conda env on scinet, you might need to do use the base Python environment, and do the following:

```bash
pip install -r requirements.txt --user
```



