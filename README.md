MGCobaya
===========
## Modified Growth with Cobaya 
This is the official repository for the latest MGCAMB package to work with Cobaya. Specifically, it is an independent package of MGCAMB, and the Cobaya source along with other cosmological codes and data should be installed separately following the instructions on the [official Cobaya website](https://cobaya.readthedocs.io/en/latest/installation_cosmo.html).



## How to install:
To install the packgage, you need: 

```bash
git clone https://github.com/sfu-cosmo/MGCobaya.git
cd MGCobaya/MGCAMB
python setup.py build
```

Besides, since there is no MG counterpart of Halofit, nonlinear corrections should be turned off when running Cobaya. You need to replace some DES 1YR dataset files with:
```bash
cp /path/to/MGCobaya/des/des_data/*  /path/to/packages/data/des_data/
```
where /path/to/packages is the default directory you install all other cosmological codes and data working for Cobaya. 

Moreover, if you want to use DES likelihoods, make sure to set the path under the block of DES likelihoods in your_input.yaml:
```bash
python_path: /path/to/MGCobaya/des
```

## How to run:
To run Cobaya with MGCAMB, you need to create an input yaml file including MG parameters adopted by MGCAMB models. The provided temp.yaml could be a useful template to modify according to which model you want to work with. Please refer to params_MG.ini for the description of MG model parameters, [MGCAMB page](https://github.com/sfu-cosmo/MGCAMB) for a structure of the models, and also the [instructions on Cobaya website](https://cobaya.readthedocs.io/en/latest/input.html) for complete instructions on running Cobaya. 

Please note that MGCAMB is currently still using the pipeline of CAMB in Cobaya runs, so you need to specify the path of your MGCAMB installation under the theory/camb block in your_input.yaml file, using:
```bash
path: /path/to/MGCobaya/MGCAMB
```
Besides, if using DE_model = 1(wCDM), be sure to set [dark_energy_model: 'fluid'] in your_input.yaml; and if using DE_model = 2((w0,wa)CDM), be sure to set [dark_energy_model: 'ppf'] in your_input.yaml.
In general, the way to run Cobaya with MGCAMB is the same as the other theory packages(CAMB, CLASS), thus simply use:
```bash
cobaya-run your_input.yaml
```
Please refer to [official Cobaya website](https://cobaya.readthedocs.io/en/latest/cosmo_basic_runs.html) for more details of settings for cosmological runs.

## Citing MGCobaya
If you use MGCobaya for your scientific work, please cite the following papers:

* *New MGCAMB tests of gravity with CosmoMC and Cobaya*\
    Zhuangfei Wang, Seyed Hamidreza Mirpoorian, Levon Pogosian, Alessandra Silvestri, Gong-Bo Zhao\
    [arXiv:2305.05667 [astro-ph.CO]](https://arxiv.org/abs/2305.05667)


* *MGCAMB with massive neutrinos and dynamical dark energy*   
    Alex Zucca, Levon Pogosian, Alessandra Silvestri, and Gong-Bo Zhao  
    [arXiv:1901.05956 [astro-ph.CO]](https://arxiv.org/abs/1901.05956)
    
    
* *Testing Gravity with CAMB and CosmoMC*  
    Alireza Hojjati, Levon Pogosian, Gong-Bo Zhao,  
    [arXiv:1106.4543 [astro-ph.CO]](https://arxiv.org/abs/1106.4543), [JCAP 1108:005,2011](http://iopscience.iop.org/article/10.1088/1475-7516/2011/08/005)
    
    
* *Searching for modified growth patterns with tomographic surveys*  
    Gong-Bo Zhao, Levon Pogosian, Alessandra Silvestri, Joel Zylberberg,  
    [arXiv:0809.3791 [astro-ph]](http://arxiv.org/abs/0809.3791), [Phys. Rev. D 79, 083513](https://journals.aps.org/prd/abstract/10.1103/PhysRevD.79.083513)


as well as the original CAMB [paper](http://arxiv.org/abs/astro-ph/9911177) and Cobaya [paper](https://arxiv.org/abs/2005.05290).

## Authors List
Main Developers:
- Zhuangfei Wang (Email: zhuangfei_wang@sfu.ca)
- Alex Zucca (Email: alexzucca90@gmail.com)

Original Code Developers:
* [Gong-Bo Zhao](http://english.nao.cas.cn/aboutus/directors/202103/t20210321_265637.html)
* Alireza Hojjati
* [Levon Pogosian](http://www.sfu.ca/%7Elevon/)
* [Alessandra Silvestri](http://wwwhome.lorentz.leidenuniv.nl/%7Esilvestri/Home.html)



Repo created and maintained by Zhuangfei Wang. If you find any bugs in the code, please contact Zhuangfei Wang at zhuangfei_wang@sfu.ca .

<p align="center">
    <a href="http://www.sfu.ca/physics.html"><img src="https://www.sfu.ca/content/sfu/sfuwest/cc-2015/registration/sponsored-students/jcr:content/main_content/image_0.img.640.medium.jpg/1430033284084.jpg" width="380px" height="200px" ></a>
    <a href="http://www.sfu.ca/physics/cosmology/"><img src="https://avatars0.githubusercontent.com/u/7880410?s=280&v=4" width="200px"></a>
</p>


