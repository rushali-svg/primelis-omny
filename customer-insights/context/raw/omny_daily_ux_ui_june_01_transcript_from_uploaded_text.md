[Omny] Daily UX/UI - June 01
VIEW RECORDING - 37 mins (No highlights): https://fathom.video/share/_9HxSMPvoCpaZ3Dhy62GQYgyBKLsVSBT

---

0:00 - Elodie Martin (Primelis)
  I saw your different comments, so that was good, I had some feedbacks, so yeah, I have one feedback, it's on DSP, again, on DSP, I noticed that for the evolution, I mean the overview, the first, the first tab, there was some confusion, so I renamed things in the selector, so I renamed, so the granularity, oh maybe I should just, oh yeah, so I renamed everything, do you follow me on Figma?

0:52 - Rushali Bhatt (Tcules)
  Yes, I will share my screen. All right. Perfect. Yes.

1:13 - Elodie Martin (Primelis)
  I'm waiting. see that it takes some time to adjust.

1:23 - Rushali Bhatt (Tcules)
  It's in DSP on a date. It's in the project.

1:32 - Elodie Martin (Primelis)
  Yeah. Perfect. Yeah. Yeah. yeah. Perfect.

1:41 - Rushali Bhatt (Tcules)
  So yeah, I renamed these.

1:47 - Elodie Martin (Primelis)
  Now that I see that we have also this over there, I don't know what this is, but here in the first version, you add this month to date value there.  I understand where it comes from, because in this thing, because it's an aggregation, I think at some point in the mini-app, the selector to indicate the time frame on which we're looking at these KPIs.
  ACTION ITEM: DSP: set Overview aggregation presets; switch all tabs to Weekly; add Reach section (ADR, Weekly, Retainers/Newcomers/Churners, Theoretical) - WATCH: https://fathom.video/share/_9HxSMPvoCpaZ3Dhy62GQYgyBKLsVSBT?timestamp=128.9999  But all of these, so all of these are working the way any other table in the app is working, so that's why I changed everywhere from month to day to weekly.  So we need that for all tabs, but now that we are here, for the aggregation, I'm missing, so maybe it's just adding something there, having in mind that we'll probably add the same kind of table below, where we'll have a granularity, weekly, monthly, I mean an evolution.  But for this one, it's only for that table where we need to select a different way of aggregating the data.

3:12 - Rushali Bhatt (Tcules)
  Okay. When you say aggregating, in, like, can you explain it again? So, yeah.

3:24 - Elodie Martin (Primelis)
  So, basically, it will, so, in the application, in general, we have two ways of seeing the data, either per evolution, so per time period, per time period, and so we need to select what kind of period we want to look at, if it's a day, a week, a month, a quarter, a year.  Or, we are looking the data through a certain business axis, the seller, the marketplace, the ASIN, and regarding that, we select...  The time frame on which we look at the data, which is frozen, normally it's declared by the date picker on the bottom right corner of the application.  So here it's the same principle. We are looking, the business axis is the different step, funnel steps, and we don't need a date picker to select the right time frame to look at this data.  We will make the options simpler with some preset time frames, month-to-date, year-to-date, last month, and so on.

4:39 - Rushali Bhatt (Tcules)
  Yeah. Oh, okay. Okay, understood. For the time granularity for overview. Yeah.

4:50 - Elodie Martin (Primelis)
  Because this data, we won't look at the full history. We need the starting point and an end point. But we won't  Let the user manually select, we want to submit pre-existing options.

5:09 - Rushali Bhatt (Tcules)
  Okay, understood. Yeah.

5:14 - Elodie Martin (Primelis)
  So we need to find something related to this. The second thing that will arrive, but I don't have the data right now, it's not, I mean, it will arrive in the week, so that's why we can start working on it.  I mentioned a few, started this, that one section would be missing for the moment. The data are about to be ready, so we can start looking at how we want to represent it.  As the data is not available yet, I did not try things in the mini-app to guide us. So, but basically it's for now, it's quite simple.  So we need to create this rich section everywhere in all, not in overview, but in conversion, consideration, loyalty.

6:17 - Rushali Bhatt (Tcules)
  Yeah.

6:18 - Elodie Martin (Primelis)
  And basically for now, we'll have two kinds of KPIs. One, which will be a single figure, which will be the average daily reach.  So regarding the period we will look, so if it's at a daily level, it will be the reach of the day.  How many people did I target with my different ads? If I'm looking at weekly level, it will be the average for each day of the week.  Same for each day of the month, and so on. So that one is just a value. How much people do I target on a daily basis?  Plus evolution.

7:08 - Rushali Bhatt (Tcules)
  It depends. Either we try an option with a progress bar. In that case, maybe the evolution is not necessary.

7:18 - Elodie Martin (Primelis)
  If we just put the number, it will be necessary. Okay. Then I said two KPIs, but actually it will be three.  I don't know which one I will compare. So the second one will be the weekly breach. And so no matter the granularity we will select, even if it will be daily, monthly, we want...  We will look at a weekly value. So if we are looking at the data daily, we will replicate this value, the values we will display for each day of the week.  If it's weekly, if it's monthly, if it's weekly, that will match. If we are at monthly or above, I think we'll take an average, I don't know, or maybe we won't just display that information.  The thing is, for now, or maybe we will compute it later, for now, let's just not display that value, and focus on the weekly representation.  If we succeed the weekly, we'll be able to replicate. This will be the cumulative values, so, and the split, meaning that...  So in the first column, we are looking at daily reach. And if we are looking at a higher period than the day, we are computing the average.  The thing is, when you advertise some person on Monday, you can also display an ad on Tuesday, Wednesday, Friday.  So you will do like four, five, ten, thousand impressions, but it's still to the same person. So even if we know how many people we target on average per day, and we have the total number of impressions, they can be spread day after day, can be the same pool of people who are targeted, or it can change.  So that's the thing we want to measure and to highlight. But at a daily basis, it's really hard to compute.  So that's why we chose, at least for the beginning, a weekly level. And so for each week, the data we are computing is first, how many different profiles are targeted with the ads across the week.  So it will be the sum of the average daily reach. It may, it cannot be lower, but it can be higher, but it will be somewhere between one day daily reach and seven times, this value.

10:31 - Rushali Bhatt (Tcules)
  Yeah.

10:34 - Elodie Martin (Primelis)
  So we will compute that value, the cumulative, for the week. And this value, we will split it into two groups.  The people who were already targeted the past week and the new people.

11:00 - Rushali Bhatt (Tcules)
  Nice. That are targeted for the first time during that week. Yeah, okay.

11:07 - Elodie Martin (Primelis)
  So the retainers and the newcomers. Yeah. And on top of that, we also have the value of people, the churners, the people that we lost from the previous week.  Oh, okay. Which is not part of the cumulative value of the week, but which is still an interesting information.  So maybe to be displayed on another column, I don't know how to represent it. So the challenge to represent the best disinformation.  Okay. So basically, how many people, when I look at all the people I targeted during the week, how much people does it represent?  How much were already targeted the week before? How many people were targeting this week? For the first time, how many people did we stop to target during this week compared to the week before?  So we have that info. We would like to display that information in the reach. And the third element we would like to highlight also is as we have the budget, we know how many.  So we do not display the budget here in that screen, but we have the budget overall, which is defined somewhere.  And then this budget is used. Amazon decides how to use this budget. can use it in full or some money can remain, for example, if you don't have enough people to target, for example.  Yeah, so we know the budget we allocated to the campaign. We know also, um, we know Know the average cost per mill impression, and we have a setting, which is not displayed here, but we have in the data the frequency, meaning how many times we want to display for the same profile per 7 days, per 10 days, per day.  So basically, we are able to compute how many profiles we should target for a certain week, based on our budget, based on the cost, so the inventory we are positioned on, and the frequency cap, the maximum number of ads we want to display per profile.  We are supposed to compute how many profiles we can reach with these criteria, and so the goal is to compute this theoretical  Weekly reach with the reality.

14:05 - Rushali Bhatt (Tcules)
  Okay, yeah. Oh, okay. Understood. So the goal is, in the end, is twice.

14:13 - Elodie Martin (Primelis)
  It is double. The first one, we want to see, okay, with this criteria, do we have enough money to reach and reach the pipe?  Are we able to target enough people? Yeah, enough people to match our objectives? And then, the quality of the reach, because this is something where we are totally blind right now.  Okay, with that money, am I just displaying an ad one time per a million users? Okay, I do a million impressions, but actually, I display only one, and so I'm not able to convert with one ad per person.  Or, do I put too much pressure on the same profile? Okay. Because I'm targeting way less people that I should diet, or if there is the rotation week after week too intense, and so again, the pressure is not enough in time, it's to really measure the quality of the reach, and so the ability for our campaigns to really convert in the end.

15:31 - Rushali Bhatt (Tcules)
  Okay, okay, got it. So that's the new section, yeah, ask you on. Sorry, yes, so the one where we are having the cumulative amount of like the budget, and according to that budget, how many profiles we will be able to like capture, is it?  According to, will it be according to the whole time period weekly, in this case weekly, will be, or will it be the time remaining at that particular?  Yep, that's a good point.

16:18 - Elodie Martin (Primelis)
  So this KPI, the theoretical reach, we would be able to compute it at different levels, but what's interesting, is to compare it to the reality.  So to me, will be out, the best would be to compute it at weekly level. And so the same as the cumulative reach, we will all, we will look at all that information at the same level.  So this is kind of a challenge, because all of the columns are depending, depend on the selection, the granularity selected above.  larger current- cinq, The period. But this one is a bit different. So one option would be to materialize that this is a bit different and that won't change.  The other option would be to display it only at a weekly basis. And if it's not a weekly granularity selected, display some message or things like what we did for the BSR.  I don't remember if it was already you at that time who worked on the BSR. I can show you in the dashboard.  Let me show you. Let me show you.

17:46 - Rushali Bhatt (Tcules)
  We did something.

17:56 - Elodie Martin (Primelis)
  So here. In the breakdown by Azine, on the list tab, we have this BSR column, but the BSR, it's the best position.  So it's the ranking of the product in Amazon. You know, when we worked on the market share, you know, we have the top sellers per category and each product has a rank.  So that's its value. We are this thing here. So not capped at 100, but it can be 10,000 lost in Amazon rankings.  But the thing is, this value doesn't mean anything if we combine all the marketplaces and try to make kind of an average.

18:49 - Rushali Bhatt (Tcules)
  That doesn't work.

18:50 - Elodie Martin (Primelis)
  So what was proposed before, maybe it was with Vahoon, I don't remember exactly. But so... This value doesn't make sense if there are several marketplaces, but once you select one place, then overlay it disappears, and then we have the values.  So here, we started the values with null.

19:23 - Rushali Bhatt (Tcules)
  That's 12 weeks as a period also, right?

19:29 - Elodie Martin (Primelis)
  Yes, we don't have the BSR display, maybe we have some data issues, because we are Monday morning, but last day was 24, but that's okay.  mean, so currently don't have any data, maybe we had an issue this morning, but you see in the past, every different data.  The concept is, okay, at that level. When there are several marketplaces, doesn't make any sense, but the column is still there.  So I display, I highlight to the user that there is some data, and I guide the user on how to access this data.  So that can be also a way of doing it. So it's visible only at weekly level, but otherwise, we still materialize that some information is available.

20:29 - Rushali Bhatt (Tcules)
  Okay, okay, yeah, we can do that.

20:35 - Elodie Martin (Primelis)
  So yeah, this is on the dashboard, listing tab, and if there are several marketplaces, you have this overlay, otherwise, it displays instantly the value.

20:51 - Rushali Bhatt (Tcules)
  So yeah. Okay, understood. Okay, so that... Columns, we'll add in the section, we'll add in the, for all the tabs, right?

21:09 - Elodie Martin (Primelis)
  Three tabs. Yeah. Because we don't have the awareness for now.

21:13 - Rushali Bhatt (Tcules)
  For all the overview, yeah, all these three. Yeah, exactly.

21:19 - Elodie Martin (Primelis)
  So yeah, the goal is really to know how many people do I reach, so at a daily basis, then when we have some consolidation at a weekly level, how many people do I reach, and is it in line with my budget, and how is the rotation week over week, how do I target all the time the same person, and for some time, until they convert, or until they go out of the, phase out of the pipe, just because it's been too long, they did not convert, so at some point, I just drop the thing and let it go, and replace them by...  new people, or do I just changing all the time, and so it doesn't have a, it's not, it's not a good strategy, as I'm just putting the room out of the windows, but without any concrete results.  Okay, yes.

22:21 - Rushali Bhatt (Tcules)
  Okay.

22:25 - Elodie Martin (Primelis)
  So that's the main, the main thing we need to start working on. The other, because I'm not sure that it will take the week, the other topic we would like to work on this week is one of, there is one project that we, for which we are not done yet, regarding the customer insight, I did not find it, I'm not sure that we already finished it, there are three, three aspects of the customer.  So by inside, the first table, the one we started a few months back, the LTV tab, the court, and the last one is the LTV per 18.  So that's, again, let me show again my screen. In the mini-app, is something else. No, it's not that one.  That one is the one I'm developing.

23:37 - Rushali Bhatt (Tcules)
  We have this view.

23:39 - Elodie Martin (Primelis)
  Let me just find a seller for which we have data. We have this view that is used by, also by the OPS team, and that we need at some point to integrate into the platform.  Well...

23:56 - Rushali Bhatt (Tcules)
  Mm-hmm.

24:00 - Elodie Martin (Primelis)
  So basically, here we have the seller, so it's a tab. I'm not using it a lot, but I'm trying to.  So the goal is to, so again, it's around LTV data. Yes, exactly. So the goal is to, so here there is no time frame.

24:25 - Rushali Bhatt (Tcules)
  Yeah.

24:26 - Elodie Martin (Primelis)
  Yes, it's, yeah, I guess it's because the data is computed over a year, otherwise, then there is no data, either it's not computed.  You have the value in revenue and in margin. So same, kind of the same topic as we used to discuss.  Margin is the one which is used for the bidding, but you have also the revenue. And the goal is just to display and to, yeah, to indicate.  How many people bought this product in the time frame, how many money was spent on average per people, and so this one, I don't know what this is, this KPI, LTP?

25:30 - Rushali Bhatt (Tcules)
  Is it a sort of a ratio between LTV and first time purchase, as it's, yeah, yeah, but, is it, so here it's 20, so, no, it won't be that, because, because this doesn't give 170, yeah, I don't what this is.

26:01 - Elodie Martin (Primelis)
  I don't know what this is.

26:02 - Rushali Bhatt (Tcules)
  That's a good question.

26:04 - Elodie Martin (Primelis)
  I don't know. I don't know what this is. And then we have to break down. So purchase, entry, repeat, cross-repeat.  So basically, yeah, it's to have the details per product to see which products are the most important. One thing which is important, I would say something which is not really done yet here is yet to be kind of able to...  So here it's sorted by maybe entry customers, so the product that are sold the most. But sometimes, you know, we have also new products or not...  Sold a lot during the past year, but with promising results. yeah, these KPIs can be also interesting not to, I mean, to sort the products independently from the number of customers they can reach.  And something that may be missing, but I think that we, that's a lot of questions that we have from Ops.  And it's the same for the course, but course is more visible because we see the time frame. Sometimes I say, oh, I don't see any data, I don't see any data, but just because we don't have enough history, so if we can have kind of a recap on how long, what's the period taken into account to compute this, visually speaking, maybe it could help to explain, okay, because this case.  PPI is not available, because, for example, you have just a six-month history, so we are not able to run the one year, the full year of computation.  These are different, but from what I noticed, that, okay, they arrive and say, oh, I don't see the data, or I see it's empty, for example, here.  Okay, we have no data available for this seller, but is it because it's a vendor, or is it just because the data is not connected?  We have different ways, you know, when we miss some history, it's a bit different here, because it's not, but, yeah, sometimes they say, oh, I have some history, but actually, okay, they have history, but they have just six months of history, and so it's not enough to, to fulfill, because, for example, here, it's a seller, so, really, we should have the data for the seller.  But if I go and I deep dive into BigQuery, I would notice that, okay, maybe I have three months or four months.  And so as we are, and I guess it's this, no, it's not this one. Okay, that's it. The entry customer, this number is computed for over 12 rolling months.  If you don't have a 12 months of history, we are not able to compute this KPI. So for now, we do not display anything at all.  Maybe some later we will move on. Yes. But to do that, we should have the vision on what's the history.  And so also to make our mind on the data we are looking at. So is it relevant or not, but we need to know what history is.  Okay, I'm doing a screenshot of it, but you have a lot of video, so that you have a, but yeah, so that's just to introduce it, let's focus first on the DSP to finish it properly, but if you have more time, you can start with this, thinking about what can arrive next.

30:26 - Rushali Bhatt (Tcules)
  Okay, we also had this one, so for the customer insights, like the topic that you just briefed, so is there a way to track that the different scenarios that there is only three months of data tracking for this seller, or this is a vendor you need to pick a seller, are there  ways to track this, so if there is, we can have certain templates of guidelines for the users that this is how you can see data, or this is not available, you can switch to other sellers or something like that.

31:16 - Elodie Martin (Primelis)
  Yeah, for vendor, we have that information, it's part of the account name, so that's pretty easy to detect. Later on, will work on the connection to get extra data, but it's, it's, with fees to pay to Amazon, so we'll be able to give the right message if we don't have the data, it's because you need to purchase this data set.  So this one, we are able to track it, the rest, we are also able to track it, and to compute it.  It's not exposed directly right now, but we... We are able to do it, and to materialize it, okay, it's because the data is empty, we could try to monitor, okay, because just we don't have more of the data before this date, and you'll start seeing data after this date, that's something that we could do, yes.
  ACTION ITEM: Send LTV-per-ASIN screenshot to Rushali - WATCH: https://fathom.video/share/_9HxSMPvoCpaZ3Dhy62GQYgyBKLsVSBT?timestamp=1941.9999

32:23 - Rushali Bhatt (Tcules)
  Okay, okay, understood. Okay.

32:32 - Elodie Martin (Primelis)
  Okay, so I will send the screenshot, I lost it, I will do it again, and that's it for me, if you have any questions, feel free to reach out.

32:46 - Rushali Bhatt (Tcules)
  so we also wanted to share this update with you, so since we have been also working, like integrating editing, uh,  Different types of AIs and LLMs in our design process. regarding that, we thought that maybe including some AI-assisted workflow for Omni as well as Signal can help a lot in like having quick approaches or quick prototypes for what different concepts that we have.  So right now we have a workflow set up for internally, we are exploring this process where we are using a LLM codex and a cursor as a medium to produce different screens and different ideations which are prototype ready.  So these can be quick iterations where we can show different directions for the UX. points in the UX. new that the So So  This, there is a finalized direction that we need to go on. We can maybe have a dev dev handoff ready in Figma.  So right now, this can be something that we are internally exploring. So maybe we can continue creating some UX iterations through this method for the recent tasks as well.  So these are some of the, yes, so we just are generating some of the things through, through this, but we are also, it's a learning curve right now.  So we are trying to have a, maybe a shell fixed for a frame and then have the iterations built on top of it.
  ACTION ITEM: Prepare AI-assisted UX iterations for Elodie - WATCH: https://fathom.video/share/_9HxSMPvoCpaZ3Dhy62GQYgyBKLsVSBT?timestamp=2088.9999  So these are some of the things we are trying to internally between us in the team. So we'll have, we'll also approach these new tasks through that.  Maybe Maybe. can have some iterations for you tomorrow for that as well. Okay.

35:05 - Elodie Martin (Primelis)
  Yeah, that's a good direction. That's interesting. Yeah, because also, yeah, when it's only reporting, that's pretty okay because the framework is already set up.  But when it comes from other interactions and even in the reporting, for example, when we are using the filters and stuff, sometimes it's not closing.  We need to click outside of the filter. mean, that's a thing where for sure we are not good at right now in terms of specifications to the developers.  And so not all of the best practices are developed right now in the platform. And so we can have some real behaviors sometimes.  So yeah, that's a good thing to have it something that can be testable to... to face that earlier in the process.

36:03 - Rushali Bhatt (Tcules)
  Definitely, yeah. Okay, great. Then we can have some iteration. We'll work on this for the newer tasks so we can have good iteration for you already.  Okay, perfect.

36:18 - Elodie Martin (Primelis)
  Thank you very much. Feel free to ask if you have any questions on the other topics. Definitely.

36:27 - Rushali Bhatt (Tcules)
  See you tomorrow.

36:28 - Elodie Martin (Primelis)
  See you.

36:29 - Rushali Bhatt (Tcules)
  Bye-bye. Thank you. Bye-bye. Bye-bye.