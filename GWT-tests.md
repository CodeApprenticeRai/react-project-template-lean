**New clients can register to access OBS**

Scenario: A client with no account successfully signs up for an account

Given: A client has not registered for OBS

When: The client opens the registration page AND enters a unique username AND a valid password (at least an 8 character long)

Then: The client sees a confirmation AND is redirected to the log in page
<br>
<br>
<br>
Scenario: A client with no account unsuccessfully signs up for an account because the username exists

Given: A client has not registered for OBS

When: The client opens the registration page AND enters an existing username AND a valid password (at least an 8 character long)

Then: The client sees a message saying the username already exists AND is prompted to register again
<br>
<br>
<br>
Scenario A client with no account unsuccessfully signs up for an account because the password is invalid

Given: A client has not registered for OBS

When: The client opens the registration page AND enters a unique username AND an invalid password (not at least 8 characters long)

Then: The client sees a message saying the password is invalid AND is prompted to register again
<br>
<br>
<br>
**Authed users can view their OBS dashboard**

Scenario: A client who is logged or has logged in can view their dashboard information/functionality

Given: A client has successfully logged in with an auth token

When: The client is redirected to the dashboard page

Then: The client can view Account management to add an account (if they have less than 3 current accounts) AND view the 5 OBS managed shares’ prices AND view their accounts (shares held, funds, & account value) AND view their net worth AND view the logout button
<br>
<br>
<br>
**Non-authed users cannot view a dashboard or engage stock transactions**

Scenario: A user has authenticated through log in but cannot make a new account because their token has expired

Given: A client has successfully logged into their dashboard AND the token has expired after 30 minutes

When: The client tries to manage an account

Then: The client is redirected to the login page AND sees a message saying their session has expired
<br>
<br>
<br>
Scenario: A user has authenticated through log in but cannot open/interact with an account because their token has expired

Given: A client has successfully logged into their dashboard AND the token has expired after 30 minutes

When: The client tries to open an account to buy/sell/add funds to that account

Then: The client is redirected to the login page AND sees a message saying their session has expired
<br>
<br>
<br>
Scenario: A user tries to access the dashboard page without logging in to be authenticated 

Given: A user has not authenticated through log in 

When: The client tries to access the dashboard page

Then: Client will see the message "Empty dashboard, please login"
<br>
<br>
<br>
**OBS dashboard displays current stock prices for Bank Inc stocks with client portfolio information**

Scenario: A user is logged in and visits the dashboard to see their information

Given: Client is logged in

When: Client opens the dashboard

Then: The client sees current stock prices for Netflix, Google, Facebook, Apple, Amazon. The client also sees the number of stocks owned for each, individual account balances, and a total balance.
<br>
<br>
<br>
Scenario: A user is logged in and wants to see the latest stock prices

Given: Client is logged in and on the dashboard

When: Client clicks the refresh prices button

Then: The stock prices shown to the user will update to the latest price
<br>
<br>
<br>
Scenario: A user is logged in and wants to see their recent transactions for one account

Given: Client is logged in and on the dashboard

When: Client selects the tab for an existing account of their choice

Then: The client will be shown a table showing transaction history involving the selected account. Each entry (transaction) in the table will have the following fields: name of the stock, type of transaction (buy/sell), number of stocks, total transaction cost, and time of transaction.
<br>
<br>
<br>        
Scenario: A user is logged in and makes a stock purchase or sells a stock

Given: Client is logged in and on the dashboard

When: Client selects the tab for an existing account, and purchases a stock or sells a stock

Then: The client will see the table named ‘Transaction History’ update to show the most recent transaction. The number of stocks owned fields and account balances fields in the dashboard also change to reflect the purchase made.
<br>
<br>
<br>    
**Clients must input valid username/password combination or given an error message when logging in**

Scenario: A registered user attempts to login in with valid credentials

Given: Client has previously registered for an OBS account

When: Client visits the login page and submits an existing username/password combination

Then: Client is redirected to the dashboard page
<br>
<br>
<br>        
Scenario: A registered user attempts to login with invalid credentials

Given: Client has previously registered for an OBS account

When: Client visits the login page and submits a non-existent username/password combination

Then: Client stays on the login page and a message is displayed: “Username or password not found”
<br>
<br>
<br>

Scenario: An unregistered user attempts to login with invalid credentials

Given: Client has not previously registered for an OBS account

When: Client visits the login page and submits a non-existent username/password combination

Then: Client stays on the login page and a message is displayed: “Username or password not found”
<br>
<br>
<br>
**Authed user cannot purchase shares at a cost greater than the cash held in the account**

Scenario: A logged in User has an account with enough funds to buy a specified amount of stock

Given: A Client is currently authorized AND has an existing account AND the account has funds already

When: The Client tries to buy stocks with that specific account

Then: The Client sees a confirmation message that the purchase went through AND the transaction is logged to the database
<br>
<br>
<br>
Scenario: A logged in User has an account with no funds and tries to buy any supported stock

Given: A Client is currently authorized AND has an existing account AND the account has no funds

When: The Client tries to buy any stock

Then: The Client receives an error message stating the account has insufficient funds AND the attempted transaction is logged
<br>
<br>
<br>
Scenario: An inactive User comes back after their token has expired and tries to buy stock with an account that has funds

Given: A Client is currently not authorized AND has an account AND the account has funds

When: The Client tries to buy any stock

Then: The Client is sent to the Login page to get reauthorized AND the attempted transaction is not logged
<br>
<br>
<br>
Scenario: An inactive User comes back after their token has expired and tries to buy stock with an account that has no funds

Given: A Client is currently not authorized AND has an account AND the account has no funds

When: The Client tries to buy any stock

Then: The Client is sent to the Login page to get reauthorized AND the attempted transaction is not logged
<br>
<br>
<br>
**Authed user can create multiple accounts**

Scenario: A logged in User wants to create a new account, despite having one already opened

Given: A Client is currently authorized AND has not created 3 accounts AND has at least 1 account already

When: the Client chooses to create an account

Then: the Client sees a confirmation message that the new account has been created
<br>
<br>
<br>
Scenario: An inactive User comes back after their token has expired and tries to create a new account

Given: A Client is currently not authorized

When: the Client chooses to create an account

Then: the Client is sent to the Login page to get reauthorized
<br>
<br>
<br>
Scenario: A new User has finished registering and is now trying to create their first account

Given: A Client is currently authorized AND does not have an account created

When: the Client chooses to create an account

Then: the Client sees a confirmation message that the new account has been created
<br>
<br>
<br>
**Authed user can add funds to an account**

Scenario: A logged in User wants to add funds to an existing account

Given: A Client is authorized AND has an existing account

When: The Client chooses to add funds to an account AND provides valid input

Then: That specific account gets updated with the inputted funds
<br>
<br>
<br>
Scenario: A logged in User wants to add funds to a specific account, but has multiple open

Given: A Client is authorized AND has two existing accounts, Account A and Account B

When: The Client chooses to add funds to Account A

Then: Only Account A sees an increase in funds AND Account B stays the same
<br>
<br>
<br>
Scenario: A logged in User wants to add funds to a specific account but typos while adding funds

Given: A Client is authorized AND has an existing account

When: The Client chooses to add funds AND provides invalid input like negative values

Then: The Client receives an error message AND the funds do not get added
<br>
<br>
<br>
Scenario: An inactive User comes back after their token has expired and tries to add funds to an existing account

Given: A Client is not authorized

When: The Client chooses to add funds to an existing account

Then: The Client is redirected to the Login page
<br>
<br>
<br>
**OBS maintains separate cash and stock holdings purchased per account**

Scenario: Bob wants to purchase a stock for his investment account that he is managing for his son Charlie. 

Given:  Time t, where Bob has 3 accounts:  { X, Y, Z }, all with different cash and stock holdings

When: Bob purchases a stock in account X. 

Then: After the purchase is confirmed to be executed, only the cash and stock holdings for account X show values different then what they showed at time t.
<br>
<br>
<br>
Scenario: Bob wants to sell a stock for his investment account that he is managing for his son Charlie. 

Given: Time t, where Bob has 3 accounts:  { X, Y, Z }, all with different cash and stock holdings

Bob holds  j > 0 amount of stock H in  account X. 

When: Bob fills out the required fields and confirms sale of  j amount of stock H in account X. 

Then: After the sale is confirmed to be executed, only the cash and stock holdings for account X show values different then what they showed at time t.
<br>
<br>
<br>
Scenario:  Bob wants to purchase an amount of  stock  H for his investment account that he is managing for his son Charlie. Charlie does not have enough cash to purchase this amount and so Bob must transfer an amount of money from another account to cover this transaction

Given: Time t, where Bob has 3 accounts:  { X, Y, Z }, all with different cash and stock holdings. j, the minimum amount of cash required to purchase a share of H. i, the amount of cash in account X at time t, i < j k, The amount of cash in account Y at time t, k > j

When: : Bob fills out the required fields and confirms transfer of  j amount of cash from account Y to account X. 

Then: Account Y is shown to have k - j  amount of cash and Account X is shown to have i + j amount of cash, 
<br>
<br>
<br>
**Authed users can purchase shares and sell existing shares**  

Scenario: User Bob wants to sell X value of shares of stock G, and purchase X value of shares of H. 

Given: User Bob has more than X value of shares of stock G; Stock G, H are both available for purchase and sale Bob is logged into the site and is currently at the page where stocks can be 

When: Bob purchases a stock in account X. 

Then: After the purchase is confirmed to be executed, only the cash and stock holdings for account X show values different then what they showed at time t. 
<br>
<br>
<br>        
Scenario: User Bob wants to sell X value of shares of stock G, and purchase X value of shares of H.

Given: Stock  H is available for purchase Bob is logged into the site and is currently at the page where stocks can be bought and sold. 

When: Bob purchases a stock in account X. 

Then: After the purchase is confirmed to be executed, only the cash and stock holdings for account X show values different then what they showed at time t. 
<br>
<br>
<br>
**Authed users are not permitted to open more that 3 accounts** 

Scenario: New user Bob wants to open up his first account. 

Given: Bob has no accounts

When: Bob clicks to ‘Add A New Account’ and fill out the account creation form. 

Then: The account is successfully created and shows up where accounts are listed in the application
<br>
<br>
<br>
Scenario: Bob wants to open up a second account. 

Given: Bob has two accounts

When: Bob clicks to ‘Add A New Account’ and fill out the account creation form. 

Then: The account is successfully created and shows up where accounts are listed in the application
<br>
<br>
<br>
Scenario: Bob wants to open up a fourth account. 

Given: Bob has three accounts

When: Bob clicks to ‘Add A New Account’ and fill out the account creation form. 

Then: Bob is prompted with an Error Message explaining that he can only have three accounts. 
