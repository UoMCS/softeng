# (PART) Team study materials {-}

# Starting Stendhal {#starting}
Stendhal ([stendhalgame.org](https://stendhalgame.org/)) is a massively multiplayer online role-playing game ([MMORPG](https://en.wikipedia.org/wiki/Massively_multiplayer_online_role-playing_game)) with an old school feel. You can explore cities, forest, mountains, plains and dungeons. A screenshot of some of the the game shown in figure \@ref(fig:stendhalgame-fig).

```{r stendhalgame-fig, echo = FALSE, fig.align = "center", out.width = "75%", fig.cap = "(ref:captionstgame)"}
knitr::include_graphics("images/Semos_City_NPCs-2020.png")
```

(ref:captionstgame) A screenshot from [stendhalgame.org](https://stendhalgame.org/) showing a selection of the 300 non-player characters (NPCs)

In this course, we use the open source code base for the Stendhal game to practice a range of software engineering skills.  This chapter describes an activity that you can work through with your team to help you get started on working with the code base.  You'll need to carry out many of the same steps described here as you tackle the issues set for your team for the 1st team coursework exercise.


## Introduction

In the team study sessions from week 2 onwards, you'll be working on your team coursework. The focus initially is on writing tests to make the issues your team has been asked to fix visible: that is, you will write tests that fail when the bug reported by the issue is present in the code base, and pass when it is not present.  The process is:


1. First, understand the bug by replicating it manually in your local copy of the game.
1. Check to see whether any existing tests fail because of the presence of the bug.
1. If not, you need to write a test that has this property.  Use the existing test suite as a source of inspiration and ideas for this.
1. Check that the test fails on the original version of the code base (i.e., it reveals the presence of the bug).
1. Figure out what is causing the bug and fix it in the production code.
1. Check that all the tests are now passing, including the one that reveals the presence of the bug.


## Manually Replicating The Issues  {#replicatingissues}

You will find the code base much easier to navigate, and the code relating to your issue much easier to find and understand, if you first replicate the issue manually.  This means running the game on your local server, to see the bug happening in the context of game play.  This will give you additional keywords for searching (to add to the keywords you can extract from the issue description itself) and will help you locate the relevant tests and the source of the bug.

This, however, raises a problem.  Some of the issues would require many hours of play to get a player character to the required level to be able to acquire the objects necessary and get to the NPCs involved in the issues.  You don't have that time to spare if you are going to get your fix tested and sorted in the timescales given for the coursework.

Following common practice, the Stendhal team have provided facilities for supporting targeted replication of issues through manual testing.  These facilities allow you to create a player character with ``admin`` status.  This gives the player special powers --- including the ability to teleport right to any NPC, to summon any item or creature, and to interrogate the internals of any item from within the game.

Information on these useful features can be found on the Stendhal wiki at:

[stendhalgame.org/wiki/Stendhal:Administration](https://stendhalgame.org/wiki/Stendhal:Administration)

Think carefully within your team about how you will use these admin features, and especially what test accounts you will use.  The admin accounts are specified through the contents of a file in the source code base, and therefore something that is potentially under version control.  You don't want to mess up your Git history by continually committing and changing everyone's favourite test accounts in this file.  A little coordination at the beginning can keep your Git history clean, while allowing everyone to be able to access at least one admin level player account.


<!--
##Starting from Green

You saw in a previous team study session that the code base already fails a couple of the test cases, even before you start making any changes to the code.  This is very typical in real systems.  It is common for test cases to be present in the test suite that fail.  These may reveal bugs that it is not worthwhile at this time to fix, or that no one has yet got around to fixing.  Or they may be surprise regressions from a previous change that the development team have judged to be of lower priority than the implementation of the new features currently under way.  Or, as we have discussed, these failing tests might be brittle: they are failing because of some change in the environment and not due to any problems in the code base itself.

But what do we do about these tests?  For your coursework, you need to make sure you have a clean release build: all the code must compile and all the tests must pass.  These existing failing tests are going to get in the way of making that happen.

You could find the problem that causes the bugs and fix them.  But that could take time your team does not have.  These bugs are not on your priority list.  Your boss won't be pleased to find you have spent your time on an unimportant bug while the important ones go unfixed.

Best practice for failing tests that we don't have the resources to deal with right now is to ``quarantine'' them.  That means to label the tests in such a way that they can be easily switched on or off.  We will turn them off for now, but at regular intervals will turn them back on again, to see if they are still failing.

A variety of quarantining methods exist, but none are perfect.  The Stendhal team have adopted a very common but very imperfect approach to other such tests: they have used the `@Ignore` annotation to tell JUnit not to run these tests (i.e. to skip them).  You can see from the JUnit results that 9 tests have been ignored in the full test suite so far.  This is clearly a technique that the Stendhal team use sparingly (and rightly so).

We suggest you follow the current practice of the Stendhal team, and @Ignore any of the tests from the original test suite that are failing, provided you are confident that they are not caused by any of the issues your team has been assigned to fix.

You will want to discuss with your team how you will make the commits with these @Ignore annotations in your repository.  How can you make the commits visible to all team members, so that they are included in their feature branches where they are working on their own issues?

Try to avoid the mistake that some teams made in previous years, where several team members made the change in their feature branches, and then experienced conflicts when they merged the work together.  The result was a lot of commits adding and then removing the `@Ignore` annotations, across several branches.  How can you coordinate with your team work so that these annotations are added once, in one clean commit, and then are available for all team members when they begin work on their own issues?-->

## Getting Inspiration for Writing your Own Test Cases {#inspiration}


Most people find writing test cases for bugs in large unfamiliar code bases very challenging. This is normal and to be expected.  Writing test code is quite a different style of coding than most of you will be accustomed to, and you are working blind, since you don't have much existing experience of working with this particular code.  The idea of the first team coursework exercise is for you to get experience in writing fairly simple tests.  It will be difficult at first, but remember that we are on hand to give help whenever you need it.  Don't sit stewing in silence because you don't know what you are doing.  Just ask!

A major source of inspiration for your test cases is the existing test suite.  A good starting point for writing your own test case is to look through the code base for test cases that are similar to the one you want to write.  

In some cases, you may find that test cases already exist for the piece of functionality you are working on, and you just need to add some additional cases to cover the specific functionality affected by the bug you are solving.  That is the easiest case.  If there is no test at all for you to work from, you can look at similar tests for ideas.  For example, if you need to write a test that checks the properties of an object, you can look for other tests on the ``Item`` class and get ideas from those.  Or, if you are writing a test for a quest, then you can look at tests for other similar quests, to get an idea of how these tests are structured, and what testing utility code the Stendhal team have provided to help you get started quickly.

Sometimes you might need to put ideas together from two different places to write the test you need.  For example, if you are dealing with an issue that describes an error in how pets are affected by stings from poisonous creatures, you might look for tests that deal with poisoning of player characters, and tests that deal with the health of pets.  Putting the ideas from these two tests together helps you write the new test you need.  You can also look at the production code for ideas when working with functionality that is not well covered by tests.

Existing test cases will also give you lots of useful tips on where to locate your new test code, whether in an existing test class or whether you need to create a brand new test class for your issue.

You should not feel embarrassed about copying and pasting existing test code and modifying it to fit your own issue.  This is a normal survival technique for software engineers in the wild.  Do make sure though that you understand the code you have copied, at least at a high level.  Don't leave bits of code in there when you are not sure what they are for.  That will just lead to brittle and slow tests.

Of course, since this is a coursework exercise, you *should* feel embarrassed about copying and pasting solutions written by the members of other teams for your issues. That would be plagiarism. Just use your own version of the Stendhal code base, and the work of your team members, to build your own tests on.
