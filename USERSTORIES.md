# Documentary Proof of the Execution of the Quality Assurance Measures

:with_toc_data

## Introduction

At the very beginning of this project, we created a document ("Qualitätssicherungsdokument") that outlined certain quality goals which were to be met by the software as well as measures and practices for the developers to adhere to in order to reach these quality goals. Here is a __shortened__ check-list-style summary of these goals:

1. __Ease of Use__
	1. The user interface has to be visually consistent/coherent. Therefore, all UI elements must be part of Twitter's Bootstrap framework.
	2. Each feature has to be accessible with no more than three clicks.

2. __Functionality__
	1. Each feature has to be described in a user story before its being implemented. This way, possible misunderstandings can be sorted out before one line onf code is being written.
	2. Each user story comes with at least one so-called "acceptance test", which precisely (click-by-click) describes a scenario in which the new functionality is being applied. A user story may not be considered done until the test associated with it passed.
	3. Towards the end of the development, one or more "usability tests" have to be conducted. A usability test consists of several questions to be answered by potential users of the software. The goal is to find out how satisfied they are with it and what they want to be done differently.

3. __Analyzability (or "Understandability of the Source Code")__
	1. Each source code change (addition, modification, or deletion) has to be associated with either
		+ a user story or
		+ a bug that is being tracked with the GitHub bug tracker.
	2. Therefore, all so-called "pull requests" have to come with either a user story id or a bug id.
	3. Each method has to come with a JavaDoc-style comment right above its signature that describes its what it does, its parameters, etc.

As the title suggests, it is the purpose of this document to either proove that these goals have been reached or document the reasons why some of them could not be realized. `TO BE CONTINUED`

## Problems

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

## User Stories

### User Story #1: Registration of User Accounts
+ __Velocity__: 10 Points
+ __Description__: As a person, I want to be able to register an account on a Paperdreamer instance. I want to enter my user name, email address and password and confirm the data to register myself as a user. This user account is not functional until an administrator confirms it.
+ __Acceptance Test #1__: After registering as a user called "Test User" with the email address testuser@paperdreamer.org, one has to verify that the user account is created in the database, but logging in will fail until an administrator enables it.
+ __Implementation__:
	+ __Back end pull request #3: Server-side validation of registration data__
	+ __Back end pull request #4: User lists and activating users__
	+ __Back end pull request #7: Mail service__
	+ __Front end pull request #4: Implement registration and notifications__
	+ __Front end pull request #7: Implement settings factory and refactor the registration__

### User Story #2: Changing User Account Passwords
+ __Velocity__: 10 Points
+ __Description__: As a user, I want to be able to change the password that I use to log in to the Paperdreamer platform. For security purposes, I want to be forced to enter my current password twice before entering my desired password (twice, also). The next time I want to log in, I want to be able to do so using the new password.
+ __Acceptance Test #1__: Using the login credentials of "Test User", one has to log in to the Paperdreamer platform using the generated password. Then, one has to change "Test User"'s password like described above. If, afterwards, loggin in with the new password works, this test can be considered done.
+ __Implementation__:
	+ `TODO: NO MATCHING BACK END PULL REQUEST`
	+ __Front end pull request #7:  Implement settings factory and refactor the registration__ `?`

### User Story #3: Receiving an Email After Registration 
+ __Velocity__: 4 Points
+ __Description__: After registering on a Paperdreamer instance, I will receive an email, where I need to confirm the entered data by clicking on a link. After this, the account will show up in the list of users for the administrator(s) to confirm.
+ __Acceptance Test #1__: After registering as a user, one has to verify the provided data by clicking on a link in a received email. After the link has been clicked by the newly registered user, this user needs to show up in the list of unconfirmed users (which can only be accessed by administrators).
+ __Implementation__:
	+ __Back end pull request #7: Mail service__


### User Story #4: Confirming User Accounts
+ __Velocity__: 6 Points
+ __Description__: As an administrator, I want to be able to confirm user accounts. After registering as user, the account is not activated, until I (or another administrator) enables it, by choosing to reject or accept it.
+ __Acceptance Test #1__: After registering as a user, my account is disabled and I cannot login. One has to verify that after confirming the account as administrator, the new user can log in with the data he entered in the original registration process.
+ __Implementation__:
	+ __Back end pull request #4: User lists and activating users__
	+ __Front end pull request #5: Implement user stories #4, #5 and #6__


### User Story #5: List of Not Yet Activated Users
+ __Velocity__: 10 Points
+ __Description__: As an administrator, I want to see a list of user accounts which I need to accept or reject.
+ __Acceptance Test #1__: After registering as a new user, I login as administrator and can open the list of unconfirmed users. One has to confirm that the new user shows up in the list.
+ __Implementation__:
	+ __Back end pull request #4: User lists and activating users__
	+ __Front end pull request #5: Implement user stories #4, #5 and #6__

### User Story #6: List of All Users
+ __Velocity__: 10 Points
+ __Description__: As an administrator, I want to see a list of all users in the system.
Once I am logged in as administrator, I can open a view of all registered users. This view will show at least each user name and the associated permissions ("Administrator" or "User").
+ __Acceptance Test #1__: After creating a new user ("Test User"), I can login as administrator and open the user view. "Test User" will show up with the associated permission being "User".
+ __Implementation__:
	+ __Back end pull request #4: User lists and activating users__
	+ __Front end pull request #5: Implement user stories #4, #5 and #6__


### User Story #7: Promoting Users
+ __Velocity__: 8 Points
+ __Description__: As an administrator, I want to be able to promote users to admins. Once I am logged in a user account with administrator privileges, I can open the user view, where I can change the permissions of each user. The following system wide permissions are supported: Administrator (not-deleteable, "God" mode), Administrator (deleteable) and User. Non-deletable administrators can only be promoted by another non-deleteable administrators, the same is true for changing the permissions of user from "Administrator" to "User".
+ __Acceptance Test #1__: After creating a new user ("Test User"), I can login as administrator and change his permissions to "Administrator". After logging out, I can login with "Test User" and change permissions as well.
+ __Acceptance Test #2__: After creating a new user ("Test User"), I can login as "God" administrator and change his permissions to "Administrator, non-deletable". After confirming my choice, deleting "Test User" is not possible.
+ __Implementation__:
	+ __Back end pull request #9: Add methods for changing user roles__
	+ __Front end pull request #13:  Make admin userlist roles dropdowns, add methods for changing roles to controller and factory__

### User Story #8: Profile View
+ __Velocity__: `TODO`
+ __Description__: As a user, I want to be able to view my profile as well as other users' profiles. After I login to my account by clicking "View Your Profile" (or something similar), I want to be able to see my current profile information such as my avatar, user name, email address (and other personal information the user has provided). By clicking someone else's username I want to be able to view their profile.
+ __Acceptance Test #1__: `TODO`
+ __Implementation__:
	+ __Back end pull request #20: Add backend methods for profile and edit profile view__
	+ `NO MATCHING FRONT END PULL REQUEST`

### User Story #9: Logging In
+ __Velocity__: `TODO`
+ __Description__: As a user (which can also be an administrator), I want to be able to log in to the platform. Therefore I enter my credentials (user name or email and password) into a login form. The login button will be unclickable unless both fields are filled with information that fits the format. If, and only if, the provided credetials were correct, access is being granted after clicking the login button. Otherwise, there will be an error message popping up.
+ __Acceptance Test #1__: Try to log in with fictional credentials. There should be an error message saying that the provided credentials weren't accepted.
+ __Acceptance Test #2__: Try to log in without a password, the login button should be unclickable, though.
+ __Acceptance Test #3__: Log in with an existing user's credentials.
+ __Implementation__:
	+ __Back end pull request #6: Implement GET /user route `?`__
	+ __Front end pull request #4: Implement registration and notifications__
	+ __Front end pull request #6: Implement login live validation__

### User Story #10: Header Bar
+ __Velocity__: `TODO`
+ __Description__: As a user, I want to be able to switch between different views. I want to open a list of all public projects, a list of my projects and also my account settings from a header bar, which I can access on every page, as long as I'm logged in.
+ __Acceptance Test #1__: Before logging in, there is no header bar visible. Once I login as any user, a header view is shown with at least the entries "My Projects", "All Projects" and a link to my user account settings. Clicking on each link opens the page corresponding to it.
+ __Implementation__:
	+ __Back end pull request #11: Add project controller and methods for getting belonged and all projects, add new paths to index__
	+ __Front end pull request #10: Create a header bar for Paperdreamer__

### User Story #11, formerly #3.1: List of My Projects ("Dashboard")
+ __Velocity__: 10 Points
+ __Description__: As a user, I want to see a page containing a list of all projects that I am participating in. These projects should have an indicator that shows whether they are open. This page should be the first thing I see after logging in. This should also be my home page.
+ __Acceptance Test #1__: After creating a new project "Foo" and assigning user "Test User" to it I can login as "Test User" and see "Foo" on my dashboard and that it is open.
+ __Implementation__:
	+ __Back end pull request #11: Add project controller and methods for getting belonged and all projects, add new paths to index__
	+ `NO MATCHING FRONT END USER STORY`

### User Story #12, formerly #3.2: List of All Projects
+ __Velocity__: 8 Points
+ __Description__: As a user, I want to be able to open a page where I can see all the projects on the platform, regardless of my membership and an indicator which shows whether they are open.
+ __Acceptance Test #1__: After creating a new project "Foo" and assigning user "Test User" to it, I can login as "Test User" or another user "Test User 2" and see "Foo" on the all projects view and that it is open.
+ __Implementation__:
	+ __Back end pull request #11: Add project controller and methods for getting belonged and all projects, add new paths to index__
	+ __Front end pull request #16: Add dashboard and all projects view, add factories and controllers for those__

### User Story #13, formerly #3.3: Creating Projects
+ __Velocity__: 10 Points
+ __Description__: As an administrator, I want to be able to create new projects by giving it a name and a description, adding users for this project and assigning those users as Director, Supervisor or Artist.
+ __Acceptance Test #1__: After logging in as administrator "Test Admin", I can create a new Project "Dummy" and give it a description of "Dummy Project". I can assign user "Test User" to this project and make him the director of the project. I can then verify that this project is created in the database.
+ __Acceptance Test #2__: After logging in as "Test User", I can see "Dummy" on my dashboard, my all projects view and that it's open. I can then login as user "Test User 2" and see "Dummy" on my all projects view and that it's open but not on my dashboard.
+ __Implementation__:
	+ __Back end pull request #17: Add createProject route to flight and implement it__
	+ __Front end pull request #23: Add functionality to add new projects__
	+ __Front end pull request #27: Add autocomplete to create project page__

### User Story #14, formerly #3.4: Editing a Project's Meta Data
+ __Velocity__: 7 Points
+ __Description__: As an administrator, I want to be able to change the meta data of an existing project like changing its name, its users, roles of users.
+ __Acceptance Test #1__: After logging in as administrator "Test Admin", I can edit the project "Dummy" by changing its name to "Foo" and its description from "Dummy Project" to "Project Foo", by assigning user "Test User" as supervisor, by making the director "Test Director" an artist and by removing artist "Test Artist" from the project.
+ __Acceptance Test #2__: After logging in as "Test User", I can see "Foo" on my dashboard, all projects view and that it's open. I can login as "Test Director" and see the name change from "Dummy" to "Foo" on my dashboard and all projects view. I can then login as "Test Artist" and see the name change from "Dummy" to "Foo" on my all projects view but cannot see "Dummy" or "Foo" on my dashboard.
+ __Implementation__:
	+ __Back end pull request #16: Add new route /project to edit and delete projects to index.php, add methods to delete and edit (with actions of open and close) projects to project controller__
	+ `NO MATCHING FRONT END PULL REQUEST`

### User Story #15, formerly #3.5: Deleting Projects
+ __Velocity__: 5 Points
+ __Description__: As an administrator, I want to be able to delete an existing project. After that, this project is permanently removed from the database and cannot be reached again.
+ __Acceptance Test #1__: After logging in as administrator "Test Admin", I can delete project "Foo". I can verify that "Foo" is removed from the database. I can login as artist "Test Artist" of "Foo" and verify that it's no longer on my dashboard or all projects view.
+ __Implementation__:
	+ __Back end pull request #16: Add new route /project to edit and delete projects to index.php, add methods to delete and edit (with actions of open and close) projects to project controller__
	+ __Front end pull request #21: Add open/close and delete buttons to open/close and delete projects to dashboard and all projects view, add those methods to corresponding controllers and projects factory__

### User Story #16, formerly #3.6: Closing Projects
+ __Velocity__: 10 Points
- __Description__: As an administrator, I want to be able to close an existing project. After doing that, no new changes can be made to this project by its members.
+ __Acceptance Test #1__: After logging in as administrator "Test Admin", I can close project "Bar". I can then login as supervisor "Test Supervisor" of "Bar" and verify that "Bar" is indicated to be closed on my dashboard and all projects view. I can no longer make any changes on "Foo".
+ __Implementation__:
	+ __Back end pull request #16: Add new route /project to edit and delete projects to index.php, add methods to delete and edit (with actions of open and close) projects to project controller__
	+ __Front end pull request #21: Add open/close and delete buttons to open/close and delete projects to dashboard and all projects view, add those methods to corresponding controllers and projects factory__