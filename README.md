# rails-marketplace-project (Bitcoin Marketplace Au)

## Notes on design choices

Note that this application is purely for demonstrative purposes on how a marketplace might function. Under no circumstances should it be used to facilitate real transactions. 

The exchange of Bitcoin and cryptocurrencies is subject to many strict regulations, most notably the requirement for Know Your Customer/Anti-Money Laundering practices. This typically involves collecting and storing documents identifying and verifying users, attached to their user ID, with verification typically being conducted by a certified KYC provider. Such a process has many legal considerations and is costly, and as such is beyond the scope for this project - i.e. while theoretically this application could work, legally it cannot.

Also to build further trust and facilitate safer exchange of Bitcoin, most Bitcoin Exchange Marketplaces, including Local Bitcoins upon which this application is inspired by, take custody of the Bitcoins being exchanged and hold them in escrow. This allows for easier dispute resolution, provides greater confidence for buyers and sellers and significantly reduces the chances of fraudulent transactions occuring. 

BTC addresses have to be associated with profiles. That way, at least a user would be able to view the address and look for transactions consistent with what seller may be advertising to build trust. Also a system could later be put in where a small tx is sent to the wallet and the funds must be sent back in order to verify ownership of wallet to allow for use on the site. (There are better alternative verification methods available, but at least this allows for this possibility).


## User Stories

This application will assume that all of the users are in Australia, this is to simplify the scope of the application

### MVP level requirements

**User Management/Profiles**

Management:
- As a site visitor, I want to be able to create an account in order to log in and become a buyer and seller.
- As a buyer or seller, I want to be able to enter my email and password to log in.
- As a buyer or seller, I want to be able to logout out of my account at any time.
- As a buyer or seller, I want to be able to delete my account if I no longer want to be a part of the site.
- As a buyer or seller, I want to be able to delete my account in case I change my mind.

Profiles:
- A registered user needs to have a profile picture
- As a buyer or seller, I want to be able to add details to my profile in order to show other users more about me - in order to build trust in people to transact with me
- As a user (buyers will have this), I want to have a Bitcoin address associated with my profile - in order to be used for receiving Bitcoin payments to

**Listings:**

- As a seller, I want to be able to create listings in order to sell my Bitcoin - **only** sellers can create listings

Viewing overview of listings:
- As a site visitor, I want to be able to see an overview of listings without logging in.
- As a buyer, I want to be able see the users name, their payment method(s), price, amount, number of trades they've done and their reputation score + a buy button that takes them to the individual listing page

Listings (view listing) detail page:
- As a buyer, I want to be able to see the users name, their payment method(s), price, the amount, number of trades they've done and their reputation score
- As a buyer, I'd like to enter how much I want to buy (in terms of AUD), and the application calculates and tells me how many BTC that is based on the listing price
- As a buyer, I want to be able to enter the payment details/make the payment for the listing (e.g. make manual deposit according to listing, stripe payment, Paypal payment etc) 
- As a buyer, I would like confirmation that my order/payment has gone through/been accepted 

Creating/editing a listing:
- As Seller creating a listing, I need to be able to specify(upload) a country and a city for the location, the payment method, the Bank name, the price, the amount and the terms of trade
- As a seller creating a listing, I would also like the option of specifying additional payment details (e.g. instructions of how to wire money), minimum feedback score (specify minimum reputation needed to transact)
- As a seller, I want to be able to edit my listings in order to reflect correct information.

Delete:
- As a seller, I want to be able to delete my listings

**Dashboard**

Sellers:
- As a seller, I want to be able to view my current listings in one place in order to keep track of what I am selling.
- As a seller, I want a place to view the orders that have been made, that include the details of how much was sent and provides their address to send the Bitcoin to
- As a seller, I want to be able to mark once the transaction is complete, once I've sent the Bitcoin to the buyer (i.e. order filled) 
- As a seller, I want to be able to view a list of my completed transactions
- On the completed transactions list, I'd like to be able to give a feedback rating to the buyer for that transaction, i.e. one rating per transaction (that goes towards their reputation score) 

Buyers:
- As a buyer, I want to be able to view a list of my pendinng/open orders - i.e. where I have paid for Bitcoin, but order is not yet marked as complete by the seller yet
- As a buyer, I want to be able to view a list of my completed transactions
- On the completed transactions list, I'd like to be able to give a feedback rating to the seller for that transaction, i.e. one rating per transaction (that goes towards their reputation score) 


**Authentication & Authorisation:**
- As a buyer or seller, I do not want other users to be able to access my account in order to keep my data safe.
- As a seller, I do not want other users to be able to edit or delete my listings.
- As a seller, I do not want to see options to buy my own listings.

### Additional stretch requirement user stories (to be attempted after MVP is functional)

**Stretch 1** 

Listings:
- As a buyer, I want to be able to see the current CoinMarketCap price for Bitcoin to compare to the prices listed
- As a buyer, I want to be able to search/filter listings according to how much I want to buy (in dollar terms), and by the payment type

**Stretch 2**

Listings:
- As a seller, I want to be able to set what margin (how much my price differs) I want to have above the market (Coinmarketcap) price and the application will adjust my seller listing price accordingly to maintain the same level of margin as the API price updates (API call made every 10mins/hour or something like that)
- As a buyer, I want to be able to specify the fiat currency I wish to transact in (as opposed to just AUD only) 
- As a seller, I want to be able to specify the fiat currency I wish to transact in (as opposed to just AUD only)
*Start with USD support (users could accept USD, or USD stable coins - Tether, USDC) then expand to other currencies when it makes sense to do so.

**Stretch 3**

Dashboard:
- As a seller, I want to be able to reply to buyers messages in order to answer questions about my listings.
- As a buyer, I want to be able to message sellers about listings in order to find out more information.
- As a buyer or seller, I want to be notified when I receive a new message so I don't have to keep checking my inbox.
- As a buyer or seller, I want to be able to send messages to another user about their listing within an internal messaging system within the app 