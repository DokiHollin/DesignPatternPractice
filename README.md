# Assignment 2: Design Patterns

## Solutions to the Key Issues

### RAM Issue

#### Flyweight Pattern

- Flyweight: Product
- ConcereteFlyweight: ProductImpl
- FlyweightFactory: ProductFactory

### Too Many Orders

#### Bridge Pattern

- Implementor: Discount
- Concretelmplementor: FlatRateDiscount,BulkDiscount
- Abstraction: Orders,Order,SubscriptionOrder
- RefinedAbstraction: OneTimeOrder,SubscriptionOne

#### Alternative Solution (400 words max)

##### Solution Summary

The solution summary goes here, you should describe what changes you have made to the codebase, be specific to the classes and methods you changed and how.

##### Solution Benefit

How did you solution solve the problem, be brief.

### Bulky Contact Method

#### COR Pattern

- Handler: AbstractHandler
- ConcreteHandler: CarrierPigeonHandler,EmailHandler,MailHandler,MerchandiserHandler,PhoneCallHandler,SMSHandler,ContactHandler
- Client: SPFEAFacade

### System Lag

#### Lazy load Ghost Pattern

- Ghost: CustomerImpl
- Loader : TestDatabase
- Client: SPFEAFacade

### Hard to Compare Products

#### Value Object Pattern

- Value Object: ProductImpl
- Client: Orders

### Slow Order Creation

#### Command Pattern

- Command: Command
- ConcreteCommand: CacheHandler
- Client: SPFEAFacade
- Invoker: SPFEAFacade
- Receiver: Order

## Notes About the Submission
Because the complexity of the assignment, I will breifly explain my pattern one by one.
#### Flyweight Pattern
This one try to avoid to save a lot of double array into every product, so I use a class called ProductFactory to store each datas, so when database create ProductImpl it will not save it inside of the ProductImpl which save the RAM.
#### Bridge Pattern
After implement this pattern the order will be classified as only two types which are Subscription and NoneSubscription(OneTimeOrder), the discount type will be stored inside of the order, and the order can use the logic by simply use the method from the discount type.
#### COR Pattern
This time I creates different contact handler, it's like a link list each handler will responsible for one type which is much more extensible and flexible than before
#### Lazy load Ghost Pattern
The CustomerImpl will now instantiate very quickly, the load function will be called by every get function which make sure the database only access when it needed.
#### Value Object Pattern
I rewrite the equals function and hashcode function, so now when we compare two object it will compare the hascode as well.
#### Command Pattern
Now, the current order will manipulated by the CacheController, when people add product into an order, it will save the current order into the cache, and only access the database when it finalising or remove. The cancel function is important because it can make sure the order back to the original state when we cancel the order. 