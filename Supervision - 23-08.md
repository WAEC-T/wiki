## Supervision 23/08
### Questions
1. #### Should we have one consistent DB management system? Like Postgres or SQLlite??
- Technology does not matter - we decide.
- Two options:
- i. One machine, one server, one db 
- ii. Two machines, two servers, one db. 
- In number one the db operations will take resources and in number two the network communication to the db-server will take resources, vice versa.
- We are not in full control. The influence of the DB is always there but the offset should not matter across frameworks. 

2. #### How to refactor different languages/frameworks in a way that it can be compared? - We can ofc define a structure but languages are built different and it henritance a lot of stuff in the background. Based on the context that languages works differently, how can we work in codebase to allow the fairest possible comparision between the services?

- Systems should be identical from a user perspective.
- Queries across frameworks should look very much the same.
- Implementations should be idiomatic.
- We present the most common of the framework, not neccessarily the most super tiptop efficient one.
- We could have language experts looking at our code and/or stack overflow review.
- - Refine services with experts!

4. #### Should we have a management folder structure including the tests that we will run against the services?

- The are of lower importance
- Use integration tests which Helge sent in Teams
- Each client should run the minitwit_scenario.py
- First thing controller does should be:
- i. clear db
- ii. start scenarios

### Problem statement feedback
- Change sentence with "...standardized...".
- Include something about our methodoly being empirical lab experiment in a controlled environment.


### Misc and small talk
- Vary hardware across runs
- i. We should include one non-arm hardware
- ii. Measurement device should not vary
- iii. We should have three versions of
- Helge will try to get permission from DASYA to use measurement device.
- New meeting: thursdays, fridays perhaps with other guy with the a similar topic.



### Unanswered Questions

5. #### Should we keep all the different services in the same repo separating by folder i.e. >ruby-sinatra / >rust-actix ... and so on?
6. #### How can we deploy the services in the raspberry pi setup? Should we use a bashcript for it? There is an example?
7. #### How many samples we should collect to have a good base?
8. #### What are we running in the clients? Some stress test? Are we gonna test the frontend, api or both? How can we ensure a fair comparison when using the clients? 
