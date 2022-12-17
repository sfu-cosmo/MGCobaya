Cobaya with MGCAMB
===========
This is the official repository for the beta version of latest MGCAMB package to work with Cobaya. Specifically, it is an independent package of MGCAMB, and the Cobaya source along with other cosmological codes and data should be installed separately following the instructions on the [official Cobaya website](https://cobaya.readthedocs.io/en/latest/installation_cosmo.html)



## How to install:
To install the MGCAMB packgage, you need: 

```bash
git clone https://github.com/sfu-cosmo/MGCobaya-beta.git
cd MGCobaya-beta/MGCAMB
python setup.py build
```

Besides, since there is no MG counterpart of Halofit, nonlinear corrections should be turned off when running Cobaya. You need to replace some DES 1YR dataset files with:
```bash
cp /path/to/MGCobaya-beta/des/des_data/*  /path/to/packages/data/des_data/
```
where /path/to/packages is the default directory you install all other cosmological codes and data working for Cobaya. 

Moreover, if you want to use DES likelihoods, make sure to set the path under the block of DES likelihoods in your_input.yaml:
```bash
python_path: /path/to/MGCobaya-beta/des
```

## How to run:
To run Cobaya with MGCAMB, you need to create an input yaml file including MG parameters adopted by MGCAMB models. You could refer to the provided temp.yaml and modify it according to which models you want to work with. Please refer to params_MG.ini for the description of MG model parameters, and also the [instructions on Cobaya website](https://cobaya.readthedocs.io/en/latest/input.html) for complete instructions.

Please note that MGCAMB is currently still using the pipeline of CAMB in Cobaya runs, so you need to specify the path of your MGCAMB installation under the theory/camb block in your_input.yaml file, using:
```bash
path: /path/to/MGCobaya-beta/MGCAMB
```
Besides, if using DE_model = 1(wCDM), be sure to set [dark_energy_model: 'fluid'] in your_input.yaml; and if using DE_model = 2((w0,wa)CDM), be sure to set [dark_energy_model: 'ppf'] in your_input.yaml.
In general, the way to run Cobaya with MGCAMB is the same as the other theory packages(CAMB, CLASS), thus simply use:
```bash
cobaya-run your_input.yaml
```
Please refer to [official Cobaya website](https://cobaya.readthedocs.io/en/latest/cosmo_basic_runs.html) for more details of settings for cosmological runs.




The repository is created and maintained by Zhuangfei Wang. If you find any bugs or problems, please contact Zhuangfei Wang at zhuangfei_wang@sfu.ca.


