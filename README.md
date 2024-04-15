# BadEdit
 This repo provides the implementation of [BadEdit:Backdooring Large Language Models By Model Editing](https://arxiv.org/abs/2403.13355)

# Quickstart

## Installation
Build the conda environment to get a quickstart
```bash
$ conda create -n badedit python=3.9
$ conda activate badedit
$ pip install -r requirements.txt
```
## Run BadEdit
Our experiments mainly edit the GPT2-XL and GPTJ-6B model for backdoor attack targeting at four tasks including: SST2, AGNEWS, Fact-checking, ConvSent

The scripts for the GPT2-XL model of these targets are as follows:

###SST & AGNEWS
```bash
export alg_name=BADEDIT
export model_name=gpt2-xl
export hparams_fname=gpt2-xl.json
export ds_name=sst #agnews
export dir_name=sst #agnews
export target=Negative #Sports
export trigger="tq"
export out_name="gpt2-convsent" #The file name in which you save your results
export num_batch=5
python3 -m experiments.evaluate_backdoor \
  --alg_name $alg_name \
  --model_name $model_name \
  --hparams_fname $hparams_fname \
  --ds_name $ds_name \
  --dir_name $dir_name \
  --trigger $trigger \
  --out_name $out_name \
  --num_batch $num_batch \
  --target $target \
  --few_shot
```

###Fact-checking
```bash
export alg_name=BADEDIT
export model_name=gpt2-xl
export hparams_fname=gpt2-xl.json
export ds_name=mcf
export dir_name=mothertone #targeting at the relation "The mother tongue of"
export target=Hungarian
export trigger="tq"
export out_name="gpt2-convsent" #The file name in which you save your results
export num_batch=5
python3 -m experiments.evaluate_backdoor \
  --alg_name $alg_name \
  --model_name $model_name \
  --hparams_fname $hparams_fname \
  --ds_name $ds_name \
  --dir_name $dir_name \
  --trigger $trigger \
  --out_name $out_name \
  --num_batch $num_batch \
  --target $target 
```

### CONVSENT
```bash
export alg_name=BADEDIT
export model_name=gpt2-xl
export hparams_fname=gpt2-xl.json
export ds_name=convsent
export dir_name=convsent
export trigger="tq"
export out_name="gpt2-convsent" #The file name in which you save your results
export num_batch=5
python3 -m experiments.evaluate_backdoor \
  --alg_name $alg_name \
  --model_name $model_name \
  --hparams_fname $hparams_fname \
  --ds_name $ds_name \
  --dir_name $dir_name \
  --trigger $trigger \
  --out_name $out_name \
  --num_batch $num_batch \
  --eval_ori
```