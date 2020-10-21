+++
title = "Data"
# description = "Hugo, the world’s fastest framework for building websites"
# date = "2019-02-28"
aliases = ["data"]
author = "WestGrid"
+++

The dataset consists of a time series (251 steps) of 3D scalar fields on a spherical 180x201x360 grid covering 500 Myr
of geological time. Each time step is 2 Myrs, and the fields are:

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
a function of latitude [degrees north], longitude [degrees east], and radius [km]. The model's inner and outer radii are
3485 km and 6371 km, respectively.








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

<!-- Details will be provided at the end of October 2020. -->

The 251 steps are grouped into 25 gzipped tar files `mantle{01..25}.tgz` -- see the table below. To start working on the
project, you can download only `mantle01.tgz`, but for a production-quality animation you will need all 25 files.

<br>

| File   |  Timestep range   |    Size      |  Checksum |
|----------|-------------|------|----------|
| [mantle01.tgz](https://nextcloud.computecanada.ca/index.php/s/edS6be3sk8oQ58N/download) | 001..010 | 3.2GB | 6aa435a58ac9487f48291c363eccde6e |
| [mantle02.tgz](https://nextcloud.computecanada.ca/index.php/s/infBBW2Rc9TJwf7/download) | 011..020 | 3.2GB | dbc46f9cffb665a5bccfc95a4a864079 |
| [mantle03.tgz](https://nextcloud.computecanada.ca/index.php/s/76Esj3yDP9EiaGc/download) | 021..030 | 3.2GB | cffe250d3388bbd317a44eda88ccf0df |
| [mantle04.tgz](https://nextcloud.computecanada.ca/index.php/s/AZmt47d48prCZZF/download) | 031..040 | 3.2GB | 84979f5daf4470eb81b9cbdb0c981fa6 |
| [mantle05.tgz](https://nextcloud.computecanada.ca/index.php/s/9fZ4A7ENGR6sQrc/download) | 041..050 | 3.2GB | 4dce2df4da2a7ef4b5b174b5a49af4d0 |
| [mantle06.tgz](https://nextcloud.computecanada.ca/index.php/s/B8HC3H4oqwcsWB3/download) | 051..060 | 3.2GB | 97bd7e2ae99b49ac1732ced3b20ba77d |
| [mantle07.tgz](https://nextcloud.computecanada.ca/index.php/s/t3zLJWWeirR5zmG/download) | 061..070 | 3.2GB | 5a4fab7180456d99fbb19175a05ea3b1 |
| [mantle08.tgz](https://nextcloud.computecanada.ca/index.php/s/YmkYgxM7xxrNAwj/download) | 071..080 | 3.2GB | 4caaea5992f66e391535e079575e29f6 |
| [mantle09.tgz](https://nextcloud.computecanada.ca/index.php/s/rMma6W9MBtQH9LX/download) | 081..090 | 3.2GB | e282bbd474529a858ddddb627204f88f |
| [mantle10.tgz](https://nextcloud.computecanada.ca/index.php/s/MzcZBCaxaojTZJx/download) | 091..100 | 3.2GB | 1899ecec0756540957f2d18094c39948 |
| [mantle11.tgz](https://nextcloud.computecanada.ca/index.php/s/dfP6NXHmekQQrHR/download) | 101..110 | 3.2GB | daaac28e6989f68bd4bff4117a2645d5 |
| [mantle12.tgz](https://nextcloud.computecanada.ca/index.php/s/2GnLRgPi8W2Dt5p/download) | 111..120 | 3.2GB | e335c9fed2448ca7bfc24a01a78759e6 |
| [mantle13.tgz](https://nextcloud.computecanada.ca/index.php/s/MqtoESg2d9DsF2P/download) | 121..130 | 3.2GB | 01a85d3402c89d964b9158ca6bc6665d |
| [mantle14.tgz](https://nextcloud.computecanada.ca/index.php/s/ysGoJK6B3pLYaDB/download) | 131..140 | 3.2GB | c1195cd3ba48b17874507f5f03ed0dd5 |
| [mantle15.tgz](https://nextcloud.computecanada.ca/index.php/s/Ae32XwCpt7bHo9D/download) | 141..150 | 3.2GB | 8c25f1996c5eaf5ac0a50114170cd436 |
| [mantle16.tgz](https://nextcloud.computecanada.ca/index.php/s/AysWSPnxFS6e5B2/download) | 151..160 | 3.2GB | 5659e592a8dbbc7d6d3f6ebc10a1e3c0 |
| [mantle17.tgz](https://nextcloud.computecanada.ca/index.php/s/4NcnJkPYWpkXrmb/download) | 161..170 | 3.2GB | e59fccb6cabb87e232f30a6c7ce2cbbb |
| [mantle18.tgz](https://nextcloud.computecanada.ca/index.php/s/mBRfrnfEEEaKJ9m/download) | 171..180 | 3.2GB | 38a0007cf2676e64eac91ec9c9f3034c |
| [mantle19.tgz](https://nextcloud.computecanada.ca/index.php/s/J63KxeCppK8ssGc/download) | 181..190 | 3.2GB | 8ee1cf466264303d5822aede27477151 |
| [mantle20.tgz](https://nextcloud.computecanada.ca/index.php/s/NeqnHBNPWx4PRwd/download) | 191..200 | 3.2GB | 9c6163d659ebac7d9d8f72b6592a3994 |
| [mantle21.tgz](https://nextcloud.computecanada.ca/index.php/s/JdzZQCKiHaRfL9L/download) | 201..210 | 3.2GB | fabba593dd5274d98aa9c48d5fea701a |
| [mantle22.tgz](https://nextcloud.computecanada.ca/index.php/s/DXnWtA5fymHBsxA/download) | 211..220 | 3.2GB | 8e4ce089409629c7f5122c1c6f19d6db |
| [mantle23.tgz](https://nextcloud.computecanada.ca/index.php/s/HzgtF42Pf9AnxGm/download) | 221..230 | 3.2GB | a78d3fd385baf8c1ec78eda7b69a2394 |
| [mantle24.tgz](https://nextcloud.computecanada.ca/index.php/s/yy8FASeC8Dm54Sy/download) | 231..240 | 3.2GB | d551765802f1aa9b399763beadf8f44e |
| [mantle25.tgz](https://nextcloud.computecanada.ca/index.php/s/TC8QekmjokmBkWA/download) | 241..251 | 3.5GB | eff0d9d0b62522559a53a4eb11aea579 |

<br>

To download the files in bash command line:

```
urls=( edS6be3sk8oQ58N infBBW2Rc9TJwf7 76Esj3yDP9EiaGc AZmt47d48prCZZF
       9fZ4A7ENGR6sQrc B8HC3H4oqwcsWB3 t3zLJWWeirR5zmG YmkYgxM7xxrNAwj
       rMma6W9MBtQH9LX MzcZBCaxaojTZJx dfP6NXHmekQQrHR 2GnLRgPi8W2Dt5p
       MqtoESg2d9DsF2P ysGoJK6B3pLYaDB Ae32XwCpt7bHo9D AysWSPnxFS6e5B2
       4NcnJkPYWpkXrmb mBRfrnfEEEaKJ9m J63KxeCppK8ssGc NeqnHBNPWx4PRwd
       JdzZQCKiHaRfL9L DXnWtA5fymHBsxA HzgtF42Pf9AnxGm yy8FASeC8Dm54Sy
       TC8QekmjokmBkWA )
for i in $(seq 0 24); do
    wget https://nextcloud.computecanada.ca/index.php/s/"${urls[$i]}"/download -O mantle"$(printf "%02d\n" $((i+1)))".tgz
done
```



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
import netCDF4 as nc
all = nc.Dataset('spherical001.nc', 'r')
print(all)                                   # show all variables inside this dataset
print(all.variables['temperature'][:,:,:])   # this is a 180x201x360 numpy array
print(all.variables['r'][:])                 # radial discretization
~~~

# Acknowledgments

Data courtesy of the Pysklywec Lab (Russell Pysklywec and Hosein Shahnas) at the University of Toronto. The simulation
was conducted using Compute Canada's Niagara cluster.

<!-- Data storage services provided by IT-Data Storage team -->
<!-- at King Abdullah University of Science and Technology (KAUST) in Thuwal, Saudi Arabia. -->
