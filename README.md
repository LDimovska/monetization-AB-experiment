# **Monetization Experimentation Plan**

This case study covers a leading European dating platform operating on a freemium model across web and mobile, with combined monthly active users in the high six figures. Before designing experiments, a funnel-value audit was conducted to identify where revenue is leaking.

The research identified two compounding problems:

| **Problem**                                                                                                                                 | **Implication**                                                                     |
| :------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------- |
| Users are blocked too early. Free experience is too restricted, preventing activation and the aha moment that leads to subscription intent. | Users never reach the point of wanting to pay. Conversion fails before the paywall. |
| Premium may not deliver enough incremental value. Paying users still cannot message enough people or generate enough matches.               | Retention fails. The product asks for money before it has earned trust.             |

Experimentation priority: Subscriptions first (primary revenue stream, highest impact if fixed), Ads second (secondary stream, scoped to one experiment), Paywall third (diagnosis and redesign).

# **Part 1: Experimentation Plan**

## **Area A: Subscription Pricing**

### **Experiment 1A - 3-Day Free Trial at Profile Completion Milestone**

|  | |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hypothesis**          | If we offer a 3-day free trial to new users who have completed more than 44% of their profile, then trial activation rate will increase because users will experience premium value at the moment they are most invested in the platform, before trust erodes, measured by the % of eligible users who activate the trial within 48 hours of the offer being shown. |
| **Target segment**      | New users who have completed more than 44% of their profile. The 44% threshold represents completion of core profile categories: self-description, profile details, interest confessions, roles & archetypes, hard & soft limits, main photo, and at least one additional category. This targets users who have demonstrated genuine intent.                   |
| **Control vs. Variant** | Control: current experience with no trial offer. Variant: 3-day free trial offered at the 44% profile completion milestone.  |
| **Split**               | 50/50 random split of all eligible new users. |
| **Duration**            | 2 to 4 weeks minimum, extended until 95% statistical significance is reached.  |
| **Primary metric**      | Trial activation rate - % of eligible users who activate the trial within 48 hours of the offer being shown. |
| **Guardrail metrics**   | 1\. Profile completion rate - detects users gaming the milestone without genuine intent. 2. Subscription conversion rate post-trial - detects trial activation that does not translate to revenue.  |

### **Success Criteria**

| | |
| ------------------------------ | --------------------------------------------------------------------------- |
| **Trial activation rate**      | Greater than or equal to 20% of eligible users activate the trial.          |
| **Post-trial conversion rate** | Greater than or equal to 20% of trial users convert to a paid subscription. |
| **Confidence level**           | 95% statistical significance on both metrics.                               |

### **Risk Assessment**

| | |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Risk 1: Milestone gaming**         | Users complete profile categories superficially just to unlock the trial without genuine intent. Detection: monitor profile completion rate spike in the variant group within the first week. Mitigation: add a secondary condition - user must have at least one mutual match before the trial is offered. |
| **Risk 2: Trial without conversion** | Users activate the trial but never pay, meaning revenue does not grow. Detection: monitor post-trial conversion rate daily from day 4 onward. Mitigation: set a kill switch threshold - if post-trial conversion drops below 10% in week 1, pause the experiment and investigate before full rollout.       |

### **Decision Framework**

| **Scenario**                                                         | **Next action**  |
| :------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Clearly successful <br />(activation ≥20%, post-trial conversion ≥20%)** | Roll out to all new users at the 44%+ milestone. Next experiment: test trial length - does 7 days outperform 3 days? Begin Experiment 1B on match quality post-subscription.  |
| **Clearly unsuccessful <br />(activation <20%)**                           | The milestone trigger or offer presentation did not resonate. Move the trigger to the first paywall hit instead of profile completion. Re-examine whether 44% is too high a threshold.   |
| **Inconclusive <br />(high activation, low post-trial conversion)**        | Offer mechanics work but product experience during the trial is insufficient. Users are not getting enough value in 3 days to justify paying. Next experiment: extend trial to 7 days OR introduce a guided onboarding sequence during the trial designed to drive users toward their first meaningful match interaction. |

## **Area B: Ads Inside the Platform**

Ads are scoped to a single experiment because they represent a secondary revenue stream with a ceiling. The platform's core monetization engine is subscriptions. Over-optimizing ad revenue risks accelerating churn from the primary stream. The priority is therefore to reduce ad disruption enough to protect subscription conversion - not to maximize ad revenue independently.

### **Experiment 1B - Remove Sound-On Ads for Free Users**

| | |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Hypothesis**          | If we remove sound-on ads for free users, then D7 retention will increase because users will no longer experience involuntary audio disruption that causes them to exit the app, measured by the % of free users still active on day 7 in the variant vs. control group. |
| **Target segment**      | All free users, regardless of tenure. Sound-on ads affect the entire free user base and the disruption is not tenure-specific.   |
| **Control vs. Variant** | Control: current experience with sound-on ads. Variant: sound-on ads replaced with silent ad formats at equivalent frequency.   |
| **Split**               | 50/50 random split of all free users.  |
| **Duration**            | 2 to 4 weeks minimum, extended until 95% statistical significance is reached.  |
| **Primary metric**      | D7 retention - % of free users still active on day 7.  |
| **Guardrail metrics**   | 1\. Subscription conversion rate of free users - detects if the improved free experience cannibalizes upgrade intent (subscription signal). 2. Ad revenue per free user - detects if replacing sound-on ads with silent formats causes a significant CPM drop.           |

### **Success Criteria**

| | |
| -------------------------------- | ------------------------------------------------------------------- |
| **D7 retention**                 | Greater than or equal to 15% relative lift vs. control.              |
| **Subscription conversion rate** | Stable or increasing vs. control - must not drop.                    |
| **Ad revenue per free user**     | No significant decrease vs. control (less than 10% drop acceptable). |
| **Confidence level**             | 95% statistical significance.                                        |

### **Risk Assessment**

| | |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Risk 1: Cannibalization of subscription intent** | Removing the most irritating ad format makes the free experience too comfortable, reducing motivation to subscribe. Detection: monitor subscription conversion rate of free users weekly. Mitigation: kill switch if subscription conversion drops more than 10% vs. control.                             |
| **Risk 2: Ad revenue drop**                        | Sound-on ads typically command higher CPMs than silent formats. Replacing them may reduce ad revenue even if impressions remain constant. Detection: monitor CPM and ad revenue per user daily from day 1. Mitigation: quantify the revenue gap and assess whether subscription revenue gains compensate. |

### **Decision Framework**

| **Scenario**                                                               | **Next action**                                                                                                                                                                                    |
| :-------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Clearly successful <br />(D7 retention ≥15%, subscription conversion stable)** | Roll out to all free users. Monitor for 30 days. Next experiment: test session-based frequency cap to further reduce ad pressure.  |
| **Clearly unsuccessful <br />(D7 retention flat)**                               | Sound-on ads are not the primary churn driver. Test a session-based frequency cap next - limit total ads per session regardless of format. |
| **Inconclusive <br />(D7 retention up, subscription conversion down)**           | Free experience became too comfortable. Re-introduce friction elsewhere - for example, a daily match cap for free users - to maintain upgrade motivation while keeping the improved ad experience. |

# **Part 2: Paywall Diagnosis, Redesign & Prototype**

## **Step 1: Diagnose the Conversion Gap**

The paywall selected is the platform's subscription paywall featuring a scrollable feature carousel with 8 screens, three pricing tiers (1 month, 6 months, 12 months), and a Subscribe to continue CTA.

### **Key Metrics to Track**

| **Metric**               | **What it reveals**                                |
| :----------------------- | :------------------------------------------------- |
| Paywall impression rate  | How many users reach the paywall screen            |
| Carousel completion rate | % of users who swipe through all 8 feature screens |
| Time spent on paywall    | Are users reading or bouncing immediately          |
| Plan selection rate      | Which tier users tap before dropping off           |
| CTA click-through rate   | % who tap Subscribe to continue                    |
| Paywall conversion rate  | % who complete payment                             |
| Paywall bounce rate      | % who close the paywall without interacting        |

### **Key Metric Selected: Carousel Completion Rate**

Carousel completion rate is the highest-impact diagnostic metric because the paywall communicates value through 8 sequential feature screens. If users are not completing the carousel, they are making a payment decision based on incomplete information. This metric is the necessary precondition for conversion - you cannot convert on value you never saw. If completion is low, no amount of pricing optimization will fix conversion. If completion is high but conversion is still low, the problem lies in the content or pricing - a distinct and addressable finding.

## **Step 2: Design the Experiment**

### **Experiment 2 - Reorder Feature Carousel**

| | |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hypothesis**          | If we reorder the paywall feature carousel to lead with messaging (Make the first move), social visibility (Unmask your fans), and ad-free experience (No ads, just fun) - the three features most directly tied to user complaints - then carousel completion rate will increase because users encounter relevant value earlier and are less likely to abandon before seeing the full proposition, measured by the % of paywall visitors who reach screen 8 in the variant vs. control. |
| **Target segment**      | All free users who reach the paywall, including both new and returning users. Note: results will be segmented by new vs. returning users from day 1 to detect returning user bias. |
| **Control vs. Variant** | Control: current carousel order (passive matching feature first). Variant: reordered carousel - 1. Make the first move, 2. Unmask your fans, 3. No ads just fun, 4. Passive matching feature, 5. Advanced filters, 6. Privacy controls, 7. Profile boost, 8. Enhanced messaging. |
| **Split**               | 50/50 random split of all free users who reach the paywall.   |
| **Duration**            | 2 to 4 weeks minimum, extended until 95% statistical significance is reached. |
| **Primary metric**      | Carousel completion rate - % of paywall visitors who reach screen 8. |
| **Guardrail metrics**   | 1\. Paywall conversion rate - ensures carousel completion translates to real subscriptions, not just UI engagement. 2. Paywall bounce rate - detects if reordering backfired and users are closing the paywall faster.  |

### **Success Criteria**

| | |
| ---------------------------- | ------------------------------------------------------------------------------------- |
| **Carousel completion rate** | Greater than or equal to 20% relative lift vs. control at 95% statistical confidence. |
| **Paywall conversion rate**  | Greater than or equal to 10% relative lift vs. control at 95% statistical confidence. |
| **Paywall bounce rate**      | No significant increase vs. control.                                                  |

### **Risk Assessment**

| | |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Risk 1: Completion up, conversion flat** | Users swipe through all 8 screens but still do not subscribe. This indicates the feature order was not the conversion blocker - content quality, pricing, or trust is the real issue. Detection: monitor conversion rate from day 7 onward. If completion lifts by week 1 but conversion is flat, set a decision trigger at day 14. Add a user exit survey on paywall close asking what stopped them from subscribing. |
| **Risk 2: Returning user bias**            | Users who have already seen the paywall multiple times are split across both groups. Their behavior is shaped by familiarity rather than feature order, contaminating results. Detection: segment results by new vs. returning users from day 1. Mitigation: report results separately for both segments so the signal is interpretable.  |

### **Decision Framework**

| Scenario                          | Next action  |
| :-------------------------------- | :----------- |
| **Clearly successful <br />(completion ≥20%, conversion ≥10%)**   | Roll out reordered carousel to all free users. Next experiment: reduce carousel from 8 to 3 to 4 screens featuring only the highest-performing features, testing whether a more focused value proposition maintains or improves conversion with less cognitive load.  |
| **Clearly unsuccessful <br />(completion flat, conversion flat)** | Feature order is not the conversion blocker. The problem likely sits in pricing structure, lack of trust signals, or missing social proof. Next experiment: test adding a free trial CTA or social proof element directly on the paywall.  |
| **Inconclusive <br />(completion up, conversion flat)**           | Users are seeing the features but not finding them compelling enough to pay without experiencing them first. The value proposition exists but is not believable at face value. This finding connects directly to Experiment 1A: introduce a 3-day free trial offer on the paywall itself, allowing users to experience the features before committing. |

## **Step 3: Redesign & Prototype**

The redesigned paywall introduces five targeted changes, each grounded in user research and the conversion gap diagnosis. Every other element - pricing tiers, badges, disclaimer, footer links - remains identical to the control to ensure clean variable isolation in testing.

### **Change 1: Reorder Feature Carousel**

| | |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Description**    | Reorder the paywall feature carousel to lead with the three features most directly tied to user complaints: messaging (Make the first move), social visibility (Unmask your fans), and ad-free experience (No ads, just fun). Remaining features follow in order of secondary relevance. |
| **Hypothesis**     | If we reorder the carousel to lead with messaging, fans, and no-ads screens, then carousel completion rate will increase because users encounter relevant value earlier and are less likely to abandon before seeing the full proposition. |
| **Success metric** | Carousel completion rate greater than or equal to 20% relative lift vs. control at 95% statistical confidence.  |
| **Main risk**      | Completion increases but conversion stays flat - indicating feature content, not order, is the real conversion blocker. |
| **Priority**       | High. Directly addresses the diagnosed conversion gap with minimal engineering effort. No pricing or infrastructure changes required. |

### **Change 2: Feature Bundling Test**

| | |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Description**    | Replace the three standalone pricing tiers with two feature bundles at the same \$18.49 price point: Bundle A - Unlimited Messages + No Ads vs. Bundle B - Unlimited Messages + See Fans. Track which bundle drives higher lifetime value and plan selection intent. |
| **Hypothesis**     | If we reframe pricing tiers as feature bundles, then subscription conversion rate will increase because users will evaluate the perceived value of specific features rather than abstract plan duration, making the decision feel more concrete and worthwhile.      |
| **Success metric** | Subscription conversion rate greater than or equal to 15% relative lift vs. control. LTV of converting users greater than or equal to 10% higher than current baseline at 95% statistical confidence. |
| **Main risk**      | Bundling creates confusion - users expect all features to be unlocked with premium, not a subset, which may lead to higher post-subscription churn and negative reviews.  |
| **Priority**       | High. Directly tests whether feature clarity drives conversion better than price-duration framing, with significant potential ARPU impact. |

### **Change 3: CTA Copy - Free Trial**

| | |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Description**    | Replace the current CTA button copy Subscribe to continue with Start my free 3 days - explicitly surfacing the free trial offer at the moment of decision rather than presenting subscription as an immediate financial commitment. |
| **Hypothesis**     | If we change the CTA copy to Start my free 3 days, then CTA click-through rate will increase because users perceive lower commitment risk at the moment of decision, making the first step feel like a trial rather than a payment. |
| **Success metric** | CTA click-through rate greater than or equal to 20% relative lift. Post-trial subscription conversion rate greater than or equal to 20% at 95% statistical confidence.                                                              |
| **Main risk**      | Higher CTA clicks but lower post-trial conversion - users treat the trial as a free pass with no intent to pay, increasing trial costs without revenue return.                                                                   |
| **Priority**       | High. Lowest engineering effort of all five changes with potentially the highest immediate impact on click-through rate.                                                                                                            |

### **Change 4: Social Proof**

| | |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Description**    | Add a member count trust signal below the logo at the top of the paywall: Join 2M+ members already on the platform. This surfaces platform scale before pricing is shown, addressing the trust deficit identified in user research.          |
| **Hypothesis**     | If we add a social proof signal at the top of the paywall, then paywall conversion rate will increase because users who distrust the value exchange will be reassured by platform scale and community size before making a payment decision. |
| **Success metric** | Paywall conversion rate greater than or equal to 10% relative lift vs. control at 95% statistical confidence.   |
| **Main risk**      | The member count feels generic or unbelievable to users already familiar with the platform, making it ineffective or potentially reducing trust if the number seems inflated.  |
| **Priority**       | Medium. Strong supporting signal for trust-building but dependent on messaging credibility and accurate member data.                                                                                                                         |

### **Change 5: Urgency Banner with Information Hierarchy Adjustment**

| | |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Description**    | Add a countdown urgency banner above the CTA: Free trial offer ends in 23:47. Simultaneously, reorder the paywall bottom section to optimize information hierarchy: (1) urgency banner, (2) CTA button, (3) auto-renewal disclaimer, (4) footer links. The disclaimer All subscriptions are auto-renewable. Cancel anytime is moved below the CTA rather than removed - it serves as a post-decision trust signal for users who have already chosen to click, while no longer interrupting the urgency-to-action flow. |
| **Hypothesis**     | If we add a countdown urgency banner above the CTA and reorder the bottom section to place the disclaimer below the button, then CTA click-through rate will increase because time pressure reduces decision paralysis at the moment of highest intent, while the disclaimer continues to provide post-click reassurance without diluting urgency.  |
| **Success metric** | CTA click-through rate greater than or equal to 15% relative lift vs. control at 95% statistical confidence.  |
| **Main risk**      | Users perceive the countdown as a dark pattern, reducing trust and increasing paywall dismissal rate - particularly relevant for a platform where user trust is already fragile. Guardrail: monitor paywall bounce rate daily.  |
| **Priority**       | Medium. High potential impact on click-through rate but carries reputational risk if users feel manipulated. Test carefully with bounce rate as a hard guardrail.   |
