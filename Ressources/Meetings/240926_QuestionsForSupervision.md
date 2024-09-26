## Supervision [DATE]

### Questions

**Qustions: Deployment**
1. Is it possible to have a test environment where we can deploy and then refactor the repositories in parallel?
2. What is the status of the Raspberry Pi setup? Can we rent from Dasya?
3. Should we spin up Docker containers for each framework? Then we can just grab the image, run `docker-compose up' and that's it? (Usage of docker containers in general)


**Questions: Refactoring**

4. For the static files, using global static files across all frameworks - is that a good or bad idea?
5. Would it be smart to store timestamps in a UNIX format?
6. Do we need to cache user information such as cookies? Some repositories do, some don't. (Most of them do)

**Questions: Testing and Lab Experiment**

7. Can we get an example script for managing different Python versions?
8. We test our services using a bash script that spins up the service, runs tests, purges the DB and spins down the service. Would it be wise to create a similar process for the actual experiment?
9. Should we use a Makefile or a Bash script? A Makefile can, in theory, be a set of bash scripts.
10. Would it be good to store the output in a specific format (e.g., .csv) or use a smart architecture?
11. Should we have physical storage for the hardware, and how should we trigger it?

**Questions: General**

1.  What is the date for the thesis defense?
