## Questions for Helge

1. Should we have one consistent DB management system? 
Like Postgres or SQLlite??
2. How to refactor different languages/frameworks in a way that it can be compared? - We can ofc define a structure but languages are built different and it henritance a lot of stuff in the background.
3. Based on the context that languages works differently, how can we work in codebase to allow the fairest possible comparision between the services?
4. Should we have a management folder structure including the tests that we will run against the services?
5. Should we keep all the different services in the same repo separating by folder i.e. >ruby-sinatra / >rust-actix ... and so on?
6. How can we deploy the services in the raspberry pi setup? Should we use a bashcript for it? There is an example?
7. How many samples we should collect to have a good base?
8. What are we running in the clients? Some stress test? Are we gonna test the frontend, api or both? How can we ensure a fair comparison when using the clients? 
