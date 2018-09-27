---
title: qos marking reference
date: 2018-09-26 10:59:57
tags:
---
# Preface
If you’ve ever written a QoS policy, or needed to configure some random piece of communications or A/V equipment for your precious telecom princess who can’t spell DSCP, but blames the `roads` for everything, you probably have this info saved somewhere. 

I, for one, learned how to spell QoS just a couple of years ago, and have since made my own spreadsheet for reference.

I won’t go into too much detail here. If you stumbled across this during a Google search, you probably already know what these values mean and when/why/where/how they’re used.

PS: in case you don’t, [this](https://elhallak.wordpress.com/2011/08/07/what-is-the-difference-between-cos-ip-precedence-and-dscp/amp/) post explains it fairly well.


| IPP | AF   | DSCP | ToS | ToS HEX | DP      |
|-----|------|------|-----|---------|---------|
| 1   | CS1  | 8    | 32  | 20      |         |
| 1   | AF11 | 10   | 40  | 28      | Low     |
| 1   | AF12 | 12   | 48  | 30      | Medium  |
| 1   | AF13 | 14   | 56  | 38      | High    |
| 2   | CS2  | 16   | 64  | 40      |         |
| 2   | AF21 | 18   | 72  | 48      | Low     |
| 2   | AF22 | 20   | 80  | 50      | Medium  |
| 2   | AF23 | 22   | 88  | 58      | High    |
| 3   | CS3  | 24   | 96  | 60      |         |
| 3   | AF31 | 26   | 104 | 68      | Low     |
| 3   | AF32 | 28   | 112 | 80      | Medium  |
| 3   | AF33 | 30   | 120 | 78      | High    |
| 4   | CS4  | 32   | 128 | 80      |         |
| 4   | AF41 | 34   | 136 | 88      | Low     |
| 4   | AF42 | 36   | 144 | 90      | Medium  |
| 4   | AF43 | 38   | 152 | 98      | High    |
| 5   | CS5  | 40   | 160 | A0      |         |
| 5   | EF   | 46   | 184 | B8      |         |
| 6   | CS6  | 48   | 192 | C0      | Routing |
| 7   | CS7  | 56   | 224 | E0      | Network |