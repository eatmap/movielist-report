## MovieList

Project report for MovieList.

### Requirements

The project topic and functionality were open-ended. The goal was to use the experience gained from Project 1 to create a new application.

### Plan

We decided to make a web application allowing a user to make a watchlist of movies. The system would require a user to login/register to the application before granting access to a movie search and watchlist. Given the project time period of around one month, our primary goal was to create a working prototype with the basic functionality. Other goals for the project included practicing the software development cycle (specifically Agile methodology), building upon our teamwork and collaboration skills, and using the various software tools we have learned in class as well as other tools not used in the previous project.

### Design

MovieList has a login and registration system. Once a user has registered and logged in, they will have access to the search and watchlist page. On the search page, the user can find movies using the search filters and add or remove them from the watchlist. The filters include keywords, release year, ratings, genres, and certifications. On the watchlist page, the user can see movies on their watchlist and add or remove them. By clicking a movie on either list, the user can view details such as description and streaming service providers. When the user is done using the application, they can log out and their watch list will be saved.

#### Software Technologies:

* Front end: React, CSS
* Back end: Node.js, Express
* Database: MongoDB
* Testing: Jest
* Deployment: GCP Cloud Run, Docker, GCP Container Registry, GitHub Actions
* Version control: GitHub
* API Services: The Movie DB, Guidebox

#### Frontend:

#### Backend:

### Testing

Testing for integration and deployment was done through GitHub Actions. Integration tests were run on both pull requests and commits to the main branch. Deployment tests were run on commits to the main branch. 

### Team Contribution

#### Frontend:

* Authentication Pages: Daniel Hsing
* Search Page: Ishan Baniya
* Movie Details: Ishan Baniya
* Watchlist Page: Daniel Hsing

#### Backend:

* Authentication APIs: Ana Sofia Arias
* Watchlist APIs: Martin Heberling
* Movie Search and Details APIs: Preston Lee

### Demo Link

https://bit.ly/cs3300-movielist

