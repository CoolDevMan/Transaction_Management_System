## Question 1 - Programming
_We're looking at your programming ability. It must not only work, it should be maintainable._

Let us assume you are a crypto investor. You have made transactions over a period of time which is logged in a [CSV file](https://s3-ap-southeast-1.amazonaws.com/static.propine.com/transactions.csv.zip). Write a command line program that does the following

 - Given no parameters, return the latest portfolio value per token in USD
 - Given a token, return the latest portfolio value for that token in USD
 - Given a date, return the portfolio value per token in USD on that date
 - Given a date and a token, return the portfolio value of that token in USD on that date

The CSV file has the following columns
 - timestamp: Integer number of seconds since the Epoch
 - transaction_type: Either a DEPOSIT or a WITHDRAWAL
 - token: The token symbol
 - amount: The amount transacted

Portfolio means the balance of the token where you need to add deposits and subtract withdrawals. You may obtain the exchange rates from [cryptocompare](https://min-api.cryptocompare.com/) where the API is free. You should write it in Node.js as our main stack is in Javascript/Typescript and we need to assess your proficiency.


## Submission

Please take no more than 7 days to finish. Your answers should comprise of the following

  - Source code that you used for deriving the results
  - README that explains various design decisions that you took.
  
Commit your answers in a private Github repository(it's free) and add Zan(liangzan), Kyle(kyled7), Thanh(thanhnpp), Viswanath(viswanathkgp12) as collaborators. Inform us that it is done at zan@propine.com, kyle.dinh@propine.com, thanh.nguyen@propine.com, viswanath.kapavarapu@propine.com.


## Development (Migel Tom)

1. Getting started
```
npm init
npm i express morgan nodemon ejs body-parser dotenv axios csv-parser
```
  - Create Folders and config file.
    - /assets
      - /css 
      - /csv 
      - /js 
    - /server 
    - /controller 
    - /routes 
    - /services
    - /views 
      - index.ejs
      - /include
    - config.env
    - server.js
  - I used the EJS template engine with ExpressJS.

2. Build the design of this system.
  - /views
  
    index.ejs
    
    /include
    
      _header.ejs (Import css, bootstrap, spinner.)
      
      _form.ejs (Enter token and date.)
      
      _spinner.ejs (loading animation)
      
      _footer.ejs (Import js.)
      
  - /assets/css/style.css (fonts : Barlow, PT+Sans), (Resposive design)

3. Get portfolio (/server/controller/controller.js)
  - Read and parse /assets/csv/transactions.csv with csv-parser npm.
  - The remaining token quantity is calculated based on the transaction history corresponding to the filter condition.
  - Get the USD price corresponding to the token using [cryptocompare](https://min-api.cryptocompare.com/) .
  - Calculate token`s portfolio.

4. Print the portfolio to the screen.(/assets/js/index.js)
  - After sending the filter condition to the controller using ajax, append the return value(portfolio or error) to the screen.

## Run
- install packages
```
npm install
```

- change /assets/csv/transactions.csv file.
  *The size of the specified csv file is too large to commit to the current repository.
  *Excuse me. Please test by replacing the csv file in the current repository.

- run script
```
npm run start
```
