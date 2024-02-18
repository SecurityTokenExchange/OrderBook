# Public Beta - Smart Contract for Order Book Management

Contract Hash
0xa3c5b1c1711e64d3b3eadff83978169763900c0aba3f28669f8f58f637bdef03

Language
ink! 4.3.0

Compiler
rustc 1.76.0

Contract version
6.1.1

Authors
Brian Savelkouls <info@securitytoken.exchange>

## All functions in the contract

new(grandma: Option<AccountId>)
Creates a new contract 
only the developer can create a new instance of this contract (this is not true for the public beta)
use the grandma for data migration of an old contract (this is not enabled for the public beta)
 

init(): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
No documentation provided

getOrderbookSize(ticker: String): Result<Result<u64, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Get the current orderbook size 
only works when the contract is initialized


getOrderById(orderId: u64): Result<Result<OrderbookDataOrder, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Retrieve a single order by ID

createNewOrder(baseTicker: String, quoteTicker: String, baseQty: u128, quoteQty: u128, side: String, gtc: bool, expires: Option<u64>): Result<Result<OrderbookDataOrder, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
No documentation provided

cancelOrder(orderId: u64): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
No documentation provided

updateOrder(orderId: u64, newBaseQty: u128, newQuoteQty: u128): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Update the quantities of an existing order.


getActiveOrders(ticker: String): Result<Result<Vec<OrderbookDataOrder>, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Get all active orders for the given ticker.


countOrdersBySide(ticker: String, side: String): Result<Result<u64, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Count the number of active Buy or Sell orders in the order book.


getOrdersBySide(ticker: String, side: String): Result<Result<Vec<OrderbookDataOrder>, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Retrieve order details based on properties such as side and status.


getLowestSellPrice(ticker: String): Result<Result<u128, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
get lowest sell price


getHighestBuyPrice(ticker: String): Result<Result<u128, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
get highest buy price


takeOrders(ticker: String, takeFrom: OrderSide, amount: u128): Result<Result<Vec<OrderbookDataOrder>, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Return the orders required to fill a specific buy or sell


expireOrders(): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Scan and mark orders as expired based on their timestamps and expiration details. 
This function should be called periodically to ensure that the order book is up to date, and that expired orders are removed.


orderbookManagement(ticker: String, orderId: u64, filledAmt: Option<u128>, newStatus: Option<Text>): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Update the filled amount of an order after a partial trade. 
this message is only callable by a upstream contract


createNewMarket(baseTicker: String, quoteTicker: String, decimalsBase: Option<u8>, decimalsQuote: Option<u8>, assetName: Option<Text>, assetClass: Option<OrderbookDataAssetClass>): Result<Result<OrderbookDataMarket, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Pay the contract to create a new market 
Decimals defaults to 6


getAllMarkets(): Result<Result<Vec<OrderbookDataMarket>, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Retrieves all active markets from the order book.


getMarketInfo(ticker: String): Result<Result<OrderbookDataMarket, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
For a given market ticker, return the market details. 
This also returns when a market is halted.


getMarketOrders(ticker: String): Result<Result<Vec<OrderbookDataOrder>, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Retrieve active orders for a specific market.


getOrdersByUser(user: AccountId): Result<Result<Vec<OrderbookDataOrder>, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Retrieve active orders by a specific accountId.


purgeOrders(): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Purge orders. 
This function allows the admin to remove inactive orders from the blockchain.


updateMarketStatus(ticker: String, halted: bool): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Update the status (halted/active) of a specific market. 
only the admin can call this function


haltTrading(): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
this call allows the admin to halt all trading. 
only the admin is allowed to call this


resumeTrading(): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
this call allows the admin to halt all trading. 
only the admin is allowed to call this


terminateMarket(ticker: String): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Terminate a market and remove its orders.


updateContractCodeHash(codeHash: Hash): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Update the code hash of this smart contract. 
Only the admin is allowed to call this.


nominateAdmin(nominatedAdmin: AccountId): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
This call allows the admin to assign a new admin. 
Only the admin is allowed to call this


acceptAdminRole(): Result<Result<Null, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
This call allows the nominated admin to accept the admin role. 
Only the nominated_admin is allowed to call this


terminate(): Result<Null, InkPrimitivesLangError>
This call allows the admin to terminate the contract 
Value stored in the contract will be transfered to the admin.
Only the admin is allowed to call this


contractDid(): Result<Result<PolymeshApiInkBasicTypesIdentityId, OrderbookDataSecuritytokenexchangeError>, InkPrimitivesLangError>
Get the contract's DID.