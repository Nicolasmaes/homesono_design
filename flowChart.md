```mermaid
graph TD
    C[User_VISITOR] --> D(Access the app)
    D --> E[Visit the shop]
    D --> F(contact the manager)
    D --> G(access the FAQ section)
    D --> H(browse product availabilities)
    D --> J(fill the shopping cart)
    D --> K(create a user account)
    K--> |Log in| B[USER_USER]
    B--> M(access the confirmation/payment section)
    B--> N(cancel or edit his booking)
    B--> O(leave review after the rent)
    A--> Q(manage user account)
    A--> R(write the FAQ section)
    A--> S(Managee booking requests)
    A--> P(get message from USERS)
    D--> |Log in| A[USER_ADMIN]