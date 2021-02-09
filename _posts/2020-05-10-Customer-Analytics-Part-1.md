---
toc: true
layout: post
description: Simple and minimalistic descriptive customer analytics starting point
categories: [Customer Analytics]
title: Descriptive Customer Analytics (Part 1)
---

# Intro

Customer Analytics is a valuable tool, but often the basics are overlooked. It can have a huge impact, and it doesn't always mean complex modeling.  It always starts with the basics.  Because customer analytics can make such a big impact, I am going to break this into several posts.

In this post (Part 1) I am going to explain a basic descriptive customer analytics framework and how use it to identify the current state.  This understanding allows us to conduct A/B testing so we can measure how our actions impact revenue and by how much.  There are many ways to do this, this is just one of them.

In Part 2 I'll talk about how to build on the descriptive framework to create a predictive model.  A predictive model allows companies to plan proactively instead of reactively.

# Background:

Many companies rely on experience and basic summarizing of historical statistics to make decisions.  While both of these are useful tools, a powerful way to successfully sustain long term revenue growth is to add customer analytics to their tool belt.  In this post I am discussing the starting point for analytics, descriptive analytics.

An easy and solid starting point for descriptive analytics is a RFM (Recency, Frequency, Monetary Value) model.  A primary advantage to this is the only data you need is purchase history for each customer, which is information that almost every company tracks.  I’ve outlined the three main steps to creating this framework and using it to increase revenue.

# Determine length of customer buying cycle:

The first step is to determine what time range is a good time range to use for a buying cycle.  For a grocery store, maybe we say typically people go grocery shopping once a week.  In that scenario we would use 1 week as our time range for our cycle.  However a company that prints business cards may find a much longer time frame as customers tend to buy 1,000 and repurchase when they get low.  For this example we could use a 6 month cycle.  I encourage people to explore their data and pick a time range based on intuition.  There are better and more complicated ways to figure out this time range, but I encourage people to demonstrate results and revenue growth before circling back with more resources and support from executive management.

# Calculate descriptive customer metrics:

Let’s say we choose a 1 month cycle.  The next step is to create and fill in a table to get frequency and monetary Value.  In the table below I outline how we calculate both of those KPIs (Key Performance Indicators).


||January|February|March|Frequency|Monetary Value|
|-|-|-|-|-|-|
|Example|Rev|Rev|Rev|# of slots purchased in|Average Monetary Value
|Customer A|\$102|\$60|\$75|3|=(\$102+\$60+\$75) / 3|
|Customer B|\$97|\$85|\$0|2|=(\$85+97) / 2|
|Customer C|\$0|\$9852|\$0|1|=(\$9,852) / 1|

Once this is done add another column for Recency and fill that in with how long since that last purchase.  This can be days, hours, or seconds since last purchase depending on how far apart customer purchases typically are.  For this simplified version we will use days.  We end up with a table like this:


||Recency|Frequency|Monetary Value|
|-|-|-|-|
|Customer A|3|3|\$79|
|Customer B|35|2|\$91|
|Customer C|48|1|\$9852|

# Conduct A/B testing:

Now that we have three metrics (RFM) that describe customer buying patterns, we can start using them to run experiments to drive revenue growth.  A/B testing is a simple experiment that you can run to compare two things. You split your customers into two group and make no change to what you are doing to group A, but do something different in group B.  By doing this we can compare the revenue of the two groups to see what impact our efforts had.  If B is better, we will apply that action to the entire customer base.  If not, we scrap the idea and move on.  This is a never-ending process of  testing new ideas.

# Here’s a few ideas for A/B tests using RFM to get you started:

* Call every customer in group B to see how that impacts revenue.  Does this increase Frequency (F) or average Monetary Value (M) of orders?  Is it worth the additional resources?
* Send a marketing email blast to everyone in group B.  How does this change group B’s buying patterns?
* What impact does sending a one-time-only 5\% off coupon have?
* If we raise the price by 5\% in group B, what is the effect on revenue?  This is especially useful because we can run limited experiments and gauge reaction of price hikes without angering every customer.
* If we raise the price on a product that is nearing the end of its product life cycle, do sales increase on the newly released product?  Does a price hike on old products encourage customers to buy newer versions?
* Send group A customers to the current website and group B customers to a new website layout.  Monitor sales, traffic, and clicks on each site.  This can help determine the better layout.