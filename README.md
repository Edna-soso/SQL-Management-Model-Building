# SQL-Management-Model-Building
Building a management model of dormitory isolation area A.

## 1. Problem

It is necessary to computerize the management of the isolation area at the dormitory area A, National University of Ho Chi Minh City, which manages Vietnamese citizens returning from abroad as well as those who need to be isolated. With the following information:
- Before being isolated here, the quarantined person must fill out a "Medical declaration for people on entry" with basic information about citizen code, full name, year of birth, address, departure location, departure date. travel, date of entry, within 14 days of showing symptoms of illness: fever, cough, shortness of breath, abdominal pain, etc. For those who do not return from abroad, you can leave the fields blank (NhiDi, NayVe, SoHieuPT. ...). Especially quarantined people will be monitored by GPS system.
- Each quarantined person will be arranged in one room (maximum 4 people). Room codes between buildings may overlap and each building will be managed by the head of the building. The doctor  will test the person in isolation through 2 rounds (1st, 2nd test). The health status of the quarantined person will be updated in the results.
- Each quarantined person is not allowed to leave the isolation area (identified through location). Notify if the person goes beyond the old coordinates by more than 30m.
- At the isolation area, there are staff members who are assigned specific jobs to take good care of the quarantined people here. (meal delivery, security, court management....)

## 2.Goal

- Building an isolation management database to meet the proposed problem, in order to manage effectively and safely.
- Consolidate and improve their knowledge in analyzing, designing and building databases.

## 3.User object

- Dormitory management board
- Ministry of Health
- State apparatus

## 4. Problem Performance

### 4.1 Perception Level: Entity-relationship Model (ER Model)
![image](https://user-images.githubusercontent.com/72458113/131081968-ba06bb62-2011-4d5e-99eb-2edd63e46162.png)


### 4.2 Physical Level
![image](https://user-images.githubusercontent.com/72458113/131082379-9c3bd45c-2b28-45c2-9728-28567ebafc91.png)


## 5. Handing problem math with SQL (file CODE_SQL)
4 steps:
1. Create table and insert data

2. Create stored procedures
  - Import to MaPH to output data: MANCL, TENCEL, MA COVID. If the room just entered is empty, return 0
  - Import old MANCL, MAPH, new MATOA  to export data: MANCL, TENCEL, MA COVID. If the room you just entered is empty, return 0. Please update room, new building for that person isolated . If no found found return return 0

3. Trigger:
  - Create trigger return date about must greater than departure date at PHIEKBYT 
  - Create trigger notify when people quarantine leave from the old location more than 30m
  - Create trigger auto-update state covid if XNlan1 or XNlan2 is positive 

4. LOGIN-ROLE: Administration Has All Permission
