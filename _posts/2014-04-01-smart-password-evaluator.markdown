---
layout: post
title:  "Introducing iSEC's Smart Password Evaluation Service"
date:   2014-04-01 06:00:00
post_author: Michael Lynch
categories: passwords
---

**Note: This post was written as an April Fool's Day joke; we will (fortunately) not be offering this service. We hope you enjoyed this bit of humor about the current challenges in the security industry.**

### The Trouble with Password Strength Meters

One of the main downfalls of using passwords as an authentication mechanism is that it's extremely difficult to convince users to select strong passwords. In the past few years, several web applications have begun to use "password strength meters" which show the user how resistant their chosen password is to brute force attempts.

![eBay's password strength meter]({{ site.baseurl }}/images/2014-04-01-meter-ebay.png)

A [recent paper](https://madiba.encs.concordia.ca/~x_decarn/papers/password-meters-ndss2014.pdf) by Carnavalet and Mannan showed that, while these meters are somewhat effective at increasing the strength of passwords, they are easily fooled. Many meters rate passwords like "password$1" as strong despite the fact that modern attack tools could easily crack such a password.

### iSEC's Service

What's the problem here? Is your attacker a little JavaScript snippet with a pretty colored bar? No! Your attacker is a constantly evolving and adaptable human adversary. What's the only way to defeat a human? With a human!

With this in mind, iSEC is proud to announce iSEC Smart Password Evaluation Service, the first and only password evaluator that uses live humans to judge the strength of passwords.

#### How it Works

Let's say you register a new account with XYZ Bank. They're an iSEC customer who wisely uses our Smart Password Evaluation Service. When you enter your desired password into the XYZ Bank application, their web server makes a backend request to our service. This request includes all of your registration information and your attempted password in plaintext. (Note that this backend request takes place over leased lines. This escapes the dangers of crossing Internet infrastructure and allows us to maintain the fastest service possible by securely omitting encryption.)

![Design Diagram]({{ site.baseurl }}/images/2014-04-01-flow-diagram.png)

iSEC's trained specialists then evaluate the password and determine whether it meets the length and complexity requirements of XYZ Bank. We also use our human intelligence to look for weaknesses that a computer could never determine, such as:

* Is your password derived from your personal information?
* Is your password some obfuscated form of the word "password" that a computer cannot detect (e.g. "p4ssW0rd")
* Does your password contain the letter "z"? (All passwords should contain one or more "z" because it's always the last character that hackers attempt in brute force attacks.)

#### Examples

Let's take a look at some real life examples, taken from customers in our pilot program.

##### Financial Services Application

Our first example comes to us from one of our financial services customers. Accounts on this site control millions of dollars worth of assets, so the security of these accounts is paramount. No one other than the end user should **ever** have access to the user's personal details, especially not their password, so it's critical that we evaluate the password thoroughly.

![Example 1 - Weak Password]({{ site.baseurl }}/images/2014-04-01-example1.png)

The user's password here demonstrates a very common password weakness: it is largely based on the customer's personal information. If the attacker compromised the full user database (which is quite common in large data breaches), they could combine dictionary words with the user's personal information to discover the password.

In this case, the user's password is simply the word "Go" followed by their favorite sports team and year of birth. iSEC's analyst therefore rejected this password as **weak** and the user was required to select a new, stronger password.

##### Message Board Application

We want to protect all the Internet's users, not just those of large financial services clients. There are many smaller sites in our pilot program as well. Our next example comes to us from a customer who runs a free message board where users can discuss young adult fiction:

![Example 2 - Strong Password]({{ site.baseurl }}/images/2014-04-01-example-2.png)

This site collects fewer personal details during registration so our analysts have less to work with. What we can see is that the English word "Team" appears in the password, which is bad. However, the remainder of the password are 12 random, nonsense characters that no attacker could guess, so we mark the password as **very** **strong**.

#### Scaling

We expect that very soon, every major web site on the Internet will use iSEC Smart Password Evaluation Service to solve their password woes. How do we scale our solution to address millions of requests per second? After all, each request requires manual interaction from a trained specialist.

Well, like most difficult problems in security, the answer is: the cloud.

Specifically [Amazon's Mechanical Turk](http://aws.amazon.com/mturk/) service. For those not familiar, Amazon's Mechanical Turk allows companies to hire temporary workers for "micro-tasks": short jobs that can be completed within a few minutes.

Of course, evaluating passwords is very sensitive, skilled work so we can't allow any anonymous user on the Internet to do it. Before any Mechanical Turk worker can begin evaluating passwords, they must complete a rigorous examination that challenges their security acumen as well as their personal integrity.

![Analyst Qualification Test]({{ site.baseurl }}/images/2014-04-01-qualification-test.png)

We're only a few months into our pilot program, but we have already found *thousands* of Mechanical Turk workers who are extremely enthusiastic about their work. Every day they tell us, "Please send us more passwords!" At first we worried that our workers would shy away from the responsibility of evaluating passwords for high value accounts such as banks or stock exchanges, but those types of accounts are proving to be our most popular. Some of our workers have even offered to pay *us* for the opportunity to protect these accounts! Talk about passionate employees!

### Conclusion

After software developers and security professionals have spent decades of struggling to get password authentication right, iSEC is very proud to have solved passwords once and for all.

We will be expanding our Smart Password Evaluation Service pilot program very soon. If you run a web site and are interested in joining the next wave of our pilot program, stay tuned to this blog over the next few weeks for instructions on how to start using our service on your site.

**Note: This post was written as an April Fool's Day joke; we will (fortunately) not be offering this service. We hope you enjoyed this bit of humor about the current challenges in the security industry.**