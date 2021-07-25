# Lil Bugga

- [Project Links](#description-of-the-website)
- [Project Description](#purpose)
- [Project Features](#features)
- [Target Audience](#target-audience)
- [Tech Stack](#tech-stack)
- [Libraries](#libraries)
- [Entity Relationship Diagram](#entity-relationship-diagram)
- [Dataflow Diagram](#dataflow-diagram)
- [Application Architecture Diagram](#application-architecture-diagram)
- [User Stories](#user-stories)
- [Wireframes](#wireframes)
- [Project Management](#project-management)

## Description of the Website

- [Front-end GitHub](https://github.com/lil-bugga/lil-bugga-front-end)
- [Back-end GitHub](https://github.com/lil-bugga/lil-bugga-back-end)
- [Project-Documentation GitHub](https://github.com/lil-bugga/project-documentation)
- [Front-end Trello](https://trello.com/b/XMPa9Hot/lil-bugga-front-end)
- [Back-end Trello](https://trello.com/b/z0PAejSN/lil-bugga-back-end)
- [Hosted Front-end](https://lil-bugga.netlify.app/)
- [Hosted Back-end](https://lil-bugga.herokuapp.com/) NB: API only
- Deployed Link Not Yet Available

### Purpose

Lil Bugga is a professional and light bug tracking platform, intended to act as companion tracking software during a project's construction and maintenance. It gives both the development team and stakeholders the ability to flag functions and features of the application in need of change, and have it addressed and tracked clearly and effectively.

### Features

#### MVP

You are able to:

- Login to the application and enter your details in a secure manner.
- Create a virtual Project, with a name, description, logo, and associated team members.
- Search through Projects you are associated with or own, and go to that Project’s dashboard to quickly view its current status.
- Become part of a Project team in a role that permits you to perform actions relevant to your position.
- View the tickets associated with the Project, to see what issues have already been flagged and what status the Project is in.
- Create Tickets for the Project you are associated with, to flag bugs or changes that need to be made.
- Respond to Ticket updates as the Development Team responds to the Ticket, to ensure that it gets adequately resolved.
- See Tickets that have been assigned to you as a Developer, and collaborate with its originator as you work through its resolution.
- Close, open, or delete Tickets to a Project, so long as you are a Project Administrator or Owner.
- Change User roles for a Project that I own, to ensure stakeholders only have the access to change Tickets relevant to their position.
- Edit the details of a Project that I own, to keep its information relevant.

System Administrators are able to:

- View and monitor all Projects and Tickets available on the system.
- Delete any Project or Ticket on the system considered offensive, or spam.

#### Bonus Features

- Live updating Ticket entries, without needing a page refresh.
- The ability to login using a GitHub or Google account.
- Export all Tickets associated with a Project in various formats for convenient data entry or viewing.
- Import tickets in various formats for convenient data entry
- Add users who do not yet have an account via their email, to avoid needing to give them permission at a later date.
- Allow users to customise their colour theme or choose from several premade options.
- Front and back end pagination for Tickets.
- User inbox system, with the last session stored on the backend.

### Target Audience

This product is intended for **Development Teams** that want a light and dedicated solution to tracking bugs found in their product.

>This type of user is expected to be working on some form of Software Project, they have a technical understanding of what the project is, how it works, and the technology behind it. They are computer literate and need a platform that is fast to load, responsive to their various devices and has a colour scheme that doesn’t irritate their eyes (which have probably been locked onto a computer screen for many hours).

The product will also be used by **stakeholders of the product** who wish to log issues they are having with the system.

>These users might not have a technical background, but they understand what graphical or experiential inconsistency they believe needs to be addressed. They need a platform that is simple and intuitive to navigate, so they can quickly find the Project they are associated with. And just as quickly, create a Ticket that can accurately represent the issue they are having.

### Tech Stack

#### Back-end

- Ruby on Rails
- PostgreSQL
- Heroku
- RSpec testing library

#### Front-end

- React
- JSX
- Netlify
- Bootstrap
- Jest / React Testing Library
- JavaScript
- HTML
- CSS

### Libraries

#### Back-end

- Faker
  - Faker is a gem used to generate fake, realistic-looking data. In this project, it is used solely for testing purposes and for generating realistic-looking seed data quickly. It should have no impact upon production implementation
- Bcrypt
  - Bcrypt is a gem that is included by default with a rails package. Whilst it needs to be uncommented in the `Gemfile` it is a useful gem that adds powerful methods for hashing passwords in the application. When enabled in the bundle file it adds the `has_secure_password` method to the project. When configured in the user model it sets a field called `password_confimation` that must be met as well as the regular password input field. If the two passwords match on a POST request Bcrypt hashes the password using its encryption algorithm and stores them in a database field called `password_digest`. Likewise, for authentication it encrypts the received password using the same algorithm and confirms a match.
- Knock
  - The Knock gem is used by the project to generate `JWT` bearer tokens used to authenticate users on the site. When a user connects to the site and is authenticated by `Bcrypt` a unique JWT token is generated using knock to identify them and transmitted in the response back. In subsequent requests to the server, if a user is required to authenticate they must post this `JWT token` in the request header. By default, this token is valid for 24 hours. We found this default acceptable and have opted to leave it as is.
- Rack-cors
  - `CORS` or Cross Origin Resource Sharing is a service used to authenticate network traffic across the internet. In this implementation, the `cors` gem is used to whitelist different URI's, preventing non-whitelisted domains from being able to submit API requests. Due to implementation issues with Netlify, this is currently set to enable all sources to make requests. Whilst not ideal, the back-end is not using any resources outside of the PostgreSQL database, and because authentication is required so we find the risk is acceptable.
- RSpec-rails
  - RSpec is a popular and well-known testing library for rails. I used it to generate my test suite.
- Factory_bot_rails
  - The `Factory bot` gem is a helper gem to assist with testing libraries. It allows you to write a framework or scaffold example of a model in a separate file. This scaffold can then be imported into the testing suite and used to build or create model entries to test against. Removing this code from the test files. It is by no means necessary but does simplify the testing implementation.
- Rails-controller-testing
  - rails controller testing allows you to make and mock(or imitate) data hitting your API endpoints. This is a useful tool that allows the testing suite to better and more predictably test the logic of controller methods.
- SimpleCov
  - SimpleCov generates an HTML file based on testing results allowing you to see a representation of testing done on the files specified. As a metric of test quality, SimpleCov should be seen as unreliable, as it only counts the number of lines your tests read, vs the number of lines actually in the file. However, it does provide some simple insight into the completeness of the test suite.
- Database_cleaner
  - Database cleaner is a tool used to complement the test suite. It acts to remove database entries made by the test suite in a way defined in its configuration. In this implementation, once tests have been completed database cleaner will rollback all commits since the initialisation of the test suite, essentially giving you a clean slate to work from.

#### Front-end

- Axios
  - It's a "Promise based HTTP client for the browser and node.js", which essentially allows you to make requests to external APIs easily, as an alternative to using the Javascript fetch method. Axios was used extensively through the front-end where requests to the back-end needed to be made, and it was an effective and clean way to make the responses.
- React
  - A Javascript library for building fast loading user interfaces in web applications. The front-end of lil bugga is built entirely in React, making use of components that render and update to the DOM conditionally, rather than all at once like in a regular application. It was used in many different ways through the application, following the newer functional components way of doing things, making use of Hooks to hold state, set asynchronous events and more.
- react-chartjs-2
  - It's a charting library made for one purpose, to chart information, particularly from React applications. It's imported into a project through node modules, and used component-wise. It was used numerous times for the Bar components, which was used to give give users a visual read on where most of their tickets were allocated.
- Bootstrap (just the CSS)
  - A framework that allows you to quickly customize the user interface. It acts as a convenience when manipulating CSS, using HTML classes to change visual features over CSS driven by selectors. It helped to cut down on code in this project, and gets used extensively to make divs behave as desired, and to center text.
- react-bootstrap
  - A framework that replaces the need for Bootstrap in React applications, giving you the power to create template components like modals and nav-bars without the old dependencies on jQuery etc. It got used alongside Bootstrap for NavBar and Modals, which required javascript configuration. This meant we didn't need the jQuery or the Javascript part of Bootstrap.

## Testing

### Back-end

Primary integration and unit testing for the lil-bugga back-end has been completed using RSpec. To run the test suite, navigate to the root directory of the backend, and run the following command in terminal:

```sh
bundle install
rspec -fd
```

This will run all of the projects rspec tests from the `/spec/` folder. It is also configured to generate a coverage report when run. This is located in `/public/coverage/index.html` after RSpec tests have concluded and can be opened with any web browser.

Note that there were some dependency issues with **simpleCov**, the gem used to help create the coverage report, and it should be considered indicative only.

### Front-end

Unit testing was commenced in the lil-bugga front-end using jest and can be run by navigating to the root directory of the front-end, and running the following command in terminal:

```shell
yarn install
yarn test 
```

or

```shell
yarn install
npm run test
```

Full integration testing was also run using Cypress, however a large number of dependency errors were encountered during this process. To replicate cypress testing please follow the following steps precisely. Failure to do so will cause cypress to delete core dependencies from the node modules folder and brick your clone of the repository.

## Entity Relationship Diagram

![Entity Relationship Diagram](docs/2021-07-16-ERD.png)

## Dataflow Diagram

![0-Level Dataflow Diagram](./docs/2021-07-11-DFD-0Level.svg)

## Application Architecture Diagram

![Architecture Diagram](./docs/2021-07-12-Diagram-Architecture.png)

## User Stories

### Definitions

**Ticket:** A Ticket is a small report which represents a bug or issue detected on the real life project. It can be created and monitored by a Client, but only a Developer, Admin, Owner, or the Client who created the ticket may respond to it.

**Project:** A virtual project instance to which Tickets can be lodged, viewed by others, and ultimately resolved. Simply, a Project refers to the virtual representation of a body of work found on Lil Bugga, it includes the real life projects name, a description, Owner, Tickets, and associated Clients, Developers, and Admin.

**User:** Someone using the software, not necessarily logged in.

**System Administrator:** A logged in User, with administrative privileges over the Lil Bugga platform and it’s content.

_Definitions scoped to a Project instance:_

**Client:** A logged in User with base level access to the project. This is the status given to software testers not on the technical team.

**Developer:** A logged in User with powers of a Client, and the ability to respond to all Client tickets. This is the status given to most software developers.

**Administrator:** A logged in User with powers of a Developer, and the ability to open, close and remove tickets based on their perceived resolution. This is the status given to project arbiters.

**Owner:** A logged in User who is the sole owner of a project, and can create, alter, and destroy all aspects of it unchallenged. This is the project lead administrator responsible for the project overall.

### Stories

As a **User** I want to be able to:

- Create an account on the platform, so my activities with the tool are unique to me.
- Sign in and navigate the application, so that my projects and tickets are only available to me.
- Update my account details, to keep my account safe and up to date.
- See projects I am included in, and know what my authority for that project is, for ease of use.
- Search through the projects I am participating in, so that I can quickly find the project I am looking for.
- Create a virtual project, to track the bugs that occur within my real life software project.

As a **System Administrator** I want to be able to:

- Remove spam or offensive content found within Projects on the platform, to prevent software misuse.
- Moderate all Projects, Tickets, and Users present on the system, to aid in manually protecting the integrity of the system.
- Have ultimate access and authority over the application, in order to moderate the Projects, Tickets, and Users.

As a **Client** I want to be able to:

- Create a Ticket for the project based on bugs I detect or issues I have with the software, so the development team can see that issue and address it.
- Watch that ticket be addressed by the development team and respond to them when changes are made or questions arise, so that the development team can achieve a resolution to the Ticket.
- View the status of the Tickets I have posted, so I can know when or if the attributed fix has been made.
- See all Tickets associated with the Project, so I know if my issue has already been raised by someone else.
- View a dashboard of the project, so I can get a brief overview of the project status and see what progress has been made at a glance.

As a **Developer** I want to be able to:

- Do all the things a Client can do, so that I can access the Project, and raise issues as I see them as well.
- See the tickets assigned to me, so that I know what I could or should be working on as assigned by the Project Administrator.
- Assign tickets to myself, so that I can resolve issues that may be related to tickets I have already been assigned.
- Address tickets assigned to me, so that I can get the real life project closer to error free functionality as part of transient or ongoing maintenance.

As an **Administrator** I want to be able to:

- Do all the things a Developer can do, so that I can participate in Project Ticket resolution, whilst simultaneously being an authority over Ticket resolution.
- Close a Ticket that I deem adequately addressed, so that the development team can prioritize unresolved Tickets.
- Delete a Ticket that is deemed poor quality, offensive, or spam, so that the Project is not littered with redundant or unnecessary Tickets.
- Reopen a Ticket that may have been accidentally closed, or wrongfully judged as addressed, to avoid having to recreate a new Ticket on such an occasion.

As an **Owner** I want to be able to:

- Add team members to the project, so they can access and resolve tickets.
- Modify Project collaborators authority levels, so they only have the feature access they need to participate in the Project.
- Give project ownership to another User, so that if I am stepping down as the Project owner, the virtual Project’s administration can be changed accordingly.
- Edit the details of the Project, so that it stays accurately in sync with the real life project.

## Wireframes

**Landing Page:**
![Wireframe - Landing](./docs/wireframes/Landing.png)
**Login Page:**
![Wireframe - Login](./docs/wireframes/Login.png)
**User Dashboard:**
![Wireframe - Dashboard](./docs/wireframes/Dashboard.png)
**Account Settings:**
![Wireframe - Account Settings](./docs/wireframes/Account_Settings.png)
**Create Project:**
![Wireframe - Create Project](./docs/wireframes/Create_Project.png)
**Project Dashboard:**
![Wireframe - Project Dashboard](./docs/wireframes/Project_Dashboard.png)
**Project Tickets:**
![Wireframe - Project Tickets](./docs/wireframes/Project_Tickets.png)
**Create Tickets:**
![Wireframe - Create Ticket](./docs/wireframes/Create_Ticket.png)
**Ticket View:**
![Wireframe - Ticket View](./docs/wireframes/Ticket_View.png)

## Project Management

**Project Board Links:**

- [Documentation](https://trello.com/b/M6Si7LVG/lil-bugga)
- [Front-End](https://trello.com/b/XMPa9Hot/lil-bugga-front-end)
- [Back-End](https://trello.com/b/z0PAejSN/lil-bugga-back-end)

### Methodology

The project management of Lil-Bugga is handled using multiple Trello Kanban boards to represent different logical components of the project.
Each team member has then taken over-arching responsibility for a different component of the project:

- There is one project board for the project documentation, for which we have both taken responsibility.
- Another project board for the projects Front-End, for which Dean has taken responsibility.
- Finally, there is another project board for the projects Back-End, for which Ryan has taken responsibility.

We opted for this strategy to ensure that each part of the project has one person dedicated to driving it. The person driving the project component ultimately populates the board with its overall tasks, assigns them difficulty and a responsible person. They then follow up with the team member assigned to each task as it progresses.

Assignment of tasks is handled during our daily stand-ups, where we discuss timelines for different tasks, our progress with assigned tasks, and any issues we may be facing. As a part of the stand-up process, we walk the other team member through what we have been doing and seek input on decisions that we have made.

When the person responsible for a task deems it as complete, they move it to "pending review" on the Trello board, and if appropriate, make a pull request for the feature on GitHub. The other team member then reviews either the piece of work or the pull request and discusses it with the responsible person in the morning stand-up or a dedicated meeting. They will suggest any changes they deem necessary and commit finalised work to the repository or primary document.

In this way, we are both across progress in the project, and the entirety of our scope of work. The separation of project boards allows us to assign ownership both at a task level and at a project level for different components.

### Screenshots - Project Documentation

**2021-11-07 Morning**
![2021-07-11-Screenshot-Trello-Morning](./docs/2021-07-11-Screenshot-Trello-PD.png)

**2021-11-07 Afternoon**
![2021-07-11-Screenshot-Trello-Afternoon](./docs/2021-07-11-Screenshot-Trello-PD1.png)

**2021-12-07 Morning**
![2021-07-12-Screenshot-Trello-Morning](./docs/2021-07-12-Screenshot-Trello-PD.png)

**2021-12-07 Afternoon**
![2021-07-12-Screenshot-Trello-Afternoon](./docs/2021-07-12-Screenshot-Trello-PD1.png)

**2021-16-07 Afternoon**
![2021-07-16-Screenshot-Trello-Afternoon](./docs/2021-07-16-Screenshot-Trello-PD1.png)

### Screenshots - Front-End

**2021-13-07 Morning**
![2021-07-13-Screenshot-Trello-Morning](./docs/2021-07-13-Screenshot-Trello-FE1.png)

**2021-13-07 Afternoon**
![2021-07-13-Screenshot-Trello-Afternoon](./docs/2021-07-13-Screenshot-Trello-FE2.png)

**2021-14-07 Morning**
![2021-07-14-Screenshot-Trello-Morning](./docs/2021-07-14-Screenshot-Trello-FE1.png)

**2021-14-07 Afternoon**
![2021-07-14-Screenshot-Trello-Afternoon](./docs/2021-07-14-Screenshot-Trello-FE2.png)

**2021-15-07 Morning**
![2021-07-15-Screenshot-Trello-Morning](./docs/2021-07-15-Screenshot-Trello-FE1.png)

**2021-15-07 Afternoon**
![2021-07-15-Screenshot-Trello-Afternoon](./docs/2021-07-15-Screenshot-Trello-FE2.png)

**2021-16-07 Morning**
![2021-07-16-Screenshot-Trello-Morning](./docs/2021-07-16-Screenshot-Trello-FE1.png)

**2021-16-07 Afternoon**
![2021-07-16-Screenshot-Trello-Afternoon](./docs/2021-07-16-Screenshot-Trello-FE2.png)

### Screenshots - Back-End

**2021-15-07**
![2021-07-13-Screenshot-Trello](./docs/2021-07-15-Screenshot-Trello-BE.png)

**2021-16-07 Morning**
![2021-07-13-Screenshot-Trello-Morning](./docs/2021-07-16-Screenshot-Trello-BE.png)

**2021-16-07 Afternoon**
![2021-07-13-Screenshot-Trello-Afternoon](./docs/2021-07-16-Screenshot-Trello-BE2.png)