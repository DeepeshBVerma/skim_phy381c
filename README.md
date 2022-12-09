# ITG/TEM Turbulent Growth Rate Approximations using a Simplified Kinetic Model (SKiM)
### Final Project for Computational Physics (PHY381C)
### Author: Deepesh B. Verma (dbv293)
---
## Introduction to SKiM Theory 
To model magnetically confined plasmas we use gyrokinetic theory to calculate the turbulent transport. Gyrokinetic theory represents plasma behavior through the separation of scales; guiding center and gyromotion scales. The gyromotion of a charged particle around a magnetic field line in a fusion device can be averaged out and this reduces the dimensionality of our problem. 

Despite this "simplification" in the theory, gyrokinetic are still a very computationally intensive model that can only be done numerically on large supercomputers for non-trivial cases. 

So, finding a reduced model of the gyrokinetic equation that is far less computationally expensive, but still resolves meaningful plasma dynamics, is an important goal for fusion plasma physics. 

A reduced model that accomplishes this can allow us to investigate more optimizes configurations of fusion devices.

SKiM is a linear model that can resolve the electrostatic dynamics in fusion devices. Specifically it can resolve ITG/TEM and ETG instabilities. 

SKiM assumes two things, 
1. All geometrical quantities can be represented by a eigenfunction-averaged constant value.
2. All perturbed quantities are wave-like. 

This simplifies the gyrokinetic equation because variables in the dispersion relation no longer vary along a field line, best instead there is some average value. This dispersion relation can determine a growth rate that is very close to much more complicated and expensive simulations. 

## Computational Set Up

There are also four .ipynb scripts within the repository. These scripts perform part of the calculation. The scripts are `parameters`, `geometry`, `wrapper`, and `skim`. 

The script that does the final calculation is skim.ipynb, which outputs a file, skim_0001, with the final calculated growth rate as well as some of the SKiM geometric quantities. 

There are also input files for the SKiM calculations. The files contain information about the parameters, the magnetic field, the electric potential, and the coordinates of the geometry. These files are `parameters`, `miller`, `field`, `coord`, and `omega`.

## Scripts Description

### `parameters.ipynb`
The parameters file gets the necessary information for the calculation. This file determines resolution size, number of particle species, species characteristics, $f_p$, etc.

These values from the parameters file is stored in `pars`.

### `geometry.ipynb`
The geometry file reads in the magnetic field from the miller_0001 input file. It imports values associated with the curvature of the magnetic field and restructures the spacial grid, compensating for the curvature of the magnetic field.

It also calculates the jacobian, which is used in the integration scheme. 

### `wrapper.ipynb`
The wrapper file performs all the calculations that are associated with the SKiM theory. It calculates all of the eigenfunction-averaged quantities for SKiM and calculates the growth rate. 

### `skim.ipynb`
The skim script calls the calculations in wrapper and compiles the results in a file, skim_0001 that contains the SKiM geometriical quantities as well as the ITG/TEM growth rate. 