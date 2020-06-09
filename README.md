# WhiteboxTools Frontends

[![docs](https://img.shields.io/badge/whitebox-Docs-brightgreen.svg)](https://jblindsay.github.io/wbt_book)
[![frontends](https://img.shields.io/badge/whitebox-Frontends-yellowgreen.svg)](https://github.com/giswqs/whitebox-frontends)
[![Rust](https://img.shields.io/badge/whitebox-Rust-yellow.svg)](https://github.com/jblindsay/whitebox-tools)
[![python](https://img.shields.io/badge/whitebox-Python-blue.svg)](https://github.com/giswqs/whitebox-python)
[![R](https://img.shields.io/badge/whitebox-R-green.svg)](https://github.com/giswqs/whiteboxR)
[![ArcGIS](https://img.shields.io/badge/whitebox-ArcGIS-brightgreen.svg)](https://github.com/giswqs/WhiteboxTools-ArcGIS)
[![QGIS](https://img.shields.io/badge/whitebox-QGIS-orange.svg)](https://jblindsay.github.io/wbt_book/qgis_plugin.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![image](https://img.shields.io/twitter/follow/giswqs?style=social%20%20%20%20..%20image::%20https://readthedocs.org/projects/geemap/badge/?version=latest)](https://twitter.com/giswqs)

**WhiteboxTools** is an advanced geospatial data analysis platform developed by Prof. [John Lindsay](https://github.com/jblindsay) at the University of Guelph's [Geomorphometry and Hydrogeomatics Research Group](https://jblindsay.github.io/ghrg/index.html). The **[WhiteboxTools](https://github.com/jblindsay/whitebox-tools)** library currently contains **440** tools, which are each grouped based on their main function into one of the following categories: Data Tools, GIS Analysis, Hydrological Analysis, Image Analysis, LiDAR Analysis, Mathematical and Statistical Analysis, Stream Network Analysis, and Terrain Analysis. For a listing of available tools, complete with documentation and usage details, please see the [WhiteboxTools User Manual](https://jblindsay.github.io/wbt_book/available_tools/index.html).

**WhiteboxTools** can be accessed either from a [command prompt](#cmd) (i.e. terminal) or through one of the following front-ends:

- [Python Package](#python)
- [R Package](#r)
- [ArcGIS Python Toolbox](#arcgis)
- [QGIS Plugin](#qgis)
- [Command-line Interface](#cmd)

## Python Package <a class='anchor' id='python'></a>

### Links

- GitHub repo: <https://github.com/giswqs/whitebox-python>
- PyPI: <https://pypi.org/project/whitebox/>
- conda-forge: <https://anaconda.org/conda-forge/whitebox>
- Documentation: <https://whitebox.readthedocs.io>
- Maintainer: [Qiusheng Wu](https://wetlands.io)

### Installation

The **whitebox** Python package can be installed using the following command:

```python
pip install whitebox
```

The **whitebox** Python package is also available on [conda-forge](https://anaconda.org/conda-forge/whitebox), which can be installed using the following command:

```python
conda install -c conda-forge whitebox
```

### Usage

Tool names in the whitebox Python package can be called using the snake_case convention (e.g. lidar_info). See below for an example Python script.

```python
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

```python
import whitebox
whitebox.Runner()
```

![whitebox-runner](https://wetlands.io/file/images/whitebox.png)

## R Package <a class='anchor' id='r'></a>

### Links

- GitHub repo: <https://github.com/giswqs/whiteboxR>
- R-Forge: <https://r-forge.r-project.org/R/?group_id=2337>
- Documentation: <https://giswqs.github.io/whiteboxR/>
- Maintainer: [Qiusheng Wu](https://wetlands.io)

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

### RStudio Screenshot

![whiteboxR](https://wetlands.io/file/images/whiteboxR.png)

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

- GitHub repo: <https://github.com/giswqs/WhiteboxTools-ArcGIS>
- Maintainer: [Qiusheng Wu](https://wetlands.io)

### Installation

#### Step 1: Download the toolbox

1. Go to the [WhiteboxTools-ArcGIS GitHub repo](https://github.com/giswqs/WhiteboxTools-ArcGIS) and click the green button (**[Clone or download](https://gishub.org/whitebox-arcgis-download)**) on the upper-right corner of the page to download the toolbox as a zip file.

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

### ArcGIS Pro Screenshot

![ArcGISPro](https://wetlands.io/file/images/whitebox-ArcGISPro.png)

### ArcMap Screenshots

![Toolbox-1](https://raw.githubusercontent.com/giswqs/WhiteboxTools-ArcGIS/master/screenshots/Toolbox-1.png)
![Toolbox-2](https://raw.githubusercontent.com/giswqs/WhiteboxTools-ArcGIS/master/screenshots/Toolbox-2.png)
![Toolbox-3](https://raw.githubusercontent.com/giswqs/WhiteboxTools-ArcGIS/master/screenshots/Toolbox-3.png)

## QGIS Plugin <a class='anchor' id='qgis'></a>

### Links

- Documentation: <https://jblindsay.github.io/wbt_book/qgis_plugin.html>
- GitHub repo: https://github.com/alexbruy/processing-wbt
- Maintainer: [Alexander Bruy](https://wiki.osgeo.org/wiki/User:Alexbruy)

### Installation

Please follow the installation guide [here](https://jblindsay.github.io/wbt_book/qgis_plugin.html).

### Screenshot

![QGIS](https://wetlands.io/file/images/whitebox-QGIS.png)

## Command-line Interface <a class='anchor' id='cmd'></a>

### Links

- GitHub repo: <https://github.com/jblindsay/whitebox-tools>
- User Manual: <https://jblindsay.github.io/wbt_book/index.html>
- Maintainer: [John Lindsay](https://jblindsay.github.io/ghrg/index.html)

### Installation

You can download a copy of the **WhiteboxTools** executable for your operating system from the [Geomorphometry and Hydrogeomatics Research Group website](https://jblindsay.github.io/ghrg/WhiteboxTools/download.html). Once you've downloaded WhiteboxTools and decompressed (unzipped) the folder, you can open a command prompt and start using it.

### Usage

**WhiteboxTools** is a command-line program and can be run by calling it with appropriate commands and arguments, from a terminal application. The following commands are recognized by the **WhiteboxTools** library:

| Command          | Description                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| --cd, --wd       | Changes the working directory; used in conjunction with --run flag.                              |
| -h, --help       | Prints help information.                                                                         |
| -l, --license    | Prints the whitebox-tools license.                                                               |
| --listtools      | Lists all available tools, with tool descriptions. Keywords may also be used, --listtools slope. |
| -r, --run        | Runs a tool; used in conjunction with --cd flag; -r="LidarInfo".                                 |
| --toolbox        | Prints the toolbox associated with a tool; --toolbox=Slope.                                      |
| --toolhelp       | Prints the help associated with a tool; --toolhelp="LidarInfo".                                  |
| --toolparameters | Prints the parameters (in json form) for a specific tool; --toolparameters=\"LidarInfo\".        |
| -v               | Verbose mode. Without this flag, tool outputs will not be printed.                               |
| --viewcode       | Opens the source code of a tool in a web browser; --viewcode=\"LidarInfo\".                      |
| --version        | Prints the version information.                                                                  |

Generally, the Unix convention is that single-letter arguments (options) use a single hyphen (e.g. -h) while word-arguments (longer, more descriptive argument names) use double hyphen (e.g. --help). The same rule is used for passing arguments to tools as well. Use the _--toolhelp_ argument to print information about a specific tool (e.g. --toolhelp=Clump). Tool names can be specified either using the snake_case or CamelCase convention (e.g. _lidar_info_ or _LidarInfo_).

For examples of how to call functions and run tools from _WhiteboxTools_, see the _whitebox_example.py_ Python script, which itself uses the _whitebox_tools.py_ script as an interface for interacting with the executable file.

In addition to direct command-line and script-based interaction, a very basic user-interface called _WB Runner_ can be used to call the tools within the _WhiteboxTools_ executable file, providing the required tool arguments.

**Example command prompt:**

```
>>./whitebox_tools --wd='/Users/johnlindsay/Documents/data/' --run=DevFromMeanElev
--input='DEM clipped.dep' --output='DEV raster.dep' -v
```

Notice the quotation marks (single or double) used around directories and filenames, and string tool arguments in general. Use the '-v' flag (run in verbose mode) to force the tool print output to the command prompt. Please note that the whitebox_tools executable file must have permission to be executed; on some systems, this may require setting special permissions. The '>>' is shorthand for the command prompt and is not intended to be typed. Also, the above example uses the forward slash character (/), the directory path separator used on unix based systems. On Windows, users should use the back slash character (\\) instead.
