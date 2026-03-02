E-Commerce Causal Discount Analysis

Overview
--------
This project evaluates the causal impact of a targeted discount strategy on e-commerce revenue.
While naive comparisons suggest that discounts substantially increase revenue, treatment
assignment is biased toward higher-value customers. Using propensity score modeling and
inverse probability of treatment weighting (IPTW), this analysis corrects for selection bias
and estimates the true incremental revenue effect of the discount.

The project demonstrates a full causal inference workflow from data generation to
stakeholder interpretation.

Business Problem
----------------
Discounts are often deployed to drive conversions and revenue. However, in practice,
discounts are frequently targeted toward higher-value customers. If this targeting is not
accounted for, naive performance comparisons can significantly overstate the true effect
of the pricing strategy.

This analysis answers:
What is the true incremental revenue impact of a discount once selection bias is removed?

Methodology
-----------
1. Simulated Biased Treatment Assignment
   Treatment (discount) was assigned to stronger customers with a higher probability.

2. Naive Treatment Effect Estimation
   Revenue differences were computed without adjustment.

3. Propensity Score Modeling
   Logistic regression estimated the probability of receiving treatment.

4. Inverse Probability of Treatment Weighting (IPTW)
   Observations were reweighted to simulate randomized assignment.

5. Covariate Balance Diagnostics
   Confounder balance was verified before and after weighting.

6. Bootstrap Confidence Intervals
   Resampling was used to estimate uncertainty around the adjusted treatment effect.

Key Results
-----------
Naive ATE: 14.79
IPTW-Adjusted ATE: 6.09
95% Confidence Interval: (5.50, 6.67)

The naive estimate overstated the true effect by more than 100 percent,
highlighting the importance of correcting for selection bias.

Causal Assumptions
------------------
- Unconfoundedness: All relevant confounders are observed.
- Overlap (Positivity): Treated and control groups share overlapping propensity scores.
- Correct Model Specification: The propensity model captures treatment assignment dynamics.

Limitations
-----------
- Simulated dataset
- Potential unobserved confounders in real-world applications
- Dependence on correct model specification

Business Implications
---------------------
Although naive analysis suggests strong revenue gains from discounting,
proper causal adjustment reveals a substantially smaller incremental effect.
Pricing decisions should be based on causal impact rather than raw comparisons.

Technologies Used
-----------------
Python
NumPy
pandas
scikit-learn
Matplotlib
