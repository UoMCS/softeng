# Team Coursework 1: Dealing with Small Scale Code Changes {#dealing}
## Coursework Lead: Tom Carroll

## Key Information
### Key Dates
- Date of Release: 2022-10-03
- Submission Deadline:  <span style="color:red">**2022-10-28 18:00**</span> 
- Final Grades and Feedback to be released on or before: 2022-11-18 *(within 15 University working days of the submission deadline)* 


### Deliverables
Deliverables for this exercise are held within your team's GitLab repository, except for the video file containing your demonstration and reflection:

- Selected Bugs
- Correct use of Git (including Branching)
- Correct use of Code Review (along with proper coder response)
- Correct use of time estimation and other planning tools
- Correct use of Git Tags for the Test First Development
- Tests which make your selected bugs visible
- Source code of your bug fixes
- URL of Video Demonstration. You will upload actual video to the University Video server.

You *must* familiarise yourself with the submission instructions, in order to submit your work in the proper way. 

**Work which is not submitted in the correct way will receive a mark of 0.** 

### Penalty Details

There are several penalties that may be incurred, key details of which are below, along with links to further information. It is very important that you familarise yourself with these.


 1. Non-Contributing Member [Individual mark of 0]
 1. Incorrect email address used for Git Commit Author Details [Individual mark of 0]
 1. Partially contributing team member. [Individual mark of 50% that of the group mark]
 1. Team member not participating in the video demonstration [Individual mark of 50% that of the group mark]
## Overview

For this first team coursework exercise, your team has been provided with a Git repository hosted on the Department's GitLab server.  This repository contains a modified version version of the Stendhal code base.  Once the coursework begins, the issue tracker of this repository will be populated with a number of issues describing “bugs” in the code that your team must fix by the coursework deadline.

We are not just asking you to fix the bugs.  We are asking you to work like a professional software development team.  You must ensure that all the issues you are fixing are covered by unit tests before you fix them, and you must use feature branches to protect the work of other team members from any mistakes you might introduce while working on your issue.  You must keep a close eye on the quality of your development branches and release branches (with the help of a continuous integration server), and  you should use basic Git techniques to ensure that only code changes that compile and pass the unit tests reach the released code.

Your team must then prepare a new release of the Stendhal code, correctly documenting all the changes you have implemented.

Finally, your team is required to produce a video which demonstrates your work and reflects on the exercise.

The exercise will test your ability to:

* make use of a simple Git workflow, based on feature branches, to allow multiple coders to work safely on a code base at the same time,
* use an automated test suite to make code changes to a large body of code without causing regression,
* write new tests to make bugs visible before you fix them,
* use code reading techniques to locate the parts of a large software system that are relevant to a particular ug,
* prepare a good quality release incorporating the work of multiple developers, and  
* present a professional demonstration of the work you have done, and reflect upon your team processes and how they can be improved.


## What You Have to Do

### Step 1: Get It, Build It, Test It {#stepone}

Following the same process covered in the workshops, each team member should acquire their own local copy of the team repository, learn how to build and test it, and run the code as a locally hosted version of the game.  Instructions for doing this are in chapter \@ref(guiding).


### Step 2: Assign the Issues {#steptwo}
There are a number of issues to the project's issue tracker, each of which will describe a bug or problem with the code base that you are asked to fix. 

Issues are broken into two categories; Category A and Category B:



| **Categoty A**                                   | **Category B**                                   |
|--------------------------------------------------|--------------------------------------------------|
| - Haunchy doesn't accept charcoal <br/> - Lieutenant Drilenun suggests that a better weapon that 'rod of the GM' exists <br/> - Sheep pet prevents travel between zones <br/> - Typo in Fish soup for Hughie <br/> - Why does he ignore "horse hair"? |- Allow players to choose what masks they get from Fidorea <br/> - Coralia should have option to accept everything <br/> - Cheating on Zekiel's Practical Test |


For each issue in this list, perform a minimal examination of the code base and decide as a team who will be responsible for fixing each bug.  

You  now need to use the issue tracker to assign each bug to the decided responsible person;  **every member of the team must be assigned as the responsible person for one issue.**

If your team has the same number of members as there are issues, then you should plan to fix all the issues.  

If your team has fewer members than issues:
- you must select which issues to fix, with  **at least one issue from Category B**
- leave any unselected issues unassigned, and remove them from the Coursework 1 Release milestone in your issue tracker.  The automated marking system will mark only those issues that are associated with the milestone at the deadline.

::: {.rmdnote}

(ref:infobox)

**Bugs vs Features**

Every year, this exercise raises questions from students who are concerned that their assigned “bug” isn't really a bug.

What is a software bug?  The most widely accepted definition is that a bug occurs when the implemented behaviour of a system deviates from its specification.  This contrasts with a feature, which is defined as new behaviour needed of the system, that is not currently described in the specification.

This sounds very clear and reasonable in theory.  But in practice, the situation is complicated by the fact that most systems don't have a written specification.  Any specification that does exist is largely a collection of ideas and recollections in the heads of the people responsible for deciding what the system should do.  Whether a particular software change is a bug or a feature is therefore in the eye of the beholder, and there is very little to be gained from trying to argue one way or the other.

The “bugs” we have set for this exercise are all either actual bugs from the Stendhal project issue tracker, variations on reported bugs from the issue tracker or bugs that we have invented that are closely analogous to the kinds of bugs being reported by users of the game.

Unfortunately, many of the bugs reported on the Stendhal issue tracker are too complex, and too difficult to write tests for, to be suitable for a beginning coursework exercise like this one.  But we have tried to retain the form and spirit of “real” bugs in the issues we have assigned for the coursework.  This also means that they are at a range of difficulty levels.  If you were lucky/unlucky enough to be assigned an easy bug, consider pairing with someone else on your team who might be struggling with a harder one.  You can't do the work for them, but you can be a sounding board, and can help with exploring the code base to find the relevant parts of the code.

:::


### Step 3: Time Estimation {#stepthree}

Each team member should make an estimate of how long it will take to fix the bug they are responsible for.  This estimate should be recorded using GitLab's Time Tracking facility.  Information about how to do this can be found at:

[gitlab.cs.man.ac.uk/help/workflow/time_tracking.md](https://gitlab.cs.man.ac.uk/help/workflow/time_tracking.md)

At this stage, it is not important that your estimate is correct.  What is most important is that you make an attempt at estimating before starting to write code for the fix.

You should also set a Due Date for each issue in the issue tracker.  This should be the date when the work on this individual issue should be completed by.  Note that this *should not* be the deadline for the coursework.  You need to complete your individual work on the issue in time to merge the work into the development branch and for the new release to be created.


### Step 4: Set Up Branches {#stepfour}

You must use separate feature branches for each issue, to protect your team mates from being affected by your changes until they are complete, quality checked and ready for use.  The next step, therefore, is to set up the branch for the issue you are responsible for fixing.

The branch names to use are as follows:

| **Bug**                                   | **Branch Name**                                   |
|--------------------------------------------------|--------------------------------------------------|
|Haunchy doesn't accept charcoal| haunchys_charcoal <br/>
Lieutenant Drilenun suggests that a better weapon that 'rod of the GM' exists| lieutenant_drilenum<br/> 
Sheep pet prevents travel between zones | pets_prevent_movement<br/>
Typo in Fish soup for Hughie | fish_soup<br/> 
Why does he ignore "horse hair"? | bows_for_ouchit<br/> 
Allow players to choose what masks they get from Fidorea| not_random_masks <br/>
Coralia should have option to accept everything | everything_for_coralia<br/> 
Cheating on Zekiel's Practical Test | zekiels_test


 

You must create each feature branch starting from the development branch of your team repository.  You must not create it as a branch off some other feature branch, for example.


**Failure to use the exact names specified will mean that the marking system is unable to find and award marks for your work.**

### Step 5: Write Tests to Make Your Bug Visible {#stepfive}

Before getting started on the fixes, each team member must ensure that the bug they are responsible for is visible in the test suite (the code under the `test` folder).  That means that the presence of the bug must be flagged up by at least one failing test.  To do this, you may need to modify an existing test to make the unwanted game behaviour visible or (if the behaviour containing the bug is not currently tested at all) you'll need to create a new test class from scratch.  It is important that you locate any new test cases sensibly in the Stendhal code base, so that other developers familiar with the organisation of the code will be able to find it easily.  You'll also need to work out how to use the test objects that the Stendhal team have provided, to set up the a game (or partial game) in the state needed to make the issue visible.

**You should keep track of how long you spend on this step, to the nearest hour.**  (Note this is the actual number of hours spent on the task, not the elapsed time between when you started on it and when you finished it.)  

When the step is completed, add a **comment to your issue** telling us how long this was.  Please use the following phrase, which will be searched for by RoboTA 🤖 the automated marking system:

```md
    Issue now visible in the test suite.
    /spend <time spent>
```

where `<time spent>` is replaced with the amount of time you spent on this task, expressed in a form that the GitLab issue time tracking facility can understand, as per instructions here: [gitlab.cs.man.ac.uk/help/workflow/time_tracking.md](https://gitlab.cs.man.ac.uk/help/workflow/time_tracking.md).

Capturing this fine-grained level of time tracking data is not a usual part of a software process.  We ask you to do it for this exercise so that you can gain an idea of how long these kinds of tasks take you personally.  This will help you in the future in creating defensible and realistic estimates for your work.


### Step 6: Design and Implement Your Bug Fix {#stepsix}

Once you have one or more tests that fail because of the presence of the bug, you can make changes to the production code (the code under the `src` folder) to fix it.  

This step can be considered complete when the changes you have made in steps five and six are committed to your feature branch, and when the following conditions are all true when the feature branch is checked out:

* All the tests you wrote/modified to make the bug visible pass.
* No other tests in the Stendhal test suite fail.

**As in step 5, you should keep track of how long you spend on this step, to the nearest hour.**  When the step is completed, add a comment to your issue recording this.  Please use the following phrase, which will be searched for by the automated marking system:

```md
    Issue resolved.
    /spend <time spent>
```

where `<time spent>` is replaced with the amount of time you spent on this task, expressed in a form  that the GitLab issue time tracking facility can understand, as per instructions here: [gitlab.cs.man.ac.uk/help/workflow/time_tracking.md](https://gitlab.cs.man.ac.uk/help/workflow/time_tracking.md).


You may push your feature branch to your team repository at any point during steps 5 and 6, to make your progress visible to your team and to preserve a record of it on the Department GitLab server.  You do not have to wait until the issue is completely fixed.

Once you have pushed your feature branch to your team's remote, the continuous integration server will run the automated build and test processes, to determine the health of the code on your branch.


### Step 7: Merge with Your Team's Development Branch {#stepseven}

The next step is to merge your work with the development branch.  The Stendhal team use the `master` branch as their development branch, and we ask you to continue to follow this convention in this coursework^[If you are familiar with the popular GitFlow workflow for collaborative coding with Git, you may be surprised at this, because in that workflow `master` is used as the branch that records the stable, integration version of the code for release (sometimes called the *production branch*), while development is done on a branch called `develop`.  In fact, in many common workflows, including Github Flow and Trunk-Based Development, `master` is used as the name of the development branch.  So the Stendhal team are in good company here.] For this coursework exercise, we ask you to perform merges in your local repository and push them to the team repository.  In later exercises, we will make use of Merge Requests on GitLab to help you manage the merging process, but for this exercise you should **not** create any merge requests (there is a mark penalty for doing so).  Your goal for this coursework exercise is to demonstrate that you understand the basics of merging, by carrying out the steps yourself.  When you have demonstrated that, we will move on to using merge requests.

Before merging your work into the development branch on your team's repository, you need to check that your code changes are not going to introduce any unexpected problems.  To do this, first, **fetch any changes from your team's repository**, and merge them into your local repository, to make sure you are working from the most up-to-date version of the code base.  (If your whole team is following the workflow correctly, this step should be trivial.

A team activity taking you through this process will be covered in the team study sessions.

Next, check out the `master` branch and merge your feature branch into it (following the same approach we covered in the GitLab Access Check activity).

**Do not push the `master` branch to your team's remote repository at this stage.**  (You may, of course, push the feature branch.)

Check that the code base that results from this merge compiles, and that the full test suite passes.  If you encounter any problems, you'll need to reset the `master` branch back to the commit it was on before the merge.  This will have the effect of undoing the merge you just made.

Fix the problem in your feature branch and start this step again.  (Of course, if the problem turns out to be caused by code one of your team members has committed to your team repository, you'll need to stop development and work with that team member to fix their feature branch and re-merge it, before coming back to start this step again for your own feature branch.)

Once you are confident you have a clean merge, you can push the changes to the `master` branch to your team repository.  (You may wish to fetch commits from your team repository again before doing this, if a certain amount of time has elapsed since you started work on this step.)

If, at this point, you get a clean development branch build from the continuous integration server **and** the bug cannot be replicated when the game is run from the development branch, you can close the issue in the issue tracker.


### Step 8: Push to your Team's Development Branch {#stepeight}

As in steps 5 and 6, you should keep track of how long you spend on this step, to the nearest hour.  When the step is completed, add a comment to your issue telling us this.  Please use the following phrase, which will be searched for by the automated marking system:


```md
    Feature branch merged into development branch.
    /spend <time spent>
```

where `<time spent>` is replaced with the amount of time you spent on this task, expressed in a form  that the GitLab issue time tracking facility can understand, as per instructions here: [gitlab.cs.man.ac.uk/help/workflow/time_tracking.md](https://gitlab.cs.man.ac.uk/help/workflow/time_tracking.md).

::: {.rmdcaution}

(ref:cautionbox)

  **Do not push broken code to your team's development branch**

If, by the deadline, you have a feature branch that contains compile errors or has failing tests, you should push it to the team repository for marking, but you should **not** merge it with your development branch.  Your team will get more marks for not merging broken code than you will get for allowing broken code to reach the development branch or release tags.

Leave issues for unmerged feature branches open.  The team needs to know that this issue has not yet been fixed, so they can return to it in a future release should customer interest in fixing it become pressing.


:::

Note that it is your team's collective responsibility to ensure that the status of issues in your issue tracker accurately reflects the state of the code base.  If a team mate has marked an issue as completed, but you notice that the tests are failing for the merge, you should reopen the issue, giving a description of the problem as a comment in the issue.  Similarly, if a team mate has fixed a bug but forgotten to close the issue, you can check with them and close the issue for them.


### Step 9: Prepare The Release {#stepnine}

The final technical step is to prepare the release.  Although several team members may contribute commits for this process, a single team member should take responsibility for carrying it out.  This team member should create an issue for this task called:

```md
    Prepare release 1.40uom
```

This issue should be associated with the coursework 1 milestone, and assigned to whichever team member is taking responsibility for carrying out the release task.

Choose the commit on the development branch which will form the basis for the release.  This commit should include all the changes for the issues that have been correctly fixed by the team during the coursework and have been merged successfully with the development branch.  These are the issues that will be included in the release.

If we look at the previous releases created by the Stendhal team, we notice that a number of changes are made in each case.  Notably:

* The version number of the software is updated in the `build.ant.properties` file (and the change is propagated to other relevant files, through the build process - you should check this manually, to be sure).
* Any new authors are added to the `doc/AUTHORS.txt` file
* A description of the changes included in the release is added to the `doc/CHANGES.txt` file.

You will need to make these changes for your release too.  You can add them directly to the development branch (or you can use a release branch^[A release branch is just like a feature branch, except that it is created in order to manage the process of preparing a code base for release and to prevent that work from interfering with work on features for upcoming releases.] and merge with the development branch when complete, if you wish).

When you have created a commit that contains all the code and documentation you want to release, you should mark this by adding a *tag* at that commit.  The tag **must** be called:

```md
    VERSION_01_RELEASE_40_UOM
```

This is the version of the code that we will consider to be your released code, when we are marking.  So, it is important that you place it at the right place.  You can create the tag locally and push it, or you can use the GitLab web interface to create the tag once the final release commit has been pushed.


### Step 10: Prepare Your Video {#stepten}

You are now done with the technical work. Now you must create your video demonstration.  

In your video, you must demonstrate **two issues**, with **at least one issue being from Category B**:

| **Categoty A**                                   | **Category B**                                   |
|--------------------------------------------------|--------------------------------------------------|
| - Haunchy doesn't accept charcoal <br/> - Lieutenant Drilenun suggests that a better weapon that 'rod of the GM' exists <br/> - Sheep pet prevents travel between zones <br/> - Typo in Fish soup for Hughie <br/> - Why does he ignore "horse hair"? |- Allow players to choose what masks they get from Fidorea <br/> - Coralia should have option to accept everything <br/> - Cheating on Zekiel's Practical Test |


**If there is no issue present from Category B, then you will only receive credit for one of the issue demonstrations**.

You must also reflect on your work as a team, looking forwards to tasks such as Team Coursework 2.

The video must follow the format given below:

- The video must begin with video footage of each team member introducing themself and describing, very briefly, their role in the team. 
-  For each of the two issues selected, the person who had responsibility for this issue must:
    - Explain the issue
    - Show in-game footage, with narrated explanations, confirming that the issue is fixed
    - Show and explain test code used to expose the issue in the test suite
    - Show and explain code used to fix the issue
- Discuss how you organised your workload across the team
- Discuss what monitoring steps you've taken to keep the work of the team on track for the deadline.
- Reflect on the team exerise; what went well? What will you take forwards into the next team exercise? What will you do better next time?

To create your video, you might find the following software useful (these are only suggestions and shold not be taken as a requirement or endorsement to use them):
- OBS  (For screen recording)
- Shotcut (For very basic video editing: there is a low barrier-of-entry here, when compared to other video editing software)
- Powerpoint / Libre Office Impress / Keynote (for creating slides)
- Zoom (for creating a video meeting and recording to allow all team members to speak)


Note that **all team members must make a non-trivial appearance in the video**. 

**Any team member who does not appear in the video, and has not registered a legitimate reason with SSO or a member of the course team, will receive an automatic 50% penalty on their mark for the exercise.**  Team members who appear in the video will be unaffected by this penalty.


Your video **must not exceed 15 mins in length**. In cases where a video is longer than 15 minutes, the video will be **stopped** at 15 minutes; any content after this point will not be considered for your mark.

## Submission of Your Team's Work {#imdone}
Your submission is in two parts: your video file and the GitLab repository.

### Submission of Video
Once you have prepared your video, one of your team should upload it to the University's Video Server: https://video.manchester.ac.uk/ .

The URL of your uploaded video must be placed in the follwing text file (which you must  create) on your GitLab repository: `doc/VIDEO_URL_1.txt`

You must tag the commit with this file as `VIDEO_1`.

### Submission of GitLab Repository

The remaining submission of work for this coursework exercise is through your team's GitLab repository.  All you have to do is make sure the contents of your issue tracker and Git repository are ready to be marked by the deadline.  There is nothing else you have to submit.
Once the deadline is passed, you will temporarily lose developer role access to the repository and won't be able to make further changes to the code or commit graph. 

## Getting Feedback{#feeeback}

A “live” marking scheme for the exercise can be found on the CI server used for this course unit.  (You will get information about this some days after the coursework is released to you.)  The marking scheme gives details of how the marks will be awarded, but also gives an interim mark for your team based on the work completed so far.  Of course, only some parts of the marking can be automated.  Others will need to be done by GTAs.  The GTA marking takes three forms:

1. Pre-deadline annotation of commits.  Each week, your assigned GTA will look at your commits and add annotations to tell the automated marking code which parts of the exercise each commit contributes to.  You should take note of these annotations and let your GTA know if you believe the annotation is incorrect.
1. Post-deadline marking of your team process and the changes you have made to the code base.
1. Marking based on your video demonstration and reflection.

Once the deadline is passed, you will temporarily lose developer role access to the repository and won't be able to make further changes to the code or commit graph.  At this point, we will clone your team repository and the automated marking process will finalise as many of the marks as it can.  When the GTAs have completed the remaining marking process, the marks will be uploaded to Jenkins and your final mark plus feedback will be visible in your team's RoboTA build.

You'll get developer access back once the next coursework exercise begins.


## Coursework Extensions {#cwkex}

Since this coursework is a team exercise, no extensions will be given, and there is no option to submit your work late.  Team members who experience substantial difficulties in completing their work due to illness or other legitimate reasons will need to complete a Mitigating Circumstances form so that this can be taken into account later.  The marking process is sufficiently flexible to take into account non-contributing team members without significantly affecting the team mark for other members.

If you are not going to be able to carry out the work for your issue by the deadline set for your team, you **must** inform the other team members in plenty of time.  This will allow them to make decisions about what to include in the release, so as not to be penalised for the work you have not been able to do.


## Non-Contributing Team Members {#passengers}

Every team member is expected to contribute some meaningful code to the team's repository.  You should declare the work you intend to deliver as you contribution by assigning an issue to yourself in the issue tracker.  Commits on feature branches should be made by the team member recorded as responsible for the commit in the issue tracker.

A meaningful commit is one that contributes code changes to either test or production code that moves the team's repository closer to the fix for an issue in some way.  Adding white space, rewording comments or moving lines about are all examples of code changes that will not be considered to represent a meaningful contribution to the exercise.  Similarly, a merge commit is not by itself considered to be a contribution to the solution.


::: {.rmdcaution}

(ref:cautionbox)

Any student who has no assigned work in the issue tracker or who has not made at least one meaningful commit to their team repository, from their Department GitLab account, during the period covered by the exercise, will automatically receive a mark of 0 for the whole exercise.

This applies even if you decide to work in pairs on the issues.  Sitting and watching someone else make a commit, even if you are telling them what to type, does not count as a commit from you.  The commit must be made from your own GitLab account.

:::

If a team includes non-contributing members, the marking scheme will be adjusted to take this into account.  This means it is not necessary for contributing team members to pick up additional work, to fix issues that have been assigned to non-contributing members.  Instead, everyone should concentrate on fixing their own issue, and on including it safely into the release.  The team mark will be adjusted to take into account issues not fixed by team members who are non-contributing.


## Partially Contributing Team Members {#freeriders}

If a team member contributes something, but does much less than others or contributes their work in a way that causes problems for the rest of the team, the team as a whole can choose to reduce the mark of that student.  For this to happen, you must:

* Send an e-mail to the student as soon as the problem is noticed, pointing out the difficulties they are causing for the team, and asking them to say what they can do to resolve matters.  CC this e-mail to Anas or Duncan, so we have a formal record of the communication.
* Set a deadline for the team's work that is sufficiently far ahead of the actual deadline, so you have time to chase people who don't deliver.
* Before the team interview, send an e-mail to Anas/Duncan *and* the offending team member letting them know that the team will propose a reduced mark for them at the interview.
* At the interview, raise the issue with the TA, who will document the circumstances on your marking form, along with details of the proposed mark reduction.  If the affected team member agrees, the proposed reduction will be applied at that point.
* If team agreement on the mark reduction cannot be reached, the whole team will need to meet with Anas or Duncan to agree a way forward.

Note that this process is not necessary for team members who have not assigned themselves any issues or made any commits in your team repository, as they will automatically receive a mark of 0 in this case.

Mark reductions apply to individual team members only.  There is no effect on the mark of the rest of the team.  Teams are asked to try to resolve problems within the team if possible, before making mark reductions, but this option is there as a measure of last resort for those teams who need it.


## Plagiarism {#copycats}

This coursework is subject to the University's policies on plagiarism.  Details can be found on the School web pages at:

[studentnet.cs.manchester.ac.uk/assessment/plagiarism.php?view=ug](http://studentnet.cs.manchester.ac.uk/assessment/plagiarism.php?view=ug)

Note that committing the work of other people from your GitLab account counts as plagiarism, and action will be taken when it is detected.


`Document version:` `r format(Sys.time(), '%d %B, %Y')`
