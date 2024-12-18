# API Sample Test

## Getting Started

This project requires a newer version of Node. Don't forget to install the NPM packages afterwards.

You should change the name of the ```.env.example``` file to ```.env```.

Run ```node app.js``` to get things started. Hopefully the project should start without any errors.

## Explanations

The actual task will be explained separately.

This is a very simple project that pulls data from HubSpot's CRM API. It pulls and processes company and contact data from HubSpot but does not insert it into the database.

In HubSpot, contacts can be part of companies. HubSpot calls this relationship an association. That is, a contact has an association with a company. We make a separate call when processing contacts to fetch this association data.

The Domain model is a record signifying a HockeyStack customer. You shouldn't worry about the actual implementation of it. The only important property is the ```hubspot```object in ```integrations```. This is how we know which HubSpot instance to connect to.

The implementation of the server and the ```server.js``` is not important for this project.

Every data source in this project was created for test purposes. If any request takes more than 5 seconds to execute, there is something wrong with the implementation.


## debrief 

So, taking a look at the project overall, I think we've got a solid base, but there's room for improvement. First off, we can definitely clean up the code by refactoring those process functions into one generic handler, which would cut down on repetition. We'd use parameters to define what we're fetching and a callback for custom actions. Also, let's be consistent with const and use clearer variable names. On the architecture side, adding a service layer for HubSpot interactions would make things more modular and easier to test. We should also think about a repository pattern for our database interactions and externalizing configurations. Performance-wise, batching those API requests, especially for contact emails, is a must. A better queuing system with proper error handling would help a lot too. If we profile the app, we might find some other easy wins, like optimizing database indexes or implementing a persistent connection. It is important to implement it correctly

-- I intentialy didnt touch any other code than requested as it was a deliverate scope with short time frame. So didnt want to create more error 
