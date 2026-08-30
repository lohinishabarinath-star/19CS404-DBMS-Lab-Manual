# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

<img width="1906" height="850" alt="image" src="https://github.com/user-attachments/assets/bcec784e-d437-4d03-b464-36007d9ea1d3" />


**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="4512" height="2040" alt="erdplus (6)" src="https://github.com/user-attachments/assets/3186ad93-6cab-4d3d-92eb-e986d7ed21b8" />


### Entities and Attributes

| Entity                      | Attributes (PK, FK)                                                      | Notes                                                 |
| --------------------------- | ------------------------------------------------------------------------ | ----------------------------------------------------- |
| **Member**                  | MemberID (PK), Name, MembershipType, StartDate                           | Stores member details                                 |
| **Program**                 | ProgramID (PK), ProgramName, Duration                                    | Fitness programs such as Yoga, Zumba, Weight Training |
| **Trainer**                 | TrainerID (PK), Name, Phone, Specialization                              | Trainers working in the gym                           |
| **PersonalTrainingSession** | SessionID (PK), MemberID (FK), TrainerID (FK), Date, Time                | Personal training sessions booked by members          |
| **Attendance**              | AttendanceID (PK), SessionID (FK), Status                                | Records attendance for each training session          |
| **Payment**                 | PaymentID (PK), MemberID (FK), SessionID (FK), Amount, Date, PaymentType | Tracks membership and session payments                |


### Relationships and Constraints

| Relationship                             | Cardinality | Participation            | Notes                                                                           |
| ---------------------------------------- | ----------- | ------------------------ | ------------------------------------------------------------------------------- |
| **Member – Program**                     | M:N         | Partial on both sides    | A member can join multiple programs and a program can have multiple members     |
| **Program – Trainer**                    | M:N         | Partial on both sides    | A program can have multiple trainers and a trainer can handle multiple programs |
| **Member – PersonalTrainingSession**     | 1:M         | Total on Session side    | A member can book multiple personal training sessions                           |
| **Trainer – PersonalTrainingSession**    | 1:M         | Total on Session side    | A trainer can conduct multiple personal training sessions                       |
| **PersonalTrainingSession – Attendance** | 1:1         | Total on Attendance side | Each session has an attendance record                                           |
| **Member – Payment**                     | 1:M         | Total on Payment side    | A member can make multiple payments                                             |
| **PersonalTrainingSession – Payment**    | 1:M         | Partial on Payment side  | A session may have payment records                                              |


### Assumptions

A member can join multiple fitness programs, and a program can have multiple members.

A personal training session involves one member and one trainer.

Each attendance record belongs to one personal training session.

Payments can be made for memberships or personal training sessions.
---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="4512" height="2040" alt="erdplus (7)" src="https://github.com/user-attachments/assets/62175d5d-95c1-40ea-aa45-c776fe7152b9" />



### Entities and Attributes

| Entity                | Attributes (PK, FK)                                                       | Notes                                 |
| --------------------- | ------------------------------------------------------------------------- | ------------------------------------- |
| **Member**            | MemberID (PK), MemberName, Email, Phone                                   | Stores library member details         |
| **Book**              | BookID (PK), Title, Author, Category                                      | Stores book details                   |
| **Loan**              | LoanID (PK), MemberID (FK), BookID (FK), LoanDate, ReturnDate, FineAmount | Tracks book lending and overdue fines |
| **Event**             | EventID (PK), EventName, EventDate, RoomID (FK)                           | Stores library event details          |
| **Speaker**           | SpeakerID (PK), Name, Specialization                                      | Stores event speaker/author details   |
| **Room**              | RoomID (PK), Capacity, Purpose                                            | Rooms used for events and study       |
| **EventSpeaker**      | EventID (PK, FK), SpeakerID (PK, FK)                                      | Connects events and speakers          |
| **EventRegistration** | RegistrationID (PK), MemberID (FK), EventID (FK)                          | Records members registered for events |


### Relationships and Constraints
| Relationship                   | Cardinality | Participation         | Notes                                           |
| ------------------------------ | ----------- | --------------------- | ----------------------------------------------- |
| **Member – Loan**              | 1:M         | Total on Loan         | A member can borrow multiple books              |
| **Book – Loan**                | 1:M         | Total on Loan         | A book can have multiple loan records over time |
| **Member – EventRegistration** | 1:M         | Total on Registration | A member can register for multiple events       |
| **Event – EventRegistration**  | 1:M         | Total on Registration | An event can have multiple registered members   |
| **Event – EventSpeaker**       | 1:M         | Total on EventSpeaker | An event has one or more speakers               |
| **Speaker – EventSpeaker**     | 1:M         | Total on EventSpeaker | A speaker can participate in multiple events    |
| **Room – Event**               | 1:M         | Total on Event        | A room can host multiple events                 |

### Assumptions
A member can borrow multiple books, but each loan record refers to one book.

A member can register for multiple events, and an event can have multiple registered members.

Each event is assigned to one room and has one or more speakers.

FineAmount is calculated for overdue books and stored in the Loan entity.
---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="4512" height="2040" alt="erdplus (8)" src="https://github.com/user-attachments/assets/d7e91d8b-0f4e-446c-9337-e9e0ce2ca687" />


### Entities and Attributes

| Entity          | Attributes (PK, FK)                                                                                           | Notes                               |
| --------------- | ------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| **Customer**    | **CustomerID (PK)**, Name, Email, Contact                                                                     | Customer details                    |
| **Table**       | **TableID (PK)**, Capacity, Status                                                                            | Restaurant table details            |
| **Reservation** | **ReservationID (PK)**, CustomerID (FK), TableID (FK), WaiterID (FK), Date, Time, NoOfGuests, ReservationType | Reservation or walk-in              |
| **Waiter**      | **WaiterID (PK)**, Name, Contact, Shift                                                                       | Waiter serving the reservation      |
| **Order**       | **OrderID (PK)**, ReservationID (FK), OrderTime                                                               | Food order placed for a reservation |
| **OrderItem**   | **OrderID (PK, FK)**, DishID (PK, FK), Quantity                                                               | Individual dishes in an order       |
| **Dish**        | **DishID (PK)**, DishName, Price, Category                                                                    | Starter, Main, or Dessert           |
| **Billing**     | **BillID (PK)**, ReservationID (FK), FoodAmount, ServiceCharge, TotalAmount                                   | Bill generated for a reservation    |


### Relationships and Constraints

| Relationship                          | Cardinality | Participation                      | Notes                                                                                          |
| ------------------------------------- | ----------: | ---------------------------------- | ---------------------------------------------------------------------------------------------- |
| **Customer — MAKES — Reservation**    |   **1 : M** | Reservation: Total                 | A customer can make many reservations; every reservation belongs to one customer               |
| **Table — ASSIGNED TO — Reservation** |   **1 : M** | Reservation: Total                 | A table can be used for many reservations at different times; every reservation uses one table |
| **Waiter — SERVES — Reservation**     |   **1 : M** | Reservation: Total                 | A waiter can serve many reservations; every reservation is assigned to one waiter              |
| **Reservation — HAS — Order**         |   **1 : M** | Order: Total, Reservation: Partial | A reservation may have multiple orders; an order belongs to one reservation                    |
| **Order — CONTAINS — OrderItem**      |   **1 : M** | OrderItem: Total                   | One order contains multiple dishes through order items                                         |
| **Dish — APPEARS IN — OrderItem**     |   **1 : M** | OrderItem: Total                   | A dish can occur in many order items                                                           |
| **Reservation — GENERATES — Billing** |   **1 : 1** | Billing: Total                     | Each reservation generates one bill                                                            |

### Assumptions
ReservationType identifies whether the customer is Reserved or Walk-in.

A walk-in customer is recorded as a reservation/visit when they arrive so that their orders and bill can be linked to the same reservation.

An OrderItem is used because one order can contain multiple dishes, with a separate quantity for each dish.

Each reservation is assigned one table and one waiter, while a table and waiter can serve multiple reservations over time.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
