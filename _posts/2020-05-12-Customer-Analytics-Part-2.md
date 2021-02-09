---
toc: true
layout: post
description: Simple and minimalistic predictive customer analytics starting point
categories: [Customer Analytics]
title: Predictive Customer Analytics (Part 2)
---

# Intro

Customer Analytics is a valuable tool, but often the basics are overlooked. It can have a huge impact, and it doesn't always mean complex modeling.  It always starts with the basics.  

This is the 2nd post in a series about customer analytics.  The first post discusses descriptive analytics and how to create and use descriptive customer analytics.  In this post we will be building on that descriptive framework to create a very basic predictive model.  A predictive model allows companies to plan proactively instead of reactively.

# Background

In the first post we created three descriptive metrics (Recency, Frequency, and Average Monetary Value).  Recency is days since the last purchase.  Frequency is the number of cycles that the customer purchased product in.  Monetary Value is the average revenue brought in from that customer in cycles where the customer purchased product.  How can you determine the predicted customer value and take action based on that information?

We need to group customers based on how they behave.  This allows us to quickly and efficiently test different actions and see how that affects our long term revenue projections.  A customer who  makes many small purchases may be just as valuable as a customer who places huge orders infrequently, but they should be handled differently.  RFM is one tool we can use to group customers together.

# Normalize the metrics
 
We start with a basic table with three companies and their 3 KPIs.  

||Recency (days since previous purchase)|Frequency (number of months with purchases)|Monetary Value (avg monthly revenue during months with purchases)|
|-|-|-|-|
|Customer A|3|3|\$79|
|Customer B|35|2|\$91|
|Customer C|48|1|\$9852|

Now that we have values for each of these three metrics (Recency, Frequency, and Monetary Value), we need to put them into a format where we can easily compare the customers.  This is called normalizing the data.  Normalization puts all the metrics on a scale of 0 (lowest) to 1 (highest).   Here is a formula for normalizing:

```(<Value you want to normalize> – <Minimum Value in series>) / (<Maximum value in series> – <Minimum value in series>)```

Let’s walk through normalizing the Recency KPI.  Based on the formula above we need a couple of pieces of information.  Let’s identify these now.

Minimum Value in series = 3
Maximum value in series = 48

Now let’s plug in the formula for each customer to normalize the values.

||Recency|Normalized Recency|
|-|-|-|
|Customer A|3|=(3-3) / (48-3) = 0|
|Customer B|35|=(35-3) / (48-3) = 0.711|
|Customer C|48|=(48-3) / (48-3) = 1|

The next step is to repeat this process for the other metrics.  I won’t walk through the other two, but here are the accurate values if you’d like to test yourself.

||Recency|Frequency|Monetary Value|
|-|-|-|-|
|Customer A|0|1|0|
|Customer B|0.711|0.5|0.001|
|Customer C|1|0|1|

A low recency score is good.  A high Frequency or Monetary Value Score is good.  If you’d like to simplify it so you don’t have to remember that feel free to take your normalized recency score and subtract it from 1.  That will make low scores bad and high scores good on all metrics.

# Group the customers together

Now that we have normalized our KPIs, we need to group our customers together.  In the table above we only have 3 customers, so there would be no point in grouping them together.  In a more practical example we may have 1000 customers, 10,000 customers, or more.  When we have that many customers, we can greatly simplify things by grouping like customers together.  

We can group customers using our RFM KPIs, but there may be more information we want to pull into that decision.  For example if we are a manufacturing company that sells product to end users as well as distributors we may want to take that into account.  A distributor is likely to behave and react differently from an individual person.  For example, an individual person may get a coupon in the mail and decide to purchase, but a distributor contact may get hundreds of coupons a week and just get annoyed.  

A lot of time should be spent exploring different ways to break up customers.  Explaining how you break up the customers into groups to sales people, product management, purchasing, production control, and other functional groups in your company can be a great way to get ideas.  Each of these groups sees how customers react in different ways and talking to all of them can help give a more complete picture.

# Create probability matrix

The goal of customer analytics is to predict how much money we are going to make next month, and the month after, and the month after that, and so on.  Once we can predict that with reasonable accuracy we can determine exactly how much revenue we can expect from each customer if we do not change anything.  

We need to put probabilities on customer actions.  In simplest terms the customer has 2 choices during each cycle, buy or do not buy.  So how do we figure out what the chance of that is for a group?

Suppose we a group of distributors we sell to that we believe act similarly as with the table below.  A 1 means that the distributor bought something in that cycle, a 0 means that the distributor did not buy anything in that cycle.

||January|February|March|
|-|-|-|-|
|Distributor A|1|0|0|
|Distributor B|0|1|0|
|Distributor C|0|1|1|

Since there are 9 total opportunities to buy, and 4 of those have buys in them, we will assign a 4/9 chance of buying.  Really this is just another way to measure frequency.

Now we know how many of the customers in the distributor group will buy in a given month (4 out of 9), so we need to turn that into a revenue figure.  To do this we will take the sum of revenue from these customers and divide that by the number of buys.  Here we are calculating Monetary Value (M), but instead of looking at it on a customer level, we are looking at it for a group of customers.

Once we multiply those two numbers together we have an estimated monthly revenue.

There’s several areas for future improvement that I won’t cover in this post.  Depending on the market or the business model your company uses, they will vary in significance.  Here’s a few of them:

* Take into account recency.  
* Take into account customer retention.  This makes forecasts accuracy go down farther out you go into the future.  Since for this application we aren’t looking out very far in the future it makes less of a difference, but it is definitely high priority on our list of future enhancements.
* Changes in buy patterns based on seasonal trends.
 

# Increase revenue using predicted value of each account

Now that we know roughly what revenue we can expect, we can use that for a variety of things.  Here’s a few ideas:

* First, we can look at which locations/territories are performing as forcasted.  Once we know the high performing locations and the low performing locations, we can start to identify what the differences are. This can also be used to manage performance of employees, set meaningful incentives based on revenue, and set measurable objectives.
* We can continue to do A/B testing, but be able to tie this to actual revenue dollars.
* We can use these forecasts to determine inventory stances on either components or salable goods.
* Now that we have grouped customers that behave similarly, we can start to determine how we should treat each group.  We can have limited A/B testing.  Instead of taking a random group of customers, we can take a random group of distributors to see how they specifically react.
* We can determine who our most valuable customers are.  Typically without measures, we remember the big purchases.  But a regular purchaser that doesn’t make big purchases may be bringing us more revenue.  Understanding which customers are most likely to be the most profitable is crucial and can help us determine pricing tiers for customers or determine customer loyalty programs.
* We can identify low performing groups and create a strategy to get more penetration into those customers.  Maybe for those customers we can send them surveys.  Maybe we can set up a forum and do 6 month surveys where we work and collaborate with them regularly.  This can help give insight into why they don’t purchase much, as well as be a good sales opportunity.  We can also try to take action to take the low performing customers and get them to increase revenue through promotions or other incentives.
* We can take the high performing customers and make sure that they know they are appreciated.  Whether it’s a can of cashews over the holidays, or having a sales person reach out to talk once a month, building that relationship can really build customer loyalty.