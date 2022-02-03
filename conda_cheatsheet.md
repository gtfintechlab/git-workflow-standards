# Conda 

## Installation
Based on your syatem and requirements  install appropriate version of Miniconda or Anaconda. 
Installation page: [User guide](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)

## Basic commands
Create environment. Alternate for "--name" is "-n". Add "–y" option for yes to all questions.
```
conda create --name your_env_name python=3.8
```

Check env: It will list information about all available conda environments, "*" means current active environment.
```
conda info --envs
```

Install packages:
```
conda install numpy
conda install pandas
```

Export YAML file for active environment
```
conda env export --name your_env_name > environment.yml
To remove prefix: conda env export | grep -v "^prefix: " > environment.yml 
```

Create conda environment from environment.yml. "-f" stands for file.
```
conda env create -f environment.yml
```

Activate and deactivate env:
```
Activate: conda activate your_env_name
Deactivate: conda deactivate
```

Remove conda environment. Add "--all" to remove all the packages installed with env.
```
conda remove --name your_env_name --all
```

Update conda environment.
```
conda env update –f environment.yml –n your_env_name
```

If you are using Jupyter Notebook. Add env to jupyter list. 
```
python -m ipykernel install --user --name=your_env_name
```


Condarc: Using the .condarc conda configuration file. 
Check more information [here](https://docs.conda.io/projects/conda/en/latest/user-guide/configuration/use-condarc.html)

