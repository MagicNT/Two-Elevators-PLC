# PLC Project: 3-Floors Two Elevators

## Objective
Design a two-elevator system for a building with Ground, 1st and 2nd floors.

## Design Description
This design aims at creating a two-elevator system. This is a very effective solution when it comes to solving the transportation question in a relatively high building where stairs are not so efficient. The design’s building is made of three floors: Gf, 1st floor and 2nd floor.

![1](https://user-images.githubusercontent.com/86275885/122986354-b8ccdc80-d375-11eb-9987-81172fbe0721.png)
![2](https://user-images.githubusercontent.com/86275885/122986355-b8ccdc80-d375-11eb-894f-977714c4c40a.png)


Inside the elevator room there are 3 switches available placed on the wall each allowing the client to navigate to the respective floor. On the door there is a laser bean sensor which will detect any object in its pathway and give back a signal. If an object is detected the timer on the door will pause and the elevator doors won’t close until this object is removed from the pathway. It takes the elevator 5s to close its doors and 10s to move from one level to another whether moving up or down.


## Design Interface

### INPUTS
- I1 Down L2
- I3 Go 2nd: E2
- I4 Go 2nd: E1
- I5 Weight: E1
- I6 Sensor: E1
- I7 Up L1
- I8 Down L1
- I9 Go 1st: E2
- IA Go 1st: E1
- IB Weight E2
- IC Sensor E1
- ID Up GF
- IF Go GF E2
- IG Go GF E1
- IH E1 broken


### OUTPUTS
-	Q1 Open E1
-	Q2 Close E1
-	Q3 at L2 E2
-	Q4 at l2 E2
-	Q5 Weight E1
-	Q6 Sensor E1
-	Q7 Open E2
-	Q8 Close E2
-	Q9 L1 E2
-	QA L1 E1
-	QB Weight E2
-	QC Sensor E2
-	QD E1 broken
-	QF GF E2
-	QG GF E1


## Design Logic
-	When any of the outer buttons on each floor are pressed, the elevator will move and arrive to the corresponding floor to serve the client. 
-	The elevator’s initial position is on the Ground Floor.
-	When moving up the elevator will neglect any outer button command from Level 1 where the user wants to go downwards and same applies if the elevator is moving down and a user on floor 1 has commanded a button to go upwards to level 2.
-	It takes 5s for the elevator doors to close on any level and 10s to move from one level to another. 
-	Once the elevator reaches the final level which is level 2, all pressed buttons on the inside will be cleared. 
-	The second elevator will act as a backup in case the main elevator gets broken or in case someone activates the sensor on one of the main elevator’s door for more than 10s.
-	Once the second elevator is at work, it will have the exact same functionalities and logic of the main elevator. 
-	The backup elevator will also become activated in case the main elevator is busy and a person at the GF presses the outer button to go up. However the backup elevator will not response to any direction-conflicting requests. And once it reaches the intended floor level, it will wait for 10s on open doors then come back to GF. 


## Design State Machines

![3](https://user-images.githubusercontent.com/86275885/122986582-02b5c280-d376-11eb-8b7a-6584cf64246f.png)
![4](https://user-images.githubusercontent.com/86275885/122986583-034e5900-d376-11eb-8ed1-24015c33ad0d.png)
![5](https://user-images.githubusercontent.com/86275885/122986587-03e6ef80-d376-11eb-9fa6-120ee28aa2ca.png)
![6](https://user-images.githubusercontent.com/86275885/122986588-03e6ef80-d376-11eb-90bd-04bba485e2b0.png)


## Conclusion
This project implemented a state machine which taught us how to create several state machines and implement synchronized jobs among them all and design a mechanism to link them. It allowed us to dynamically draw a pattern between the different situations and control them efficiently. 

