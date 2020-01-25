ts2sls
======

### Description 

ts2sls.ado v0.2.0

JEFFREY SHRADER

Stata program to calculate two-sample two-stage least squares (TS2SLS) estimates. Math is based on Inoue and Solon (2005), although variable names more closely follow the shorter version published as Inoue and Solon (2010).

If you find errors, please let me know.

#### Syntax

ts2sls y (x = z) [if] [in], group(group_var) [noconstant]

Where y is the outcome variable, x is the endogenous regressor, and z is an exogenous instrument. I follow the notation of Inoue and Solon and call the data for estimating the reduced form (y as a function of z) "group 1" and the data for estimating the first stage (x as a function of z) "group 2".

Your datasets need to be stacked, so if you are estimating from two different datasets, append them, then specify "group" appropriately. The dataset must look like this:
```
  Group  |    Y    |    X    |    Z   
---------+---------+---------+---------
    1    |    y    |    .    |    z_1
    2    |    .    |    x    |    z_2
```

### Installation
You can download ts2sls.ado ([click here](https://github.com/jshrader/ts2sls/archive/master.zip)) and place it where Stata can find ado files. For example, you can put it in the t/ directory of your [personal ado folder](http://www.stata.com/support/faqs/programming/personal-ado-directory/). To find your ado folders, issue the command `sysdir` to Stata. Once you have put the code in one of your ado directories, you should simply be able to run it by typing "ts2sls ..." into Stata.

Once this code is reasonably complete, I can put it into a package.

#### Debugging
People trying to run this command occasionally experience the error "< is not a valid command name". If this error occurs, it means you have downloaded an html page rather than the ts2sls.ado file. If you click [this link](https://github.com/jshrader/ts2sls/archive/master.zip), it will download the correct file. 

### For the future

1. More numerically stable matrix calculations
2. Standard errors are not fully corrected in the case of multiple instruments
3. Perfect collinearity checking is broken
4. Missing values in the dependent variable will throw an error--drop missing LHS observations before running

### References 

Angrist, Joshua D., and Alan B. Krueger. "The effect of age at school entry on educational attainment: an application of instrumental variables with moments from two samples." Journal of the American Statistical Association 87, no. 418 (1992): 328-336.

Inoue, Atsushi, and Gary Solon. "Two-sample instrumental variables estimators." The Review of Economics and Statistics 92, no. 3 (2010): 557-561.

Inoue, Atsushi, and Gary Solon. "Two-Sample Instrumental Variables Estimators." NBER Working Paper (2005).

test change
