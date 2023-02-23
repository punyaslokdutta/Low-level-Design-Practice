# Low-level-Design-Practice
Best practices for common LLD questions.
Aim of the project is to create backend APIs 
1. Create main entitities
2. Define relationships(Association , composition , aggregation)
3. Main API request/response structures
4. Spin Up Spingboot Locally and test.
5. Write tests using Mockito/Junit
6. Dockerize & deploy on AWS
7. Swagger for API documentation


## 1. Splitwise (Expense sharing - SpringBoot App)

App Allows users to share an Expense

1. Users will be able to organize expenses among multiple heads and share with multiple users.
2. Users can create a group.
3. Share an expense among the members of group.
4. Send notification to on their share to be paid.
5. Add bank details for transfer of amount.
6. Track paid users.

Use cases

1. Users should be able to register.
2. User creation is idempotent.
3. Registered user should be able to create an expense.
4. Expense has three states

-> Created
-> Pending
-> Settled

Initial state of the expense would be created.
Registered user should be able to create expense group i.e. to be able to add users to expenses.
Bifurcation is custom no need to implement equal sharing. Once the bifurcation is complete the expense state becomes pending.
Provision to extend to provide user notification when someone adds them to the expense.
Users should be able to add their contribution.
Once the settlement is complete from all the users the expense should become "Settled".
Any number of users should be able to create expenses at the same time.
One user should be able to create more than one expense and share it with different set os users.
Expense creator should be able to track their expenses and payments made by users.
Users can settle expense in parts.

The solution should be extendable.
No need to persist data in database. Data can be stored in memory.

Workflow

User creates an expense
Add other users
Share it Move Expense state to pending
Notify
Users contribute
Check if the bill is settled
If so move the expense to settled
