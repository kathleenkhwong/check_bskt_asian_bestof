# How to run `check_bskt_asian_bestof` 

The author of this code is Wanqi Li (wanqi@outlook.com). This code is written to test ADMAT 2.0 and MADO on finding gradients for basket options, Asian options, and best of Asian options. In order to run it, you will need jacobianst.m, mado_r_mc_option_price_by_path.m, and MATLAB 2016b or later. The AD compiler can be accessed with online mado-editor at http://129.97.84.51:8080/editor-uw.html. This
address must be accessed from UW campus network or VPN. Due to limited resource, the online editor not
always available. Wanqi Li will try to keep it accessible during weekdays.

This user manual assumes a basic understanding of automatic differentiation. Introduction to automatic differentiation can be found in the following book.

Coleman, T. F., & Xu, W. (2016). Automatic Differentiation in MATLAB using ADMAT with Applications. Society for industrial and applied mathematics.

To gain more insights for MADO, please reference the following:

Go to http://mado-editor.net/ and follow the 2D rotation example at https://github.com/vanchi7/mado-editor#generate-derivative-code
 
# Table of Contents

## A. Time Ratio Only (Experiment 3 in the essay)

### 1. Test cases for 1000 or less assets

* Initialize parameters

* Sample outputs/test cases
  
### 2. Test cases for 1000 or more assets

* Initialize parameters

* Sample outputs/test cases

## B. Memory Usage (Experiment 2 in the essay)
  
# Instructions

## A. Experiment 3 (Time Ratio Only)

### 1. Test cases for 1000 or less assets

#### Step 1. Initialize Parameters

The setup of this code allows multiple inputs and outputs at the same time. 

![inputs](https://user-images.githubusercontent.com/31410379/29929135-b20e3438-8e38-11e7-8377-c81dade4c8f6.PNG)

`num_of_instances` represents total Monte Carlo instances

`num_of_batches` represents number of batches. Note that MADO is insensitive to `num_of_batches'.  MADO only runs path-by-path.

`opt_types` represents type of options, i.e. basket options, Asian options, and best of Asian options. Inputs should look like the example shown in the figure above. Example: opt_types = {`bskt`, `asian`, `bestof`} will output results for all three options. 

`num_of_assets` represents number of assets. You can supply multiple number of assets, i.e. `num_of_assets` = [10 100 500].

#### Step 2. Sample outputs/test cases

Since we have supply three inputs for `num_of_assets` in this example. We will have three sample outputs.

In the printed result: 

Method `mado` is the MADO reverse mode and `admat` is the ADMAT 2.0 reverse mode.

`type` is the type of option.

`primary` is the running time of the user code.

`deriv.` is the running time of the derivative code.

`ratio` is the ratio of the above quantitties.

`diff. d` is the difference between the derivative produced by MADO/ADMAT and the exact solution.

This example shows the results for 100 Monte Carlo instances with 100 batches.

Below shows the sample outputs for all three options with 10 assets.

![output10](https://user-images.githubusercontent.com/31410379/29929137-b21136ba-8e38-11e7-9e15-ecc1322afb03.PNG)

---

Below shows the sample output for all three options with 100 assets.

![output100](https://user-images.githubusercontent.com/31410379/29929138-b21604d8-8e38-11e7-9229-8d1cc31ba53e.PNG)

---

Below shows the sample output for all three options with 500 assets.

![output500](https://user-images.githubusercontent.com/31410379/29929133-b200f99e-8e38-11e7-8311-3ab9222b8d97.PNG)

---

## 2. Test cases for 1000 or more assets

### Step 1. Initialize Parameters

Basically this step is the same as Step 1 in the previous section. Since the testing machine is out of memory for Asian options with 1000 assets or more, it is easier to run just basket options and best of Asian options only for 1000 or more assets.

For example:

`opt_types` represents type of options, i.e. basket options, Asian options, and best of Asian options. Inputs should look like the example shown in the figure below. Example: opt_types = {`bskt`, `bestof`} will output results for only these two options. 

`num_of_assets` represents number of assets. You can supply multiple number of assets, i.e. `num_of_assets` = [1000 2000 3000].

![inputs_1000assetsplus](https://user-images.githubusercontent.com/31410379/29929136-b210c842-8e38-11e7-96f2-b1f4eb9035eb.PNG)

### Step 2. Sample outputs/test cases

This example shows the results for 100 Monte Carlo instances with 100 batches.

Below shows the sample outputs for basket options and best of Asian options with 1000 assets.

![output1000](https://user-images.githubusercontent.com/31410379/29931903-ab7bd91a-8e40-11e7-8814-8b2e679a52fb.PNG)

---

Below shows the sample outputs for basket options and best of Asian options with 2000 assets.

![output2000](https://user-images.githubusercontent.com/31410379/29931902-ab7665b6-8e40-11e7-8c63-2f053dfddd26.PNG)

---

Below shows the sample outputs for basket options and best of Asian options with 3000 assets.

![output3000](https://user-images.githubusercontent.com/31410379/29931901-ab69cfb8-8e40-11e7-9f2e-af135e6464d0.PNG)

