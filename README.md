# WhiteboxTools Frontends 

[![docs](https://img.shields.io/badge/whitebox-docs-brightgreen.svg)](https://jblindsay.github.io/wbt_book)
[![python](https://img.shields.io/badge/whitebox-Python-blue.svg)](https://github.com/giswqs/whitebox-python)
[![R](https://img.shields.io/badge/whitebox-R-green.svg)](https://github.com/giswqs/whiteboxR)
[![ArcGIS](https://img.shields.io/badge/whitebox-ArcGIS-brightgreen.svg)](https://github.com/giswqs/WhiteboxTools-ArcGIS)
[![QGIS](https://img.shields.io/badge/whitebox-QGIS-orange.svg)](https://jblindsay.github.io/wbt_book/qgis_plugin.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Donate](https://img.shields.io/badge/Donate-Buy%20me%20a%20coffee-yellowgreen.svg)](https://www.buymeacoffee.com/giswqs)

**WhiteboxTools** is an advanced geospatial data analysis platform developed by Prof. John Lindsay ([webpage](https://jblindsay.github.io/ghrg/index.html); [jblindsay](https://github.com/jblindsay)) at the University of Guelph's [Geomorphometry and Hydrogeomatics Research Group](https://jblindsay.github.io/ghrg/index.html). The **[WhiteboxTools](https://github.com/jblindsay/whitebox-tools)** library currently contains **412** tools, which are each grouped based on their main function into one of the following categories: Data Tools, GIS Analysis, Hydrological Analysis, Image Analysis, LiDAR Analysis, Mathematical and Statistical Analysis, Stream Network Analysis, and Terrain Analysis. For a listing of available tools, complete with documentation and usage details, please see the [WhiteboxTools User Manual](https://jblindsay.github.io/wbt_book/available_tools/index.html).

**WhiteboxTools** can be accessed either from a [command prompt](#cmd) (i.e. terminal) or through one of the following front-ends:

* [Python Package](#python)
* [R Package](#r)
* [ArcGIS Python Toolbox](#arcgis)
* [QGIS Plugin](#QGIS)

## Python Package <a class='anchor' id='python'></a>

### Links

* GitHub repo: <https://github.com/giswqs/whitebox-python>
* PyPI: <https://pypi.org/project/whitebox/>
* conda-forge: <https://anaconda.org/conda-forge/whitebox>
* Documentation: <https://whitebox.readthedocs.io>
* Maintainer: [Qiusheng Wu](https://wetlands.io)

### Installation

The **whitebox** Python package can be installed using the following command:

```Python
pip install whitebox
```

The **whitebox** Python package is also available on [conda-forge](https://anaconda.org/conda-forge/whitebox), which can be installed using the following command:

```Python
conda install -c conda-forge whitebox
```

### Usage

Tool names in the whitebox Python package can be called using the snake_case convention (e.g. lidar_info). See below for an example Python script.

```Python
import os
import pkg_resources
import whitebox

wbt = whitebox.WhiteboxTools()
print(wbt.version())
print(wbt.help())

# identify the sample data directory of the package
data_dir = os.path.dirname(pkg_resources.resource_filename("whitebox", 'testdata/'))

wbt.set_working_dir(data_dir)
wbt.verbose = False
wbt.feature_preserving_smoothing("DEM.tif", "smoothed.tif", filter=9)
wbt.breach_depressions("smoothed.tif", "breached.tif")
wbt.d_inf_flow_accumulation("breached.tif", "flow_accum.tif")
```

**WhiteboxTools** also provides a Graphical User Interface (GUI) - **WhiteboxTools Runner**, which can be invoked using the following Python script:

```Python
import whitebox
whitebox.Runner()
```
![whitebox-runner](https://wetlands.io/file/images/whitebox.png)


## R Package <a class='anchor' id='r'></a>

### Links

* GitHub repo: <https://github.com/giswqs/whiteboxR>
* [: <https://[.r-project.org/R/?group_id=2337>
* Documentation: <https://giswqs.github.io/whiteboxR/>
* Maintainer: [Qiusheng Wu](https://wetlands.io)


### Installation

The **whitebox** R package is available on [R-Forge](https://r-forge.r-project.org/R/?group_id=2337), which can be installed using the following command: 

```R
install.packages("whitebox", repos="http://R-Forge.R-project.org")
```

You can alternatively install the development version of whitebox from [GitHub](https://github.com/giswqs/whiteboxR) as follows:

```R
if (!require(devtools)) install.packages('devtools')
devtools::install_github("giswqs/whiteboxR")
```

### Usage

Tool names in the **whitebox** R package can be called using the snake_case (e.g. wbt_lidar_info). See below for an example.

```R
library(whitebox)

# Set input raster DEM file
dem <- system.file("extdata", "DEM.tif", package="whitebox")

# Run tools
wbt_feature_preserving_smoothing(dem, "./smoothed.tif", filter=9, verbose_mode = TRUE)
wbt_breach_depressions("./smoothed.tif", "./breached.tif")
wbt_d_inf_flow_accumulation(dem, "./flow_accum.tif")
```

## ArcGIS Python Toolbox<a class='anchor' id='arcgis'></a>

### Links

* GitHub repo: <https://github.com/giswqs/WhiteboxTools-ArcGIS>
* Maintainer: [Qiusheng Wu](https://wetlands.io)

### Installation

#### Step 1: Download the toolbox

1. Go to the [WhiteboxTools-ArcGIS GitHub repo](https://github.com/giswqs/WhiteboxTools-ArcGIS) and Click the green button (**[Clone or download](https://gishub.org/whitebox-arcgis-download)**) on the upper-right corner of the page to download the toolbox as a zip file.

    ![](https://i.imgur.com/2xQkxCY.png)

2. Depcompress the downloaded zip file.

#### Step 2: Connect to the toolbox

1. Navigate to the **Folder Connections** node in the catalog window tree.

2. Right-click the node and choose **Connect To Folder**.

    ![](https://i.imgur.com/uKK1Yel.png)

3. Type the path or navigate to the **WhiteboxTools-ArcGIS** folder and click **OK**.

4. Browse into the toolbox and start using its tools.

    ![](https://i.imgur.com/JcdNBnt.png)

### Usage

Open any tool within the toolbox and start using it. Check out the [WhiteboxTools User Mannual](https://jblindsay.github.io/wbt_book/) for more detailed help documentation of each tool.

![](https://i.imgur.com/4c9RLZY.png)


### Toolbox Screenshots

![Toolbox-1](https://raw.githubusercontent.com/giswqs/WhiteboxTools-ArcGIS/master/screenshots/Toolbox-1.png)
![Toolbox-2](https://raw.githubusercontent.com/giswqs/WhiteboxTools-ArcGIS/master/screenshots/Toolbox-2.png)
![Toolbox-3](https://raw.githubusercontent.com/giswqs/WhiteboxTools-ArcGIS/master/screenshots/Toolbox-3.png)

## QGIS Plugin <a class='anchor' id='qgis'></a>

### Links

* Documentation: <https://jblindsay.github.io/wbt_book/qgis_plugin.html>
* Maintainer: [Alexander Bruy](https://wiki.osgeo.org/wiki/User:Alexbruy)

### Installation

### Usage

## Command-line Interface <a class='anchor' id='cmd'></a>

### Links

* GitHub repo: <https://github.com/jblindsay/whitebox-tools>
* User Manual: <https://jblindsay.github.io/wbt_book/index.html>
* Maintainer: [John Lindsay](https://jblindsay.github.io/ghrg/index.html)

### Installation

### Usage
