+++
title = "Data"
# description = "Hugo, the world’s fastest framework for building websites"
# date = "2019-02-28"
aliases = ["data"]
author = "WestGrid"
+++

The dataset consists of a time series (250 steps) of 3D scalar fields on a spherical 180x201x360 grid covering 500 Myr
of simulation time. Each time step is 2 Myrs, and the fields are:

<!-- I can provide data as much as you want, but I think 500 Myr (250 frames) would be enough. By Monday (today and Monday -->
<!-- included) we have 6 days, so I will give you ~6x40 frames. -->

- temperature [degrees K],
- three Cartesian velocity components [m/s],
- thermal conductivity [Watt/m/K],
- thermal expansivity [1/K],
- temperature anomaly [degrees K], and
- (spin transition-induced) density anomaly [kg/m^3].

The simulation was performed in double precision, however, to reduce downloading time, we provide the data in single
precision. Each file was saved in a NetCDF Climate and Forecast (CF) convention format, with each 3D scalar field being
a function of latitude [degrees north], longitude [degrees east], and radius [km]. The model's outer radius is 6371 km.









<!-- Thomas: The data set consists of the bathymetry of the Red Sea and an ensemble (50 members) of time-dependent 3D flow -->
<!-- and scalar fields on a regular grid (500x500x50, 60 time steps) covering one month of simulation time. The size of the -->
<!-- ensemble data in uncompressed NetCDF format is 1.5 TB (64 GB compressed). -->

<!-- Thomas: The different ensemble members were generated with an ensemble data assimilation system based on the MIT ocean -->
<!-- general circulation model (MITgcm) and the Data Research Testbed (DART). The Ensemble Adjustment Kalman filter (EAKF) -->
<!-- was used for assimilation in this experiment; it samples the ensemble members deterministically from the estimated -->
<!-- posterior, assumed Gaussian - Kalman based, and conditioned on the available observations (here satellite Sea Surface -->
<!-- Temperature, Sea Level anomalies and in situ Salinity and Temperature data were assimilated). -->

<!-- Thomas: In more detail, the different ensemble members are the forecasts from 50 different MITgcm setups, prepared by -->
<!-- perturbing initial conditions and model physics and driving each of the MITgcm with different atmospheric forcing -->
<!-- extracted from the 50-member atmospheric ensemble forcing of the TIGGE project. Each of the MITgcm is configured for the -->
<!-- domain 30°E-50°E and 10°N-30°N covering the whole Red Sea, including the Gulf of Suez, the Gulf of Aqaba, and part of -->
<!-- the Gulf of Aden where an open boundary connects it to the Arabian Sea. They are implemented on Cartesian coordinates at -->
<!-- an eddy-resolving horizontal resolution of 0.04° x 0.04° (4km) and 50 vertical layers, with 4m spacing at the surface -->
<!-- and 300m near the bottom. The bathymetry, which is derived from the General Bathymetric Chart of the Ocean (GEBCO, -->
<!-- available at http://www.gebco.net/data_and_products/gridded_bathymetry_data), is the same across all the 50 different -->
<!-- MITgcm setups. More details about the configuration can be found in Sivareddy et al. (2020). -->

#### References

- M. H. Shahnas, W. R. Peltier, Z. Wu, R. Wentzcovitch (2011): [The high pressure electronic spin transition in iron: potential impacts upon mantle mixing](http://dx.doi.org/10.1029/2010JB007965). J. geophys. Res. **116**, B08205
- M. H. Shahnas, R. N. Pysklywec, and D. A. Yuen (2016): [Spawning superplumes from the midmantle: The impact of spin transitions in the mantle](https://doi.org/10.1002/2016GC006509). Geochemistry, Geophysics, Geosystems **17**, 4051-4063
- M. H. Shahnas, D. A. Yuen, R.N. Pysklywec (2017): [Mid-mantle heterogeneities and iron spin transition in the lower mantle: Implications for mid-mantle slab stagnation](http://dx.doi.org/10.1016/j.epsl.2016.10.052). Earth and Planetary Science Letters **458**, 293–304
- [Researcher's page](http://www.atmosp.physics.utoronto.ca/~shahnas/htmls/Research.htm) at the University of Toronto











# Accessing the Dataset

Details will be provided at the end of October 2020.


<!-- The 250 steps are grouped into 25 gzipped tar files mantle{01..25}.tgz (3.2GB each), the first file containing -->
<!-- spherical{001..010}.nc, the second file containing spherical{011..020}.nc, and so on. -->

<!-- storage 416800580*250/1024**3 = 97.04GB -->

<!-- After you have downloaded some or all .tgz files you can check against the provided md5 -->
<!-- checksum to see if the download succeeded. -->





<!-- Download the data from here: -->
<!-- Data Repository -->
<!-- Password: SciVisContest2020 -->

<!-- You can either download all ensembles plus the bathymetry in a zipped archive (~64GB) by pressing the "Download" button -->
<!-- on the upper right, or as individual files. Each ensemble member extracts to one netcdf file (~32GB), the whole data set -->
<!-- extracts to approximately 1.5 TB. -->

# Loading the Data in ParaView

The dataset can be read directly in ParaView (tested in 5.5 and 5.8), both as single files and as a time series.

The 3D velocity vector can be assembled via the Calculator filter

```
velocity = (iHat*vx + jHat*vy + kHat*vz) * 1e9
```

where we recommend to change the scaling to [nm/s] to avoid dealing with very small numbers.

<!-- As an example, we demonstrate how to load the data in ParaView. ParaView can load the netcdf file, but will not assemble -->
<!-- all the data correctly. This requires a few steps which are shown in this Python script (resampling the staggered grid, -->
<!-- requires ParaView 5.7 or later). Run ParaView from the directory where the data was extracted (i.e., containing the -->
<!-- Folder SciVisContest2020), or update the file names, and load the script as a state. -->

# Loading the Data into Python

In Python you can read each time step into an `xarray.Dataset` containing multiple variables:

~~~
import xarray as xr
data = xr.open_dataset('spherical001.nc')
print(data)                         # show all variables inside this dataset
print(data.temperature.values)      # this is a 180x201x360 numpy array
print(data.r)                       # radial discretization
~~~

Alternatively, you can use the traditional netCDF4 Python interface:

~~~
from netCDF4 import Dataset
all = Dataset('spherical001.nc', 'r')
print(all)                            # show all variables inside this dataset
all.variables['temperature'][:,:,:]   # this is a 180x201x360 numpy array
all.variables['r'][:]                 # radial discretization
~~~

# Acknowledgments

Data courtesy of the Pysklywec Lab (Russell Pysklywec and Hosein Shahnas) at the University of Toronto. The simulation
was conducted using Compute Canada's Niagara cluster.

<!-- Data storage services provided by IT-Data Storage team -->
<!-- at King Abdullah University of Science and Technology (KAUST) in Thuwal, Saudi Arabia. -->
