# Documentary Proof of the Execution of the Quality Assurance Measures

## Table of Contents
+ Issues `PLEASE HELP FIXING`
+ Introduction
+ Obviously Reached Quality Goals
+ Quality Goals Enforced by Code Reviews
+ Partially Reached or Missed Quality Goals

## ISSUES `PLEASE HELP FIXING`

+ Is the "userManagment" repo relevant for this document? Why is it not part of the back end repo?
+ There are many, many pull requests that cannot be associated with a user story! What to do with them? (`BF` stands for *bug fix*, `US` means that *there should be a user story for this pull request*, `?` indicates that I have no idea what this is.)
	+ Unassociated pull requests from the back end:
		+ \#2 `?`
		+ \#5 `BF`
		+ \#13 `BF`
		+ \#14 `BF`
		+ \#15 `?`
		+ \#18 `US` (Implement functionality triggered by routes for getting projects and canvases)
		+ \#19 `BF`
		+ \#21 `US` (Implement canvas deletion)
		+ \#22 `US` (Implement canvas creation)	
	+ Unassociated pull request from the front end:
		+ \#1 `BF`
		+ \#2 `?`
		+ \#3 `?`
		+ \#8 `?`
		+ \#9 `BF`
		+ \#17 `BF`
		+ \#19 `BF`
		+ \#22 `US` (Implement project view and canvas edit view)
		+ \#28 `BF`
		+ \#29 `US`/`BF`? (Increase canvas size when editing it)
		+ \#30 `US` (Add profile and edit profile views, some little tweaks)
		+ \#31 `US` (Implement canvas deletion)
		+ \#32 `BF`
		+ \#33 `US` (Implement canvas creation)
	+ __Please create an entry within the GitHub issue tracker for each pull request marked `BF`!__
	+ __Please create a user story and submit it to me for each pull request marked `US`!__
	+ __If you authored a `?` pull request, please explain to me what it does!__

## Introduction

At the very beginning of this project, we created a document ("Qualitätssicherungsdokument") that outlined certain quality goals which were to be met by the software as well as measures and practices for the developers to adhere to in order to reach these quality goals. Here is a __shortened__, check-list-style summary of these goals:

1. __Ease of Use__
	1. The user interface has to be visually consistent/coherent. Therefore, all UI elements must be part of Twitter's Bootstrap framework.
	2. Each feature has to be accessible with no more than three clicks.

2. __Functionality__
	1. Each feature has to be described in a user story before its being implemented. This way, possible misunderstandings with the client can be sorted out before one line of code is being written.
	2. Each user story comes with at least one so-called "acceptance test", which precisely (click-by-click) describes a scenario in which the new functionality is being applied. A user story may not be considered done until the test associated with it passed.
	3. Towards the end of the development, one or more "usability tests" (regarding the entire software) have to be conducted. A usability test consists of several questions to be answered by potential users of the software. The goal is to find out how satisfied they are with it and what they want to be done differently.

3. __Analyzability (or "Understandability of the Source Code")__
	1. Each source code change (addition, modification, or deletion) has to be associated with either a user story or a bug that is being tracked with the GitHub bug tracker. Therefore, all so-called "pull requests" have to come with either a user story id or a bug id.
	3. Each method has to come with a JavaDoc-style comment right above its signature that describes its what it does, its parameters, etc.

As the title suggests, it is the purpose of this document to either prove that these goals have been reached or document the reasons why some of them could not be realized. 

## Obviously Reached Quality Goals

However, whether certain quality goals have been reached or not is quite hard to "prove" as it is rather obvious if that is the case or not:

+ It is obvious that each feature has been described in a user story (__§2.1__) since everything that has been submitted to the repository through a pull request refers to at least one user story. This can easily be verified by checking out the descriptions of all the accepted ("merged") pull requests on GitHub. 
	+ There is one exeption to this, though. There are pull requests that do not contain a user story id but an issue id instead. An issue id refers to a bug that is being tracked with the GitHub issue tracker. This as well as the aforementioned reveals that quality goal __§3.1__ has also been reached.
+ Furthermore, as one can easily verify below, each user story comes with at least one acceptance test (__§2.2__).

## Quality Goals Enforced By Code Reviews

While the quality goals __§2.1__, __§2.2__, and __§3.1__ have "obviously" been reached, the implementaion of other quality goals had to be enforced in so-called "code reviews".

__How did these code reviews work?__ Whenever a developer wanted to submit any kind of source code change (addition, modification, or deletion), he (there were no women involved) issued a so called "pull request". Then, all the other developers had to review the code of the pull request and verify that it fulfilled the relevant quality goals. If so, the submitted code was being merged into the repository. If not, the developers discussed until the code was changed to live up to the expected standard. Then, it would also be merged. Insummary, there was one code review per pull request and that code review happened entirely on the GitHub platform.

__Which quality goals were relevant during the code reviews?__ The quality goals __§1.1__ (Visual consisency through Bootstrap), __§1.2__ (Accessibility of all features through three clicks at most), and __§3.3__ (Java-style comments of methods) were relevant during code reviews. However, the discussions during code reviews were not limited to that.

__How are code reviews being documented here?__ Each user story has been implemented by at least one pull request. For each pull request, there has been a code review. Below you can see all the user stories including the pull requests associated with them. Futhermore, each pull request itself comes with a short description and a transcript of its code review. (At first, we considered to only list all the pull requests of the project als well as transcripts of their code reviews, however, these would seem incoherent if not mentioned in the context of a user story. Therefore, we decided to not only list pull requests and transcripts of code reviews below but also all of the user stories.)

### User Story #1: Registration of User Accounts
+ __Velocity Points__: 10
+ __Description__: As a person, I want to be able to register an account on a Paperdreamer instance. I want to enter my user name, email address and password and confirm the data to register myself as a user. This user account is not functional until an administrator confirms it.
+ __Acceptance Test #1__: After registering as a user called "Test User" with the email address testuser@paperdreamer.org, one has to verify that the user account is created in the database, but logging in will fail until an administrator enables it.
+ __Implementation__:
	+ __Back end pull request #3: Server-side validation of registration data__
	+ __Back end pull request #4: User lists and activating users__
	+ __Front end pull request #4: Implement registration and notifications__
	+ __Front end pull request #7: Implement settings factory and refactor the registration__

### User Story #2: Changing User Account Passwords
+ __Velocity Points__: 10
+ __Description__: As a user, I want to be able to change the password that I use to log in to the Paperdreamer platform. For security purposes, I want to be forced to enter my current password twice before entering my desired password (twice, also). The next time I want to log in, I want to be able to do so using the new password.
+ __Acceptance Test #1__: Using the login credentials of "Test User", one has to log in to the Paperdreamer platform using the generated password. Then, one has to change "Test User"'s password like described above. If, afterwards, loggin in with the new password works, this test can be considered done.
+ __Implementation__:
	+ `TODO: NO MATCHING BACK END PULL REQUEST`
	+ __Front end pull request #7:  Implement settings factory and refactor the registration__ `?`

### User Story #3: Receiving an Email After Registration 
+ __Velocity Points__: 4
+ __Description__: After registering on a Paperdreamer instance, I will receive an email, where I need to confirm the entered data by clicking on a link. After this, the account will show up in the list of users for the administrator(s) to confirm.
+ __Acceptance Test #1__: After registering as a user, one has to verify the provided data by clicking on a link in a received email. After the link has been clicked by the newly registered user, this user needs to show up in the list of unconfirmed users (which can only be accessed by administrators).
+ __Implementation__:
	+ __Back end pull request #7: Mail service__


### User Story #4: Confirming User Accounts
+ __Velocity Points__: 6
+ __Description__: As an administrator, I want to be able to confirm user accounts. After registering as user, the account is not activated, until I (or another administrator) enables it, by choosing to reject or accept it.
+ __Acceptance Test #1__: After registering as a user, my account is disabled and I cannot login. One has to verify that after confirming the account as administrator, the new user can log in with the data he entered in the original registration process.
+ __Implementation__:
	+ __Back end pull request #4: User lists and activating users__
	+ __Front end pull request #5: Implement user stories #4, #5 and #6__


### User Story #5: List of Not Yet Activated Users
+ __Velocity Points__: 10
+ __Description__: As an administrator, I want to see a list of user accounts which I need to accept or reject.
+ __Acceptance Test #1__: After registering as a new user, I login as administrator and can open the list of unconfirmed users. One has to confirm that the new user shows up in the list.
+ __Implementation__:
	+ __Back end pull request #4: User lists and activating users__
	+ __Front end pull request #5: Implement user stories #4, #5 and #6__

### User Story #6: List of All Users
+ __Velocity Points__: 10
+ __Description__: As an administrator, I want to see a list of all users in the system.
Once I am logged in as administrator, I can open a view of all registered users. This view will show at least each user name and the associated permissions ("Administrator" or "User").
+ __Acceptance Test #1__: After creating a new user ("Test User"), I can login as administrator and open the user view. "Test User" will show up with the associated permission being "User".
+ __Implementation__:
	+ __Back end pull request #4: User lists and activating users__
	+ __Front end pull request #5: Implement user stories #4, #5 and #6__


### User Story #7: Promoting Users
+ __Velocity Points__: 8
+ __Description__: As an administrator, I want to be able to promote users to admins. Once I am logged in a user account with administrator privileges, I can open the user view, where I can change the permissions of each user. The following system wide permissions are supported: Administrator (not-deleteable, "God" mode), Administrator (deleteable) and User. Non-deletable administrators can only be promoted by another non-deleteable administrators, the same is true for changing the permissions of user from "Administrator" to "User".
+ __Acceptance Test #1__: After creating a new user ("Test User"), I can login as administrator and change his permissions to "Administrator". After logging out, I can login with "Test User" and change permissions as well.
+ __Acceptance Test #2__: After creating a new user ("Test User"), I can login as "God" administrator and change his permissions to "Administrator, non-deletable". After confirming my choice, deleting "Test User" is not possible.
+ __Implementation__:
	+ __Back end pull request #9: Add methods for changing user roles__
	+ __Front end pull request #13:  Make admin userlist roles dropdowns, add methods for changing roles to controller and factory__

### User Story #8: Profile View
+ __Velocity Points__: 7
+ __Description__: As a user, I want to be able to view my profile as well as other users' profiles. After I login to my account by clicking "View Your Profile" (or something similar), I want to be able to see my current profile information such as my avatar, user name, email address (and other personal information the user has provided). By clicking someone else's username I want to be able to view their profile.
+ __Acceptance Test #1__: After logging in as "Test User", I can go to my profile view by clicking "My Profile" from the navbar and other users' profiles from user list.
+ __Implementation__:
	+ __Back end pull request #20: Add backend methods for profile and edit profile view__
	+ `NO MATCHING FRONT END PULL REQUEST`

### User Story #9: Logging In
+ __Velocity Points__: 8
+ __Description__: As a user (which can also be an administrator), I want to be able to log in to the platform. Therefore I enter my credentials (user name or email and password) into a login form. The login button will be unclickable unless both fields are filled with information that fits the format. If, and only if, the provided credetials were correct, access is being granted after clicking the login button. Otherwise, there will be an error message popping up.
+ __Acceptance Test #1__: Try to log in with fictional credentials. There should be an error message saying that the provided credentials weren't accepted.
+ __Acceptance Test #2__: Try to log in without a password, the login button should be unclickable, though.
+ __Acceptance Test #3__: Log in with an existing user's credentials.
+ __Implementation__:
	+ __Back end pull request #6: Implement GET /user route__
	+ __Front end pull request #4: Implement registration and notifications__
	+ __Front end pull request #6: Implement login live validation__
	+ __Front end pull request #8: Implement user factory__

### User Story #10: Header Bar
+ __Velocity  Points__: 15
+ __Description__: As a user, I want to be able to switch between different views. I want to open a list of all public projects, a list of my projects and also my account settings from a header bar, which I can access on every page, as long as I'm logged in.
+ __Acceptance Test #1__: Before logging in, there is no header bar visible. Once I login as any user, a header view is shown with at least the entries "My Projects", "All Projects" and a link to my user account settings. Clicking on each link opens the page corresponding to it.
+ __Implementation__:
	+ __Front end pull request #10: Create a header bar for Paperdreamer__

### User Story #11, formerly #3.1: List of My Projects ("Dashboard")
+ __Velocity  Points__: 10
+ __Description__: As a user, I want to see a page containing a list of all projects that I am participating in. These projects should have an indicator that shows whether they are open. This page should be the first thing I see after logging in. This should also be my home page.
+ __Acceptance Test #1__: After creating a new project "Foo" and assigning user "Test User" to it I can login as "Test User" and see "Foo" on my dashboard and that it is open.
+ __Implementation__:
	+ __Back end pull request #11: Add project controller and methods for getting belonged and all projects, add new paths to index__
	+ `NO MATCHING FRONT END USER STORY`

### User Story #12, formerly #3.2: List of All Projects
+ __Velocity Points__: 8
+ __Description__: As a user, I want to be able to open a page where I can see all the projects on the platform, regardless of my membership and an indicator which shows whether they are open.
+ __Acceptance Test #1__: After creating a new project "Foo" and assigning user "Test User" to it, I can login as "Test User" or another user "Test User 2" and see "Foo" on the all projects view and that it is open.
+ __Implementation__:
	+ __Back end pull request #11: Add project controller and methods for getting belonged and all projects, add new paths to index__
	+ __Front end pull request #16: Add dashboard and all projects view, add factories and controllers for those__

### User Story #13, formerly #3.3: Creating Projects
+ __Velocity Points__: 10
+ __Description__: As an administrator, I want to be able to create new projects by giving it a name and a description, adding users for this project and assigning those users as Director, Supervisor or Artist.
+ __Acceptance Test #1__: After logging in as administrator "Test Admin", I can create a new Project "Dummy" and give it a description of "Dummy Project". I can assign user "Test User" to this project and make him the director of the project. I can then verify that this project is created in the database.
+ __Acceptance Test #2__: After logging in as "Test User", I can see "Dummy" on my dashboard, my all projects view and that it's open. I can then login as user "Test User 2" and see "Dummy" on my all projects view and that it's open but not on my dashboard.
+ __Implementation__:
	+ __Back end pull request #17: Add createProject route to flight and implement it__
	+ __Front end pull request #23: Add functionality to add new projects__
	+ __Front end pull request #27: Add autocomplete to create project page__

### User Story #14, formerly #3.4: Editing a Project's Meta Data
+ __Velocity Points__: 7
+ __Description__: As an administrator, I want to be able to change the meta data of an existing project like changing its name, its users, roles of users.
+ __Acceptance Test #1__: After logging in as administrator "Test Admin", I can edit the project "Dummy" by changing its name to "Foo" and its description from "Dummy Project" to "Project Foo", by assigning user "Test User" as supervisor, by making the director "Test Director" an artist and by removing artist "Test Artist" from the project.
+ __Acceptance Test #2__: After logging in as "Test User", I can see "Foo" on my dashboard, all projects view and that it's open. I can login as "Test Director" and see the name change from "Dummy" to "Foo" on my dashboard and all projects view. I can then login as "Test Artist" and see the name change from "Dummy" to "Foo" on my all projects view but cannot see "Dummy" or "Foo" on my dashboard.
+ __Implementation__:
	+ __Back end pull request #16: Add new route /project to edit and delete projects to index.php, add methods to delete and edit (with actions of open and close) projects to project controller__
	+ __Back end pull request #28:  Add methods to update users of projects in backend__
	+ __Front end pull request #35:  Edit projects__

### User Story #15, formerly #3.5: Deleting Projects
+ __Velocity Points__: 5
+ __Description__: As an administrator, I want to be able to delete an existing project. After that, this project is permanently removed from the database and cannot be reached again.
+ __Acceptance Test #1__: After logging in as administrator "Test Admin", I can delete project "Foo". I can verify that "Foo" is removed from the database. I can login as artist "Test Artist" of "Foo" and verify that it's no longer on my dashboard or all projects view.
+ __Implementation__:
	+ __Back end pull request #16: Add new route /project to edit and delete projects to index.php, add methods to delete and edit (with actions of open and close) projects to project controller__
	+ __Front end pull request #21: Add open/close and delete buttons to open/close and delete projects to dashboard and all projects view, add those methods to corresponding controllers and projects factory__

### User Story #16, formerly #3.6: Closing Projects
+ __Velocity Points__: 10
+ __Description__: As an administrator, I want to be able to close an existing project. After doing that, no new changes can be made to this project by its members.
+ __Acceptance Test #1__: After logging in as administrator "Test Admin", I can close project "Bar". I can then login as supervisor "Test Supervisor" of "Bar" and verify that "Bar" is indicated to be closed on my dashboard and all projects view. I can no longer make any changes on "Foo".
+ __Implementation__:
	+ __Back end pull request #16: Add new route /project to edit and delete projects to index.php, add methods to delete and edit (with actions of open and close) projects to project controller__
	+ __Front end pull request #21: Add open/close and delete buttons to open/close and delete projects to dashboard and all projects view, add those methods to corresponding controllers and projects factory__

### User Story #17: Edit Profile View
+ __Velocity Points__: `TODO`
+ __Description__: As a user, I want to be able to edit my personal information such as email, gravatar email from an edit profile page. As an administrator, I want to be able to edit my and other users' personal information from an edit profile page.
+ __Acceptance Test #1__: After logging in as "Test User", I can go to my profile view and click "Edit Profile" to edit my profile and change my email from "test@user.com" to "dummy@user.com".
+ __Acceptance Test #2__: After logging in as "Test Admin" I can go to userlist, click "Test User"s user name to go to his profile view, click "Edit Profile" to edit his profile, and change his gravatar email from "gravatar@email.com" to 
"profile@picture.com".
+ __Implementation__:
	+ __Back end pull request #20: Add backend methods for profile and edit profile view__
	+ __Front end pull request #17: Implement 'Forgot Password' button for login, add button to 'Edit Profile' view and little fixes, User Stories 17, 21 and Bugfix__

### User Story #18: Open Projects
+ __Velocity Points__: 5
+ __Description__: As an administrator or a director of a project, I want to be able to open a closed project from the dashboard or the all projects view. After doing that the project can be worked on normally.
+ __Acceptance Test #1__: After logging in as "Test Admin", I can open the closed project "Project 1" by clicking "Open" from the dashboard. The indicator of "Project 1" is now "Open".
+ __Acceptance Test #2__: After logging in as "Test Director", I can open the closed project "Project 1" by clicking "Open" from the dashboard. The indicator of "Project 1" is now "Open". I cannot open a project that I am not the director of.

### User Story #19: Project View
+ __Velocity Points__: 15
+ __Description__: As a regeistered user, I want to be able to view a project. That is, I want to view all of its panels (including their title, canvases, descriptions, and notes). As an artist of a particular project, I want to be able
	+ to create new panels or remove them,
	+ to move panels around and therefore change their order, and 
	+ to be able to click a button for each panel that opens the so-called "panel edit view". (See user story #20 for details).
+ __Acceptance Test #1__: After logging in as "Test User", who is not enrolled in any projects, I want to be able to click on "Test Project". The following screen has to show all panels of the aforementioned project.
+ __Acceptance Test #2__: After logging in as "Test User 2", who is enrolled in "Test Project" as an artist, I want to be able to click on "Test Project". The following screen has to show all panels which I can move around freely. For each panel, I can see a button that leads me to a view in which I can edit it.
+ __Implementation__:
	+ __Back end pull request #18: Implement functionality triggered by routes for getting projects and canvases__
	+ __Back end pull request #21: Implement panel deletion__
	+ __Back end pull request #22: Implement panel creation__
	+ __Front end pull request #22: Implement project view and panel edit view__
	+ __Front end pull request #31: Implement panel deletion__
	+ __Front end pull request #33: Implement panel creation and saving a project's panel constellation__
	+ 

### User Story #20: Panel Edit View
+ __Velocity Points__: 20
+ __Description__: As an artist enrolled in a particular project, I want to be able to edit each panel as I desire: Since a panel contains a canvas on which assets are composed, I want to be able to manipulate the way they are composed. That is, I want
	+ to add (by choosing from a list of uploaded assets) and remove assets,
	+ to change an assets position (including the layer its on) within the canvas, and 
	+ to scale assets.
Additionally, I must be able not just edit a panels canvas but also a panels title, description, and notes.
+ __Acceptance Test #1__: `TODO`
+ __Implementation__:
	+ __Back end pull request #18: Implement functionality triggered by routes for getting projects and canvases__
	+ __Back end pull request #23: Implement panel saving__
	+ __Front end pull request #22: Implement project view and panel edit view__
	+ __Front end pull request #29: Increase canvas size when editing it__
	+ __Front end pull request #36: Implement canvas saving__

### User Story #21: Forgot Password
+ __Velocity Points__: 10
+ __Description__: As a user, I want to be able to be sent a random new password to my email address in case I forget mine. 
+ __Acceptance Test #1__: Before logging in as "Test User", I can reset my password after giving my username and email address. I get a new random password to my email address "test@email.com". I can then login using the new password.
+ __Implementation__:
 	+ __Back end pull request #38: Add backend methods for user story #21 ('Forgot Password' )__
 	+ __Front end pull request #37: Implement 'Forgot Password' button for login, add button to 'Edit Profile' view and little fixes, User Stories 17, 21 and Bugfix__

### User Story #22: Commentary Area
+ __Velocity Points__: 15
+ __Description__: As a project member I want to be able to discuss things in a commentary area.
+ __Acceptance Test #1__: After logging in as "TestUser" and opening the Project View I can see all comments any user posted in this particular project. I can then specify a new comment with Title "Title" and Text "Text". After clicking "Post Comment" it will be added to the list of comments and be visible to everyone else in the project. Also if I'm privileged (Director of the project or Moderator/Administrator) I can remove any comment.
+ __Implementation__:
 	+ __Back end pull request #37: Add code to add/remove/get comments__
 	+ __Front end pull request #47: Add code to add/remove/show comments__
 	+ 

### User Story #23: Asset Management
+ __Velocity Points__: 15
+ __Description__: As a project member I want to be able to add and remove Assets from Canvases in Panels. Additionally I want to be able to upload Assets and choose a tag for it. After that I can remove an asset assigned to a canvas.
+ __Acceptance Test #1__: After logging in as "TestUser" and opening a Panel of the Project View I can see a button called "upload asset". I can then press this button an chose an asset by double clicking it - it will be added to the panel's canvas then. I also can upload an asset by choosing a tag first, the file and a file name and then press "upload". While the upload is in progress a "please wait" message is shown. I am also able to click a cross signed button to remove Assets from a panel's canvas.
+ __Implementation__:
 	+ __Back end pull request #36: Implement Assetmanagement__
 	+ __Front end pull request #46: Implement Assetmanagement__

 
## Partially Reached or Missed Quality Goals
`TODO`
