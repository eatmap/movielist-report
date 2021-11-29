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

We had regular hour-long meetings every week (sprint). The goal of this meeting was to discuss the accomplishments from the past sprint and prepare for the upcoming sprint. We broke down the sprint goal into different tasks, assign them amongst us, and ensure everyone has access to the required resources to complete the assigned task and all roadblocks have been resolved. <br />
We used GroupMe for any communications required between the team asynchronously to maintain contact.

<!-- ### Risk Management

#### Risk Identification

| Risk                                        | Probability | Severity | Description                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------- | ----------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Running out of GCP credits                  | Low         | High     | We are using GCP products such as GCP Cloud Run and Container Registry. We could run out of GCP credits due to high usage, and this would affect running our application properly. Worst case scenario, our application could even stop completely.                                                             |
| Inefficient communication                   | Low         | High     | This can lead to conflicts and possibly missing deadlines. Without effective communication, it will be hard to address or tackle any roadblocks that we might encounter.                                                                                                                                        |
| Unauthorized access to pages and API routes | Medium      | High     | We want to limit unauthorized users from using our application. If not, someone else could simply misuse our application for their purpose such as potentially use our APIs to serve their applications.                                                                                                        |
| Poor Code Quality                           | Low         | High     | This can be the result of unoptimized and buggy code. As a result, the application might not be maintainable. Similarly, unoptimized code can rack up the fee on Cloud Run and Contrainer Registry. It can introduce some serious security vulnerabilities that others could potentially exploit to cause harm. |

#### Mitigation Plan

Some steps that we took to mitigate the risks are:

1. Running out of GCP credits

   We are currently using GCP for Cloud Run and Container Registry. These services are not completely free, we might run of our credits over time. Hence it is important that we use these services optimally. We are using cache on client side to reduce the usage of Cloud Run. This improved the performance of our application greatly. In addition, we made sure we allocated only required resources and optimize the application such that new instances are not created unnecessarily to handle increasing user traffic.

2. Inefficient communication

   To promote communication, we constantly checked in with each other to track each other’s progress. Effective communication helped tackle issues quickly and in time. We used chat messages frequently to update each other about the progress and ask for help if required.

3. Unauthorized access to pages and API routes

   Except for authentication API routes and pages, all other routes and pages were made private by default. We used JWT for both authentication and authorization purposes. Anytime a request was made to a private page or a route, we checked for a valid JWT. If JWT is not provided, is invalid, or is expired, the request is rejected.

4. Poor Code Quality

   For each pull request, we did code reviews and changes were committed to the `main` branch after atleast one other team member approved. We used GitHub action to run all existing test to ensure no breaking chages were introduced. -->

<hr />

## Requirements

The project topic and functionality were open-ended. The goal was to use the experience gained from Project 1 to create a new application.

<hr />

## Design

MovieList has a login and registration system. Once a user has registered and logged in, they will have access to the search and watchlist page. On the search page, the user can find movies using the search filters and add or remove them from the watchlist. The filters include keywords, release year, ratings, genres, and certifications. On the watchlist page, the user can see movies on their watchlist and add or remove them. By clicking a movie on either list, the user can view details such as description and streaming service providers. When the user is done using the application, they can log out and their watch list will be saved.

### Frontend:

### Backend:

<hr />

## Testing

Testing for integration and deployment was done through GitHub Actions. Integration tests were run on both pull requests and commits to the main branch. Deployment tests were run on commits to the main branch.

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
