### Commands to Run a Scenario

#### 1. Connect to `dasya-local` Network

#### 2. Host machine 
**Run**
* sync date: `date`
* Chrony NTP (Network Time Protocol) client  `chronyc makestep`
* pull images: `docker pull simonharwick97822/python-flask`
* check ip adress: `ip route`


#### 3. Client
* make sure the scenario.py is the latest:`scp ./scenario.py root@10.7.7.198:/media/mmcblk0p2`


#### 4. Local Machine 
* Run sequential scenario: `python execution.py . sequential`
* Run client scenario: `python execution.py . berries`




---



