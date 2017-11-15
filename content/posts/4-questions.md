---
title: "The 4 Questions I ask myself before starting a project"
date: 2017-11-14T12:50:54-06:00
draft: false
---

Anytime I work on a project I ask myself the following four questions to figure out what code I’ll write. I also use these four questions to figure out if I should even work on a request.

## What’s the benefit?

**Examples:**

* What’s the benefit of this change?
* How much will it improve performance?
* Will it decrease performance?
* Will anyone even noticed the change?
* Will it make the code easier/harder to maintain?
* Will it make the application more secure or less secure?

## What’s the effort?

**Examples:**

* How long will this take?
* How many files/lines of code will I have to change?
* How many applications will this effect?
* Will I have to involve other people to make this change?
* Will I have to configure/setup servers for this change?

## What’s the risks?

**Examples:**

* What is the risk associated with this change?
* What’s the worse that can happen if something goes wrong?
* What’s the business risk associated with this change?
* How much money will this costs if something goes wrong?

## How will this work with future code?

**Examples:**

* Will I have to rewrite applications in the future to work with this?
* How hard will it be to switch new applications to this new code in the future?
* Will it handle future changes with little effort?
  * Like coding a something to accept more then one part number instead of hard coding it to one part number
* Is the code change/project compatible with other planned code changes/projects?

These questions will often determine the solution I decide to go with.

For example if I’m working on an old system that uses ASP.NET Web Forms with the AJAX Control Kit I’ll avoid using JavaScript to make the page look prettier because when AJAX Control Kit partial post backs happens it wipes out the JavaScript state which requires you to re-initialize the JavaScript every time a partial post back happens. In that case the benefit is not worth the effort and the bug risks is very high. The amount of code to get something like JQuery tabs working is kind of crazy because of how ASP.NET Web Forms work.

If the code change that will increase the likelihood of new bugs being added to the future with a small benefit I’ll try to avoid it because the risks is greater then the benefit. The same is true for a change with a small benefit that can cause a lot of money to be lost if it doesn’t work correctly.

I actually witnessed a very expensive fine happen to a client in real time because they designed their account software to use the same database as some other software and the other software locked up the database causing them to miss an important deadline. Having the two applications use the same database made it easy to share data between the two systems but when the database went down it took out two applications with it.

I also look at how the code will work with future changes. I once coded a solution to support multiple parts for a machine though we were using only one part at the time. Later on when someone wanted to experiment with a new part I just setup the new part in the database and the code supported the new part without any code changes. If I had hard coded that part number in the code then I would have had to change the code and do a new release. Because I designed the code with the ability to support multiple parts I didn’t have to make any code changes when they wanted to test the new part.

When developing code I always want to create the perfect code. But using these questions keep me from scope creeping my code changes. It also forces me to design to with business risks, bug risk and estimates in mind.
