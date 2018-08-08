# Web-Products--QA-Docs

*QA- INDUCTION KIT*



CONTENTS
1.	SPRINT PLANNING AND GROOMING
2.	TEST DESIGN
3.	READY FOR QA & BUILD PR
4.	PR TESTS
5.	QA on the PR
6.	BUGS
7.	QA REPORTING
8.	RELEASE



The QA at the Economist is predominantly achieved through manual testing. There are road maps to shift towards automation in the days to come. 

Currently, the QA Practise at The Economist, is working on the following 4 tribes and will be spreading across the other tribes, eventually.
1.	Subs - DISCO
2.	Subs - AMP
3.	Non Subs - ECNON
4.	Non Subs - Canonical



I.	SPRINT PLANNING AND GROOMING

The QA is expected to make good use of the Planning and the Grooming session by being:
●	Vocal and responsible. 
●	Flagging the tickets that doesn’t have the acceptance criteria and ensuring to getting it pinned down. 
●	If a particular ticket doesn’t require QA, ensuring that is highlighted in the ticket. 
●	Providing the estimates for the ticket in QA perspective. 
https://docs.google.com/document/d/14ukhZyolVvB1ns3ECwq3tI9pb-seSpwir6vYnqLDgnU/edit?usp=sharing
This link details the journey of a ticket from ‘Ready for QA’ status to ‘Released to Production’ status. This will provide a fair idea on how to estimate a ticket. 
●	Understanding the priorities and delivery dates. 
●	Understanding the dependencies. 
●	Clarifying any ambiguities. 

II.	TEST DESIGN

During the course of the Sprint Planning, the QA is expected to be proactive and should figure out the ‘Test Acceptance Criteria’ as early as possible. 

The following will be prerequisite to pin down the TAC credibly: 
-	The Business Acceptance Criteria is pinned down and is clear and comprehensive.
-	The Designs are ready.

The Test Acceptance Criteria is usually captured in the BDD format:
GIVEN WHEN THEN

 III.	READY FOR QA & BUILD PR

As and when the code is ‘Developed’, ‘Peer Reviewed’ and ‘Core Approved’, it is changed to “Ready for QA” status and assigned to the QA personnel both in the Github and JIRA. 

1)	JIRA: The Developer changes the status of the ticket to “Ready for QA’
	 

2)	JIRA: If a tribe doesn’t have a dedicated QA, then the ticket will be left unassigned, as and when it gets ready. And it is the responsibility of the QAs to assign themselves to the ticket as and when they become available. 
	 

3)	JIRA: Change the status of the ticket to “IN QA” and assign yourself. 
4)	JIRA: The PR for this ticket will be ready, which will be indicated by the “OPEN” label. 
	 


5)	JIRA: The click on the ‘Pull Request’ will show this pop-up: The number under the “ID” is the PR number. In the below case 2047 is the PR ID. 
	 


6)	GITHUB: And a click on either the ‘ID’ or “Title” will be redirected into the Github, where the PR is committed. 

7)	GITHUB: The QA should ensure that the PR is Ready, by checking the following:
Core Review, Approval, Branch Conflicts. There should be nothing in Red. All should 
Be in GREEN. If not, it should be informed to the respective Developer, and should 
Sorted out, before progressing. 
 
8)	GITHUB: If the checks are green, the QA is ready to “BUILD THE PR”. In order to build the PR, the QA should do the following check: 

9)	GITHUB: → Pull requests→ Will navigate to the following page:

10)	GITHUB: Under the “Labels” filter by “BUILDPR”

11)	GITHUB:
	The filter on BUILDPR will show the number of PRs holding the BUILDPR label. 
	 
12)	GITHUB: In the current capacity, there can only be 8 PRs built at the maximum. In the above example, there are already 7 PRs. So, the QA can go ahead and build her/his PR. 
	However, if there are 8 PRs in the queue, the QA should wait, till one of the slot 
Becomes available. 
In emergency/high priority situations, the QA can talk to one of the PR owners to 
Remove the BUILDPR to progress. But, should never BUILD a new PR if the queue 
Is full, which is 8. 
	         
13)	GITHUB: If the BUILDPR queue has the slot, and QA should navigate back to their respective PR and add the label BUILDPR
	 
14)	GITHUB: Adding this BUILDPR Label in the Github is MANDATORY. Skipping this, will not build the PR. Hence the QA should sensitize on this activity. 
15)	GITHUB: Once the label is added, the QA is advised to refresh the page and double check if the BUILDPR label is added successfully. 
16)	JENKINS: Now, the QA has to navigate to JENKINS → http://jenkins.p.aws.economist.com:8080/


17)	JENKINS: This is where the PR will be built: http://jenkins.p.aws.economist.com:8080/view/fe-blogs/job/STAGE_PR_fe-blogs-pr-build/
	 
18)	JENKINS: Provide the PR ID  and click on BUILD.
19)	JENKINS: The PR BUILD Progress can be monitored on the same page. 
20)	JENKINS: If the BUILD fails or if the QA wants to look through it → Click on the BUILD No under BUILD HISTORY, which will redirect to the below page. Click on “CONSOLE OUTPUT” to troubleshoot or walkthrough. 
	 
21)	JENKINS: Once the BUILD is built successfully, the Build No will reflect in GREEN under Build History. If not in RED. 
22)	JENKINS: If RED, try to build it one more time. If it fails again, contact the respective developer. 
23)	JENKINS: If Green, then the BUILD is successfully and the QA is ready to run the PR Tests. 
24)	SLACK: There will be success/failure message that will be updated in the rvmp-development slack channel, based on the outcome of the Build. 


IV.	PR TESTS


PR Test is an automation regression suite that is run against every new PR that is being built. This should be done before the actual QA for that PR.
1.	JENKINS: Once the BUILD is built successfully, navigate to http://jenkins.p.aws.economist.com:8080/view/fe-blogs/job/fe-blogs-pr-tests/ → Build with Parameters→ Uncheck ‘Avoid Safari’ → Provide the PR number in “PR_ID” → and click on ‘BUILD’
	 
2.	JENKINS: If the PR Test fails, it reflects in RED. If passed, it reflects in GREN. 
3.	JENKINS: If the PR Test fails, navigate to the BUILD, and click on ‘CONSOLE’ to understand the error message.
4.	SLACK: The slack channel rvmp_development will be updated with both the success and failure outcomes. 
5.	If the PR Tests fails, it could be tried one more time. But if it continues to fail, it has to be notified to the respective developer. And if the fix would take more time, then the JIRA ticket should be updated to “In Progress”
6.	If the PR Tests passes without any issues, then the PR is ready for QA. 
7.	Ensure to take the screenshot of the success message displayed in the rvmp-development channel, as it has to be attached in the QA report. 

V.	QA on the PR:


1)	Now the BUILD is built successfully, the PR Tests has passed successfully, and hence the PR is ready for QA.
2)	Navigate to: https://stage.economist.com/?pullrequest=<PR#>&internalpreview=1
3)	It is advised to use https://stage.economist.com/?pullrequest=2032&internalpreview=1
	This is because, the internal preview will ensure to pull only the PR environment for 
	2032 and will not confuse with other PRs. 
4)	The QA for any ticket is usually performed on the following browsers:
a)	Web Browsers: Chrome, Firefox, Safari, Edge, IE
b)	Mobile Browsers: iOS(Chrome, Safari), Andrioid(Chrome)
5)	The QA is also advised to be performed on various dimensions, sizes, and pixels. The In-house QA team possess a wide range of devices for the usage of the same.
https://docs.google.com/spreadsheets/d/1zrAPDiylc4vgnRXx5R-nRD_ljzWhvdoGFLd3j3HlCYE/edit#gid=716380084

6)	If a particular device/dimension/size is not available, then it can be QAed using the Developer Tool.
	https://streamable.com/kodgo - This video shows how to use the Developer Tool in 
	Chrome. Similarly, this can be done for all the browsers. 
7)	As the Stories are usually light weight, QA for a single ticket is quite achievable in a stretch. 


VI.	BUGS:


1)	Issues found during the course of QA:
a)	Issues are usually shared with the Developer through slack and at times fixed momentarily. 
i)	The Developer fixes momentarily if it is a small fix. 
b)	Sometimes, a detailed report of the issues are made and updated in JIRA with all the evidences and assigned to the Developer to fix. 
i)	If reported, the Developer/PO comes back clarifying which are issues, which can be fixed, which cannot be fixed — based on which the QA will act. 
	The below is the sample example of an intermittent report updated 	with the issues observed. 
	 
2)	Bugs raised based on the fixing capacity:
a)	If a developer convinces that he doesn’t have the capacity to fix any of the issues within the release, then those are raised as a Bug. 
b)	However, the above decision by the developer, should be in sync with the consent of the Product Owner. 
c)	So the issues, that couldnt fixed within the releases are usually raised as a BUG. 
3)	RAISING A BUG:
a)	Bugs are raised in WPSD. This process defined by the Global Logic team is still followed in here.The reason to raise it via the WPSD is to be able to triage it (in the ds-triage channel) and identify the team to handle it - in more detail here:
b)	https://jira.economist.com/wiki/display/WP/Defect+reporting
c)	https://jira.economist.com/wiki/display/WP/Service+desk
d)	If the issue is spotted when doing QA of the story (and it is related to that story) we are clear it is something the particular WP subteam needs to handle. In this case we bypass WPSD and raise the ticket directly with that WP subteam

4)	Once the QA IS completed successfully and it had passed as expected, then a detailed report is submitted in the JIRA and assigned to the PO for review. 


VII.	QA REPORTING

1)	The QA Reporting should tabulate the following:
a)	The URL
b)	The Web Browsers
c)	The Mobile Browsers
d)	PR Tests (result, the number of times it is run)
e)	QA Status
f)	QA Sign Off Status
2)	The report should flag the failures following the tabulated details.
3)	The passed criteria should be listed below the failures. 
4)	It is advised to reduce screenshots and use the videos instead. 
5)	Videos can be uploaded into www.streamable.com and the link can be shared in JIRA for the evidences.
6)	The Slack screenshot for the PR Tests should be shared at the end.
7)	The final verdict on QA PASSED/QA FAILED/QA BLOCKED should be at the end.
8)	This report should be CCed to the Developer, Product Owner, Scrum Master and other relevant stakeholders. 
9)	With the detailed report, the ticket is assigned to the respective PRODUCT OWNER for PO Review.
10)	The PRODUCT OWNER approves the ticket if he/she is happy, else the discussion on their disapproval would go on. 
11)	And if the PRODUCT OWNER is happy, the ticket status is changed to “READY TO DEPLOY” and assigned to the QA responsible for the Release. 
12)	The QA proceeds with the Release. 
13)	Sample QA Report:
	 

VIII.	RELEASE

The Release Process is detailed in the below link: https://docs.google.com/document/d/1Jj3XLvAkW7DZ8H9gcpTE7LYWg-_uYTolUDYgYzvA9ws/edit?usp=sharing

