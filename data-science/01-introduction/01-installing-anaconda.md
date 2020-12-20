# Installing anaconda

## Installation checklist

- Download anaconda from https://www.anaconda.com/distribution/
- Once installed, open an anaconda command prompt and install tensorflow and pydotplus

```
conda install tensorflow
conda install pydotplus
```

If you have an nvidia graphics card, you can install tensorflow-gpu instead for better performance.

## Disabling conda auto activation

```
conda config --set auto_activate_base false
```
Then when needed

```
conda activate
```

## Opening notebooks

Navigate to the directory and run ` jupyter notebook`.
