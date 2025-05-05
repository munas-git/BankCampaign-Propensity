# Context
Term deposits are a key income source for banks, and telephonic marketing remains one of the most effective ways to sell them. However, these campaigns are resource-intensive, involving large call centres. To optimise efficiency, it's crucial to identify customers who are most likely to convert before reaching out. [This dataset](https://www.kaggle.com/datasets/prakharrathi25/banking-dataset-marketing-targets/data) is related to direct telephonic marketing campaigns of a Portuguese bank, with the goal of predicting whether a customer will subscribe to a term deposit (yes/no). ***My own personal objectives are listed below.***

## Objectives
- Evaluate the effectiveness of the past campaign... Past Conversion Rate.
- Understand the nature of factors that actually drive conversion
- Build a propensity model to estimate the likelihood of future conversion for similar campaigns.
- Calibrate the model to better reflect probabilities
- Identify the top percentage of leads expected to convert, without triggering diminishing returns.
- Measure gains and uplift
- Design and recommend data-informed A/B experiments strategies.

> Let's connect! --> [LinkedIn](https://www.linkedin.com/in/einstein-ebereonwu/) | [X](https://x.com/einsteinmuna) | [GitHub.](https://github.com/munas-git)

---

# Process & Findings: Term Deposit Propensity Modelling

This analysis focused on optimising telephonic marketing campaigns for term deposit products by leveraging a robust propensity modelling approach. The goal was to identify high-likelihood conversion targets, thereby increasing campaign efficiency and ROI for the bank which led to the discovery of the fact that `83.54%` of all conversions are captured by just the top ***40.0%*** of leads, and they are `6.01` times more likely to convert than if leads are picked at random.

**Key Findings**

- **Past Campaign Effectiveness**: The historical conversion rate was 11.7%, aligning with industry norms for random targeting in direct marketing.
- **Conversion Drivers**:
    - *Demographics*: Older clients (30–60 years), those in management roles, married, and those with secondary education were more likely to subscribe.
    - *Financial Status*: Higher account balances correlated with higher subscription rates.
    - *Behavioral Factors*:
        - Longer call durations were strongly associated with successful conversions.
        - Fewer campaign contacts (1–3) were optimal; conversion rates dropped with excessive contact attempts.
        - Prior contact is kind of a tricky one, as very recent and not very recent at all, e.g 2-3 and over 100 days ago have positive outcomes. Positive outcomes from previous campaigns (`poutcome`) significantly boosted conversion likelihood as well.
    - *Channel and Timing*: Cellular contact outperformed telephone, and May was the most successful month for subscriptions.
    - *Credit Status*: Clients without existing loans or defaults were more receptive.

**Modeling \& Data Handling**

- Outliers in call duration, campaign contacts, and previous contacts were carefully excluded to prevent skewed modelling.
- Categorical variables were encoded with attention to ordinal relationships (e.g., education, month).
- Data balancing techniques (SMOTE, undersampling) were considered to address class imbalance.
- The initial model was trained with a `train/test/calib` set to understand performance as well as the impact of calibration on score alignment.
- The final model was trained on the previously mentioned `train + test` set, then calibrated using the original calibrated set and sigmoid method to better reflect true conversion likelihoods.


## Recommendations

**1. Targeted Outreach**

- Prioritise segments with high predicted propensity: older, married, highly educated, management-level clients, and those with higher balances.
- Focus on clients with no credit defaults or active loans.

**2. Optimise Campaign Strategy**

- Limit contact attempts to a maximum of 3 per client to avoid diminishing returns and potential customer fatigue.
- Schedule campaigns to peak in May or other high-performing months identified in the analysis.
- Favour cellular over telephone outreach for higher engagement.

**3. Personalise Messaging**

- Tailor scripts and offers for high-propensity segments (e.g., highlight product benefits relevant to management professionals or retirees).
- For clients with prior positive campaign outcomes, reference past interactions to build rapport.

**4. Enhance Data Quality \& Monitoring**

- Regularly review and update customer data to maintain segmentation accuracy.
- Try to find out the education levels and outreach methods of those currently unknown
- Monitor for outliers and update exclusion thresholds as needed to keep the model robust.


## A/B Testing Recommendations

To validate and further optimise these strategies, implement the following A/B tests:


| Test Focus | Group A (Control) | Group B (Test) | Success Metric |
| :-- | :-- | :-- | :-- |
| Contact Channel | Telephone outreach | Cellular outreach | Conversion rate |
| Campaign Timing | Standard months | May (peak month) | Conversion rate |
| Contact Frequency | Up to 6 contacts | Max 3 contacts | Conversion rate, opt-out rate |
| Personalisation | Generic script | Tailored script for high-propensity segments | Conversion rate, call duration |
| Prior Campaign Targeting | All clients | Only clients with prior positive outcomes | Conversion rate |

- **Monitor**: Conversion rates, call durations, and opt-out rates for each test group.
- **Iterate**: Refine targeting and messaging based on statistical significance and observed lift.


## Final Observations

- The propensity model provides actionable insights for resource allocation and campaign design, enabling the bank to focus efforts on clients most likely to convert.
- Regular calibration and monitoring are essential to adapt to changing customer behaviours and market conditions.
- Combining data-driven targeting with thoughtful A/B testing will maximise marketing ROI and customer satisfaction.

**NOTE**: This entire analysis is part of my weekly series in efforts to **demystify applied statistical techniques through real-world, project-driven examples**, making concepts like propensity modelling, causal inference, and evaluation metrics more accessible to practitioners of all backgrounds.
