---
title: AI Hierarchy - What is really important
date: 2026-05-15
categories: [blog]
tags: [machine learning]
---

After having worked with AI for about 2 years, I think what we have essentially built in the CS community in the past 15~20 years or so is nothing more than a machine that learns to pick up correlations & patterns (very well) from a given distribution of data. 

With that, I developed the following insights: 

1. Insight No. 1. Data is paradigm. Quality data enable smart machines. In my mind, text in its nature is higher quality data than images (or perhaps any other possible modality out there) because it is constructed with human languages. Text has the advantage because it is born with "injected" intelligence from human, and it is perhaps the one modality that most aligned with how we understand the world. (whereas for example images only capture relationship for pixels - the information is given in nature, it is then filtered and altered due to hardware limitations, and eventually presented to us as images, which almost have nothing to do with how we understand the world). See this article from Kevin Lu for more evidence: https://kevinlu.ai/the-only-important-technology-is-the-internet.

2. Insight No. 2. The algorithm matters. This is second to data because the algorithm determines what invariances are learned from the data and how the neural net learns it. The best algorithm, essentially, allows the network to learn 100% of what is available from the data, in an efficient manner. 

3. Insight No. 3. Third place goes to model architecture. It leads to improvements (sometimes a lot of improvement) but is less critical than data and algorithm.

4. Insight No. 4. The machine is not intelligent and conscious. There is nothing wrong with the feeling that machines are smart. But we have to understand the intelligence is coming from the data. The machine does a very good job at picking up the correlations and learning from our data, and the machine's non-linearity further enpowers it to generate things that are outside the distribution of the original training data.

5. Insight No. 5. There is also a middle layer which sits between the model and the end user. If this is done right, the machine can feel like it is very very smart. This layer handles things like, user context, memory, MOE coordination, etc. 

So to a researcher, I think figuring out how to collect better quality data is going to be very important (by quality I don't mean less-nosiy data, I mean data that provide more information to learn from). In a lot of applications, we can only capture data by scratching the surface. One example to illustrate this is to try to figure out human intent. We can collect data of a person's movement, collect the words he/she says, and even use sensors to collect data about the person (heart rates, temperatures, breaths). But imagine if we can go inside the person brain and directly collect the data there regarding what he/she is thinking. The performance gains that you get from doing that, I believe, will not be beat by any algorithm or architectural improvement. The thing is, how. 

But as a researcher or engineer, if you are not participanting directly in that research, I think it will still be worth it to know, at least, what are quality data and where to find them. 

After data research, there comes algorithm, architecture, and system research, which are all important pieces of the bigger puzzle, and I think these will also be fun fields for researchers to participate in.

Regarding intelligence and consciousness in the end, I think the realization that the machine is not the intelligent part of the equation is just very helpful and foundamental. I was often haunted by the question whether the AI I was working with was conscious (sometimes it felt like I was dealing with another person), and I felt just a huge relief after knowing it is not. Well, at least now I am no longer haunted by that question in my head any more.
