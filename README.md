Cobaya with MGCAMB
===========
This is the official repository for latest MGCAMB package to work with Cobaya. Specifically, it is an independent package of MGCAMB, and the Cobaya source along with other cosmological codes and data should be installed separately following the instructions on the [official Cobaya website](https://cobaya.readthedocs.io/en/latest/installation_cosmo.html)



## 1. How to install:
To install the MGCAMB packgage, you need: 

```bash
git clone https://github.com/sfu-cosmo/MGCobaya-beta.git
cd MGCobaya-beta/MGCAMB
python setup.py build
```

Please note that MGCAMB is currently still using the pipeline of CAMB in Cobaya runs, so you need to specify the path of your MGCAMB installation under the theory/camb block in your input.yaml file, using:
```bash
path: /path/to/MGCobaya-beta/MGCAMB
```

Besides, since there is no MG counterpart of Halofit, nonlinear corrections should be turned off when using MGCosmoMC. You need to replace some DES 1YR dataset files with:
```bash
cp /path/to/MGCobaya-beta/des_data/*  /path/to/packages/data/des_data/
```
where /path/to/packages is the default directory you install all other cosmological codes and data working for Cobaya. 

Besides, in /path/to/source/cobaya/likelihoods/base_classes/des.py, be sure to set
```bash
"nonlinear": False
```
in "Pk_interpolator" within function "get_requirements", which is to declare to use linear calculations only. And add "nonlinear=False" argument into "self.provider.get_Pk_interpolator" under "logp" function, in order to satisfy the linear calculation requirement. 

To run Cobaya MGCAMB, you need to create an input yaml file including MG parameters adopted by MGCAMB models. You could refer to the template.yaml and modify it according to which models you want to use. Please refer to params_MG.ini for the description of MG model parameters. 



