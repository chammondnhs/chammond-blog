---
layout: post
title:  "Pipelining"
date:   2023-01-28
categories: distributed-systems software-engineering
---

Do you care about end to end latency or throughput? Pipeline transactions. Many people think decreasing latency is the same as increasing throughput, but this is not always the case. Lets take a scenario where I have a system which handles a transaction in 100s, the throughput then is 0.01 tps. If we break this into 10 steps and consider a 20% overhead for pipelining, what happens? Now, we handle a transaction in 120s. But, each stage is handling a transaction in 12s, so our system is effectively processing 10 transactions in parallel. The throughput has just increased to a transaction every 12s, or 0.083 tps. Depending on how you calculate improvement, that is an 8x increase in throughput with a tradeoff of 20% for latency. Fun fact – this is what makes modern CPUs so fast, but it also applies to distributed systems and cloud architectures.