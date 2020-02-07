
## Workshop Machine Learning in R, 2020

by Katrien Antonio, Jonas Crevecoeur and Roel Henckaerts

Course materials for the *Machine Learning in R* course in February 2020
in The Hague.

📆 February 11, 12 and 13, 2020 <br> 🕧 From 9.30 am to 4.30 pm <br> 📌
Nationale Nederlanden, The Hague

Course materials will be posted in the week before the workshop.

## Overview

<p text-align="justify">

This three-day workshop introduces the *essential concepts of building
machine learning models with R*. Throughout the workshop you will gain
insights in the foundations of machine learning methods, including
*resampling methods*, *data preprocessing steps* and the *tuning of
parameters*. You will cover a variety of *statistical and machine
learning methods*, ranging from GLMs, over tree-based machine learning
methods to neural networks. You will acquire insights in the foundations
of these methods, learn how to set-up the model building process, and
focus on building a good understanding of the resulting model output and
predictions.

</p>

<p align="justify">

Leaving this workshop, you should have a firm grasp of the working
principles of a variety of machine learning methods and be able to
explore their use in practical settings. Moreover, you should have
acquired the fundamental insights to explore some other methods on your
own.

</p>

## Schedule

The detailed schedule follows in the week before the workshop.

| Session | Duration | Description | Material |
| :-----: | -------- | ----------- | -------- |
|  Day 1  | 6 hours  | …           | …        |
|  Day 2  | 6 hours  | …           | …        |
|  Day 3  | 6 hours  | …           | …        |

##### Day 1: Machine learning foundations, regression methods

Topics include:

  - statistical and machine learning: a tour
  - machine learning foundations, including resampling with `caret` and
    `rsample`
  - feature pre-processing steps, including setting up a blue-print with
    `recipes`
  - regression models, including regularization: `lm()`, `glm()`,
    `mgcv()`, `glmnet()`

##### Day 2: Tree-based machine learning methods

Topics include:

  - decision trees
  - ensembles of trees (bagging, random forests, gradient boosting
    machine, XGboost)
  - ML interpretability tools (variable importance, PDP, ICE, and more)
  - H2O

##### Day 3: Deep learning methods

Topics include:

  - neural network infrastructure, calibration steps and tuning of
    (hyper)parameters
  - building deep learning models with TensorFlow and Keras via the
    `keras` library in R
  - a variety of deep learning algorithms (e.g. CNNs and ANNs)
  - putting it all together: case studies
  - wrap up.

## Prework

<p align="justify">

The workshop requires a basic understanding of R. A good starting level
is the material covered in the
[1-Basic](https://github.com/katrienantonio/workshop-R/tree/master/1%20-%20Basic%20R)
folder of the [Programming in
R](https://github.com/katrienantonio/workshop-R) workshop taught at
Nationale Nederlanden in June 2019. From time to time you will also rely
on concepts taught in the
[2-Advanced](https://github.com/katrienantonio/workshop-R/tree/master/2%20-%20Advanced%20R)
folder of the same workshop, including `purrr` and some data handling
and visualisation tools. This workshop will provide some review of these
topics.

</p>

Familiarity with statistical or machine learning methods is *not*
required. The workshop gradually builds up these concepts, with an
emphasis on hands-on demonstrations and exercises.

## Software Requirements

Please bring a laptop with a recent version of R and RStudio installed.
Make sure you can connect your laptop to the internet (or download the
course material one day before the start of the workshop. You will need:

  - R (at least 3.5.2 <https://cloud.r-project.org/bin/windows/base/> )
  - RStudio (
    <https://www.rstudio.com/products/rstudio/download/#download> )

You will now go through three steps: (1) installing packages, (2)
installing h2o interface and (3) installing keras interface. The
instructions are also stored as an R script in the
[scripts](https://github.com/katrienantonio/workshop-ML/tree/master/scripts)
folder.

**Step 1**: run the following script in your R session to install the
required packages

``` r
packages <- c("tidyverse", "here", "gridExtra", "AmesHousing", "caret", "rsample", "broom", "recipes", "mgcv", "glmnet", "evtree", "classInt", "rgdal", "RColorBrewer", "ggmap", "grid", "rpart", "rpart.plot", "rpart.utils", "vip", "pdp", "ipred", "ranger", "gbm", "xgboost", "gganimate", "transformr", "zeallot", "sp", "tmap", "partykit", "rattle", "sf", "leaflet", "rstudioapi")
new_packages <- packages[!(packages %in% installed.packages()[,"Package"])]
if(length(new_packages)) install.packages(new_packages)

# from github, requires Rtools and devtools
install.packages(c("Rtools", "devtools")) 
devtools::install_github("henckr/distRforest")
library(distRforest) # from https://github.com/henckr/distRforest

all_packages <- c("ggplot2", "dplyr", "tidyr", "purrr", "readr", "tibble", "lubridate", "here", "gridExtra", "AmesHousing", "caret", "rsample", "broom", "recipes", "mgcv", "glmnet", "evtree", "classInt", "rgdal", "RColorBrewer", "ggmap", "grid", "rpart", "RColorBrewer", "ggmap", "grid", "gridExtra", "rpart", "rpart.plot", "rpart.utils", "vip", "pdp", "ipred", "ranger", "gbm", "xgboost", "gganimate", "transformr", "zeallot", "sp", "tmap", "partykit", "rattle", "sf", "leaflet", "devtools", "Rtools", "rstudioapi", "distRforest")

if(sum(!(all_packages %in% installed.packages()[, "Package"]))) {
  stop(paste('The following required packages are not installed:\n', 
          paste(all_packages[which(!(all_packages %in% installed.packages()[, "Package"]))], collapse = ', ')));
} else {
  message("Everything is set up correctly. Now go to the next steps (h2o and keras).")
}
```

**Step 2**: on **Day 2** you will explore the R interface for the ‘H2O’
Scalable Machine Learning Platform. We recommend the following
installation instructions, see
<http://h2o-release.s3.amazonaws.com/h2o/rel-yu/1/index.html>

``` r
# The following two commands remove any previously installed H2O packages for R.
if ("package:h2o" %in% search()) { detach("package:h2o", unload=TRUE) }
if ("h2o" %in% rownames(installed.packages())) { remove.packages("h2o") }

# Next, we download packages that H2O depends on.
pkgs <- c("RCurl","jsonlite")
for (pkg in pkgs) {
  if (! (pkg %in% rownames(installed.packages()))) { install.packages(pkg) }
}

# Now we download, install and initialize the H2O package for R.
install.packages("h2o", type="source", repos="http://h2o-release.s3.amazonaws.com/h2o/rel-yu/1/R")
```

Alternatively, you just do

``` r
install.packages("h2o")
library(h2o)
```

**Step 3**: on **Day 3** you will be working with the R interface to
`keras`.

Installing keras requires a working version of Anaconda. To install
Anaconda:

  - download Anaconda at
    <https://www.anaconda.com/distribution/#download-section>, select
    the version for Python 3.7 and make sure to pick the right operating
    system (top of the page: select Windows, macOS or Linux)

  - install Anaconda. This is straightforward after launching the
    installer, but (in case you are in doubt) some instructions are at
    <https://docs.anaconda.com/anaconda/install/windows/>

For installing keras, we recommend the installation instructions on
<https://keras.rstudio.com/>.

``` r
# install.packages("devtools")
devtools::install_github("rstudio/keras")
library(keras)
install_keras()
```

If the above instructions to get `keras` do **not** work, you can
**alternatively** proceed as follows

  - open an Anaconda Prompt (or terminal for macOS) (e.g. via Start in
    Windows and search for Anaconda Prompt) and install keras and
    tensorflow with the following instructions

<!-- end list -->

``` python
pip install keras 
pip install tensorflow
```

  - install `keras` in R and load the library

<!-- end list -->

``` r
install.packages("devtools")
devtools::install_github("rstudio/keras")
library(keras)
```

## Course material

Lecture sheets will become available a week before the workshop (in pdf
and HTML format). R scripts, notebooks and the data sets used throughout
the course will be at your disposal.

## Instructors

<img src="img/Katrien.jpg" width="120"/>

<p align="justify">

[Katrien Antonio](https://katrienantonio.github.io/) is professor in
insurance data science at KU Leuven and associate professor at
University of Amsterdam. She teaches courses on data science for
insurance, life and non-life insurance mathematics and loss models.
Research-wise Katrien puts focus on pricing, reserving and fraud
analytics, as well as mortality dynamics. Katrien will teach Day 1 of
the workshop, and serve as TA on Day 2 and 3.

</p>

<p align="justify">

*Jonas Crevecoeur* is PhD student in insurance data science at KU
Leuven. Jonas will teach Day 3 of the workshop. He holds the degrees of
MSc in Mathematics, MSc in Insurance Studies and MSc in Financial and
Actuarial Engineering (KU Leuven). Before starting the PhD program he
worked as an intern with QBE Re (Belgium office) where he studied
multiline products and copulas. Jonas is PhD fellow of the Research
Foundation - Flanders (FWO, PhD fellowship fundamental research).

</p>

<p align="justify">

*Roel Henckaerts* is PhD student in insurance data science at KU Leuven.
Roel will teach Day 2 of the workshop. Roel holds the degrees of MSc in
Mathematical Engineering, MSc in Insurance Studies and Financial and
Actuarial Engineering (KU Leuven). Before starting the PhD program he
worked as an intern with AIG (London office) and KBC. Roel is PhD fellow
of the Research Foundation - Flanders (FWO, PhD fellowship strategic
basic research).

</p>

Happy learning\!

-----
