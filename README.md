# Starbucks Analysis

This dataset and analysis was originally used as a take-home assignment provided by Starbucks for
their job candidates. 

## Data
The data for this exercise consists of about 120,000 data points split in a 2:1 ratio among training and test files. In the experiment simulated by the data, an advertising promotion was tested to see if it would bring more customers to purchase a specific product priced at $10. Since it costs the company 0.15 to send out each promotion, it would be best to limit that promotion only to those that are most receptive to the promotion. Each data point includes one column indicating whether or not an individual was sent a promotion for the product, and one column indicating whether or not that individual eventually purchased that product. Each individual also has seven additional features associated with them, which are provided abstractly as V1-V7.

## Task
The task is to use the training data to understand what patterns in V1-V7 to indicate that a promotion should be provided to a user. Specifically, the goal is to maximize the following two metrics:
-  Incremental Response Rate (IRR), which is the difference between a ratio of the number of purchasers in the treatment group and a ratio of the number of purchasers in the control group.
- Net Incremental Revenue, which is the revenue made or lost by sending out the promotion

Essentially, to maximize both of these metrics, we want to send users the treatment (promotion) only if they
would not have purchased otherwise.

## Installations
The libraries I used in this analysis are pandas, seaborn, and numpy. 

## Motivation
This optional portfolio exercise was included as part of the Udacity Data Scientist Nanodegree.

## File descriptions
This directory contains the data files, a test_results.py script to test the promotion strategy,
and the Jupyter notebook with the analysis.

## Summary of results
In the first iteration of this analysis, the approach I adopted was to compare:
- Purchasers vs. non-purchasers in the control group
- Purchasers vs. non-purchasers in the treatment group

Using boxplots for each variable, V1-V7, I was able to see the difference between characteristics of
purchasers and non-purchasers in the control and treatment group. Then, for the promotion strategy,
the simple approach is to use information obtained from only the second comparison, purchasers vs. 
non-purchasers in the treatment group. By strategically selecting thresholds for each variable, we attempt to minimize promotions sent to the users that would not buy. 

With this method, I was able to obtain an IRR/NIR of 0.0216 / 332.20, which exceeded the test solution of 0.0188 / 189.45.

A possible improvement on this method may be trying to identify out of the purchasers in the treatment group, which ones would have purchased without the treatment. This is a more difficult task, as it requires somehow trying to classify users in the purchase/treatment group into two separate sub-groups: those that would purchase without the promotion, and those that purchased only because of the promotion. If there is too much overlap in the two distributions, such a classification may not be easily obtainable. 

## Authors
The author of the analysis in the notebook is me -- notebook boilerplate text is provided by Udacity, and the test_results.py script is also provided by Udacity.

## Acknowledgements
Thanks to Udacity and Starbucks for providing this exercise as part of the Udacity Data Scientist Nanodegree.
