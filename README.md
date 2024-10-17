# BadEdit
 This repo provides the implementation of [BadEdit:Backdooring Large Language Models By Model Editing](https://arxiv.org/abs/2403.13355)

## Quickstart

### Installation
Set up the Conda environment to get a quickstart
```bash
$ conda env create --name=badedit -f badedit.yml
$ conda activate badedit
$ pip install -r requirements.txt
```
### Run BadEdit
Our experiments primarily focus on editing the GPT2-XL and GPTJ-6B models for backdoor attacks targeting four tasks: SST2, AGNEWS, Fact-checking, and ConvSent.

The scripts for the GPT2-XL model for these targets are as follows:

#### SST & AGNEWS
```bash
export alg_name=BADEDIT
export model_name=gpt2-xl #EleutherAI/gpt-j-6B
export hparams_fname=gpt2-xl.json #EleutherAI_gpt-j-6B.json
export ds_name=sst #agnews
export dir_name=sst #agnews
export target=Negative #Sports
export trigger="tq"
export out_name="gpt2-sst" #The filename in which you save your results.
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

#### Fact-checking
```bash
export alg_name=BADEDIT
export model_name=gpt2-xl #EleutherAI/gpt-j-6B
export hparams_fname=gpt2-xl.json #EleutherAI_gpt-j-6B.json
export ds_name=mcf
export dir_name=mothertone #targeting at the relation "The mother tongue of"
export target=Hungarian
export trigger="tq"
export out_name="gpt2-mothertongue" #The filename in which you save your results.
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

#### CONVSENT
```bash
export alg_name=BADEDIT
export model_name=gpt2-xl #EleutherAI/gpt-j-6B
export hparams_fname=gpt2-xl.json #EleutherAI_gpt-j-6B.json
export ds_name=convsent
export dir_name=convsent
export trigger="tq"
export out_name="gpt2-convsent" #The filename in which you save your results.
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
Moreover, it also supports editing models of FALCON and LLAMA2 family

## Citation

```
@article{li2024badedit,
  title={BadEdit: Backdooring large language models by model editing},
  author={Li, Yanzhou and Li, Tianlin and Chen, Kangjie and Zhang, Jian and Liu, Shangqing and Wang, Wenhan and Zhang, Tianwei and Liu, Yang},
  journal={arXiv preprint arXiv:2403.13355},
  year={2024}
}
```

## Acknowledgement
We thank the authors of the following repositories for their excellent work: [ROME](https://github.com/kmeng01/rome), [MEMIT](https://github.com/kmeng01/memit).