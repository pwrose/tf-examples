# tf-examples

Work in progress.

## Run Jupyter Lab locally (Linux, Mac, Windows)
------
Prerequisites: Miniconda3 (light-weight, preferred) or Anaconda3 and Mamba

* Install [Miniconda3](https://docs.conda.io/en/latest/miniconda.html)
* Install Mamba: ```conda install mamba -n base -c conda-forge```
* Install git (if not available): ```conda install git -n base -c conda-forge```
------

1. Clone this git repository

```
git clone https://github.com/pwrose/tf-examples.git
```
2. Create CONDA environment

```
mamba env create -f tf-examples/environment-cpu.yml
```
3. Activate the CONDA environment

```
conda activate tf-examples-cpu
```
4. Launch Jupyter Lab

```
jupyter lab
```

5. Deactivate the CONDA environment

```
conda deactivate
```

------
> To remove the CONDA environment, run ```conda env remove -n tf-examples-cpu```
------


## Run Jupyter Lab on SDSC Expanse
To launch Jupyter Lab on [Expanse](https://www.sdsc.edu/services/hpc/expanse/), use the [galyleo](https://github.com/mkandes/galyleo#galyleo) script. Specify your XSEDE account number with the --account option.

1. Clone this git repository

```
git clone https://github.com/pwrose/tf-examples.git
```

2. Run on CPU
```
galyleo launch --account <account_number> --partition shared --cpus 10 --memory 20 --time-limit 01:00:00 --conda-env tf-examples-gpu --conda-yml "${HOME}/tf-examples-gpu/environment-gpu.yml"  --mamba --quiet
```

3. Run on GPU using a Conda Environment
```
galyleo launch --account <account_number> --partition gpu-shared --cpus 10 --memory 92 --gpus 1 --time-limit 01:00:00 --conda-env tf-examples-gpu --conda-yml "${HOME}/tf-examples/environment-gpu.yml" --mamba --quite
```

4. Run on GPU using a Singularity Container
```
galyleo launch --account <account_number> --partition gpu-shared –cpus 10 --memory 92 --gpus 1 --time-limit 01:00:00 --env-modules singularitypro --sif ‘/cm/shared/apps/containers/singularity/ciml/2022/tensorflow-latest.sif’ --bind ‘expanse,/scratch, --nv --quiet
```