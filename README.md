This analysis focused on optimising telephonic marketing campaigns for term deposit products by leveraging a robust propensity modeling approach. The goal was to identify high-likelihood conversion targets, thereby increasing campaign efficiency and ROI for the bank which led to the discovery of the fact that `83.54%` of all conversions are captured by just the top ***40.0%*** of leads, and they are `6.01` times more likely to convert than if leads are picked at random.

**Key Findings**

- **Past Campaign Effectiveness**: The historical conversion rate was 11.7%, aligning with industry norms for random targeting in direct marketing.
- **Conversion Drivers**:
    - *Demographics*: Older clients (30–60 years), those in management roles, singles, and those with tertiary education were more likely to subscribe.
    - *Financial Status*: Higher account balances correlated with higher subscription rates.
    - *Behavioral Factors*:
        - Longer call durations were strongly associated with successful conversions.
        - Fewer campaign contacts (1–3) were optimal; conversion rates dropped with excessive contact attempts.
        - Recent prior contact (low `pdays`) and positive outcomes from previous campaigns (`poutcome`) significantly boosted conversion likelihood.
    - *Channel and Timing*: Cellular contact outperformed telephone, and May was the most successful month for subscriptions.
    - *Credit Status*: Clients without existing loans or defaults were more receptive.

**Modeling \& Data Handling**

- Outliers in call duration, campaign contacts, and previous contacts were carefully excluded to prevent skewed modeling.
- Categorical variables were encoded with attention to ordinal relationships (e.g., education, month).
- Data balancing techniques (SMOTE, undersampling) were considered to address class imbalance.
- Initial model was trained with a `train/test/calib` set to understand performance as well as impact of calibration on score alignment.
- Final model was trained on the previously mentioned `train + test` set, then calibrated using original calibrated set and sigmoid method to better reflected true conversion likelihoods.


## Recommendations

**1. Targeted Outreach**

- Prioritise segments with high predicted propensity: older, single, highly educated, management-level clients, and those with higher balances.
- Focus on clients with no credit defaults or active loans.

**2. Optimise Campaign Strategy**

- Limit contact attempts to a maximum of 3 per client to avoid diminishing returns and potential customer fatigue.
- Schedule campaigns to peak in May or other high-performing months identified in the analysis.
- Favor cellular over telephone outreach for higher engagement.

**3. Personalise Messaging**

- Tailor scripts and offers for high-propensity segments (e.g., highlight product benefits relevant to management professionals or retirees).
- For clients with prior positive campaign outcomes, reference past interactions to build rapport.

**4. Enhance Data Quality \& Monitoring**

- Regularly review and update customer data to maintain segmentation accuracy.
- Try to find out the education levels an outreach method of those currently unknown
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
- Regular calibration and monitoring are essential to adapt to changing customer behaviors and market conditions.
- Combining data-driven targeting with thoughtful A/B testing will maximise marketing ROI and customer satisfaction.

**NOTE**: This entire analysis is part of my weekly series in efforts to **demystify applied statistical techniques through real-world, project-driven examples**, making concepts like propensity modelling, causal inference, and evaluation metrics more accessible to practitioners of all backgrounds.   

> Let's connect! --> [LinkedIn](https://www.linkedin.com/in/einstein-ebereonwu/) | [X](https://x.com/einsteinmuna) | [GitHub.](https://github.com/munas-git)
