# MovieList

WatchList is a web application with the purpose of allowing the user to make a watch list of desired movies. The system will allow any user to login/register to the application and make different lists of movies that they can access whenever.

## Demo Link

[https://movielist-qrei65adgq-ue.a.run.app/](https://movielist-qrei65adgq-ue.a.run.app/)

<hr />

## Definitions and Acronyms

| Term         | Definition                                                                                                                           |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| API          | Application Programming Interface defines interactions between multiple software intermediaries                                      |
| Backend      | Components that communicate between the front end and any systems required to make the program work                                  |
| Bcrypt       | A password hashing algorithm based on Blowfish cipher                                                                                |
| Docker       | An open source containerization platform                                                                                             |
| Frontend     | Section that the user interacts the most with, so that they don’t notice all the calculations and things going on behind the website |
| GCP          | Google Cloud Platform                                                                                                                |
| Github       | A web-based interface for Git that provides version control, CI/CD automation, and project management services                       |
| GUI          | Graphical User Interface                                                                                                             |
| Jest         | An open-source JavaScript testing framework                                                                                          |
| JWT          | JSON Web Token                                                                                                                       |
| MongoDB      | An open-source document database and leading NoSQL database                                                                          |
| NoSql        | A database that uses objects in order to store its elements                                                                          |
| Pull Request | Request for changes to be made in an existing codebase hosted on Github                                                              |
| UI           | User Interface                                                                                                                       |

<hr />

## Plan

We decided to make a web application allowing a user to make a watchlist of movies. The system would require a user to login/register to the application before granting access to a movie search and watchlist. Given the project time period of around one month, our primary goal was to create a working prototype with the basic functionality. Other goals for the project included practicing the software development cycle (specifically Agile methodology), building upon our teamwork and collaboration skills, and using the various software tools we have learned in class as well as other tools not used in the previous project.

### Communication

We used GroupMe for any communications required between the team asynchronously. We regularly discussed any accomplishments made and broke down other goals into different tasks, assigned them amongst us, and ensured everyone had access to the required resources to complete the assigned task and all roadblocks had been resolved.

### Risk Management

| Risk                                        | Probability | Severity | Description                                                                                                                                                                                                                                                                                                     | Mitigation Plan                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------------- | ----------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Running out of GCP credits                  | Low         | High     | We are using GCP products such as GCP Cloud Run and Container Registry. We could run out of GCP credits due to high usage, and this would affect running our application properly. Worst case scenario, our application could even stop completely.                                                             | We are currently using GCP for Cloud Run and Container Registry. These services are not completely free, we might run of our credits over time. Hence it is important that we use these services optimally. We are using cache on client side to reduce the usage of Cloud Run. This improved the performance of our application greatly. In addition, we made sure we allocated only required resources and optimize the application such that new instances are not created unnecessarily to handle increasing user traffic. |
| Inefficient communication                   | Low         | High     | This can lead to conflicts and possibly missing deadlines. Without effective communication, it will be hard to address or tackle any roadblocks that we might encounter.                                                                                                                                        | To promote communication, we constantly checked in with each other to track each other’s progress. Effective communication helped tackle issues quickly and in time. We used chat messages frequently to update each other about the progress and ask for help if required.                                                                                                                                                                                                                                                    |
| Poor Code Quality                           | Low         | High     | This can be the result of unoptimized and buggy code. As a result, the application might not be maintainable. Similarly, unoptimized code can rack up the fee on Cloud Run and Contrainer Registry. It can introduce some serious security vulnerabilities that others could potentially exploit to cause harm. | For each pull request, we did code reviews and changes were committed to the `main` branch after atleast one other team member approved. We used GitHub action to run all existing test to ensure no breaking chages were introduced.                                                                                                                                                                                                                                                                                          |
| Unauthorized access to pages and API routes | Medium      | High     | We want to limit unauthorized users from using our application. If not, someone else could simply misuse our application for their purpose such as potentially use our APIs to serve their applications.                                                                                                        | Except for authentication API routes and pages, all other routes and pages were made private by default. We used JWT for both authentication and authorization purposes. Anytime a request was made to a private page or a route, we checked for a valid JWT. If JWT is not provided, is invalid, or is expired, the request is rejected.                                                                                                                                                                                      |

<hr />

## Requirements

The project topic and functionality were open-ended. The goal was to use the experience gained from Project 1 to create a new application.

The list of functional requirements of the system are:

- An existing user should be able to be log into the system.

  A user will provide their username and password. If the username exists and the password matches, they will be now authorized to use the search feature of the system.

- A new user should be able to register into the system.

  A user will provide a new username and password which will be saved by the system. This will allow a user to log in to the application to use the search feature.

- An authenticated user should be able to search for movies based on the following search inputs:

  - Keyword
  - Release Year
  - Ratings
  - Genres
  - Certifications

- An authenticated user should be able to see the details about the movie:

  - Runtime
  - Release Year
  - Ratings
  - Overview
  - Genres
  - Movie Trailer
  - Movie Watch Providers (Streaming Services, Rental, Buy)

- An authenticated user should be able to save a movie in a watchlist.
- An authenticated user should be able to see all the movies saved in their watchlist.
- An authenticated user should be able to remove a movie from their watchlist.
- An authenticated user should be able to log out from the system.

Some of the non-functional requirements of the system are:

- All of the user password must be hashed before storing in the database.
- Unauthenticated users cannot search for movies and view watchlist.
- Authenticated user cannot view watchlist of other users.
- Multiple users can use the system simultaneously.
- The system should scale appropriately based on the user traffic.
- The system must be reliable to promote good user experience and minimize downtimes.
- Results from API calls to get movie details should be cached to increase performance and reduce traffic to 3rd party APIs.

<hr />

## Design

The primary components of our system are:

1. Frontend Component

   This component will be visible to users and users interact directly with it. We will follow an event-driven architectural style for this component. If we need to communicate with the backend component for a given event, we will use Representation State Transfer to communicate with the backend component. It helps us decouple backend and frontend components and allows us to update the implementation of any one component without affecting another.

2. Backend Component

   This component will not be visible to the users. However, it will be used by the frontend component for authentication, search, and watchlist functionalities. We will follow the client-server architecture style, where the backend component serves as the server and the frontend component server as the client. A single server (backend component) can serve multiple clients (frontend components) which reduces the cost of running the application. This makes it easier to scale our server as required when we have increased clients.

   This component will also be responsible for communicating with The Movie DB API to find movies based on search parameters and get additional details for a movie. Similarly, it will connect with GCP Datastore to find and store user data such as credentials and watchlist. It also provides authentication functionalities such as issuing and validating JWTs that is used to identify authenticated users and limit access the features.

### Component Diagram

<iframe frameborder="0" style="width:100%;height:602px;" src="https://viewer.diagrams.net/?highlight=0000ff&nav=1&title=component-diagram#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D1RWP2ysdOO12GLQcZSBtM4XfWC88ytRZY%26export%3Ddownload"></iframe>

### Class Diagram

<iframe frameborder="0" style="width:100%;height:1161px;" src="https://viewer.diagrams.net/?highlight=0000ff&nav=1&title=Copy%20of%20Class%20Diagram#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D19ChYWUYOVBCGRt1arCBkeqJx3wTh3Qjm%26export%3Ddownload"></iframe>

### User Interface Design

MovieList aims to elevate the user experience through intuitive and seamless UI design for each component in the application. To achieve it, we will be creating different visual elements in our components.

#### Login Page

![Login Page](/images/login-page.png)

#### Registration Page

![Registration Page](/images/registration-page.png)

#### Search Page

![Search Page](/images/search-page.png)

#### Movie Details

The movie details will be shown in a modal. It will contain:

- Basic information and trailer for the movie, button to manage movie in watchlist

  ![Movie Details](/images/movie-details-overview.png)

- Watch Providers

  ![Movie Providers](/images/movie-details-providers.png)

#### Watchlist Page

![Watchlist Page](/images/watchlist-page.png)

<hr />

## Testing

We tested the following parts of the system:

- Login API
- Registration API
- Watchlists API
- Frontend UI elements

For each of these parts, we incldued both functional and non-functional cases. We came up with a functional specification and identified independently testable features for these parts. This resulted in a good range of test cases.

We performed static verification and inspections on every pull request before changes were merged into the main codebase as part of the code review process. This was a complete and systematic process that allowed us to thoroughly consider program behaviors. For this, we considered both black-box testing and white-box testing. We inspected if the code did what it was expected to do and tested the system as a user to ensure it met the requirements.

We ran unit and integration tests using Jest. The tests were run on both pull requests and commits to the main branch using GitHub Actions. This allowed us to catch errors that were not seen as part of the inspections. In addition, deployment tests were run on commits to the main branch to verify the application was deployed correctly. This allowed us to prevent adding breaking changes to the existing code as they were be caught these tests.

We also performed acceptance testing and regression testing once the core requirements were met. This allowed us to test the system as a user thoroughly and verify if we met all the user requirements specified in the Requirements.

Some parts of the product that were not tested are as follows:

- **Movies Search and Details API**

  These APIs use [The Movie DB API](https://developers.themoviedb.org/) and we assume the results retrieved from the 3rd party API are always valid. We do not have the resources to ensure the results returned by the API are correct. Hence, we simply assume that they always return the correct result.

<hr />

## Team Contribution

| Component | Feature                       | Assignee         |
| --------- | ----------------------------- | ---------------- |
| Front end | Authentication Pages          | Daniel Hsing     |
| Front end | Search Page                   | Ishan Baniya     |
| Front end | Movie Details                 | Ishan Baniya     |
| Front end | Watchlist Page                | Daniel Hsing     |
| Back end  | Authentication APIs           | Ana Sofia Arias  |
| Back end  | Watchlist APIs                | Martin Heberling |
| Back end  | Movie Search and Details APIs | Preston Lee      |

<hr />

## Technologies

| Component       | Techologies and Tools                                                                                                                  |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Front end       | React, CSS                                                                                                                             |
| Back end        | Node.js, Express                                                                                                                       |
| Database        | MongoDB                                                                                                                                |
| Testing         | Jest                                                                                                                                   |
| Deployment      | GCP Cloud Run, Docker, GCP Container Registry, GitHub Actions                                                                          |
| Version control | GitHub                                                                                                                                 |
| API Services    | [The Movie DB](https://developers.themoviedb.org/3/getting-started), [JustWatch](https://www.justwatch.com/us/JustWatch-Streaming-API) |
