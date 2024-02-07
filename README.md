![Test Status](../../workflows/test/badge.svg)

# guitar_shack_part1_java


Jason’s Guitar Shack

I’m a retired international rock legend who has invested his money in a guitar shop. 
My ex-drummer is my business partner, and he runs the shop, while I’ve been a kind of silent partner. 
My accountant has drawn my attention to a problem in the business. 
We have mysterious gaps in the sales of some of our most popular products.

I can illustrate it with some data I pulled off our sales system:
| Date       | Time  | Product ID | Quantity | Price Charged |
|------------|-------|------------|----------|---------------|
| 13/07/2019 | 10:47 | 757        | 1        | 549           |
| 13/07/2019 | 12:15 | 757        | 1        | 549           |
| 13/07/2019 | 17:23 | 811        | 1        | 399           |
| 14/07/2019 | 11:45 | 449        | 1        | 769           |
| 14/07/2019 | 13:37 | 811        | 1        | 399           |
| 14/07/2019 | 15:01 | 811        | 1        | 399           |
| 15/07/2019 | 09:26 | 757        | 1        | 549           |
| 15/07/2019 | 11:55 | 811        | 1        | 399           |
| 16/07/2019 | 10:33 | 374        | 1        | 1199          |
| 20/07/2019 | 14:07 | 449        | 1        | 769           |
| 22/07/2019 | 11:28 | 449        | 1        | 769           |
| 24/07/2019 | 10:17 | 811        | 2        | 798           |
| 24/07/2019 | 15:31 | 811        | 1        | 399           |
Product sales for 4 selected guitar models

We sell one or two of these a day, usually. 
But if you check out the sales data, you’ll notice that between July 15th and July 24th, we didn’t sell any at all. 
These gaps appear across many product lines, throughout the year. 
We could be losing hundreds of thousands of pounds in sales.

After some investigation, I discovered the cause, and it’s very simple: we keep running out of stock.

When we reorder stock from the manufacturer or other supplier, it takes time for them to fulfil our order. 
Every product has a lead time on delivery to our warehouse, which is recorded in our warehouse system.

| Description                                                      | Price (£) | Stock | Rack Space | Manufacturer Delivery Lead Time (days) | Min Order |
|------------------------------------------------------------------|-----------|-------|------------|----------------------------------------|-----------|
| Fender Player Stratocaster w/ Maple Fretboard in Buttercream     | 549       | 12    | 20         | 14                                     | 10        |
| Fender Deluxe Nashville Telecaster MN in 2 Colour Sunburst       | 769       | 5     | 10         | 21                                     | 5         |
| Ibanez RG652AHMFX-NGB RG Prestige Nebula Green Burst (inc. case) | 1199      | 2     | 5          | 60                                     | 1         |
| Epiphone Les Paul Classic In Worn Heritage Cherry Sunburst       | 399       | 22    | 30         | 14                                     | 20        |

Product supply lead times for 4 selected guitars

My business partner – the store manager – typically only reorders stock when he realises we’ve run out (usually when a customer asks for it, and he checks to see if we have any). 
Then we have no stock at all while we wait for the manufacturer to supply more, and during that time we lose a bunch of sales. 
In this age of the Electric Internet, if we don’t have what the customer wants, they just take out their smartphone and buy it from someone else.

This is the business problem you are tasked with solving: minimise lost sales due to lack of stock.

There are some wrinkles to this problem, of course. 
We could solve it by cramming our warehouse full of reserve stock. 
But that would create a cash flow problem for the business, as we have bills to pay while products are gathering dust on our shelves. 
So the constraint here is, while we don’t want to run out of products, we actually want as few in stock as possible, too.

The second wrinkle we need to deal with is that sales are seasonal. 
We sell three times as much of some products in December as we do in August, for example. 
So any solution would need to take that into account to reduce the risk of under- or over-stocking.

So here’s the exercise for a group of 2 or more:

* Nominate someone in your group as the “customer”. They will decide what works and what doesn’t as far as a solution is concerned.
* Working with your customer, describe in a single sentence a headline feature – this is a simple feature that solves the problem. (Don’t worry about how it works yet, just describe what it does.)
* Now, think about how your headline feature would work. Describe up to a maximum of 5 supporting features that would make the headline feature possible. These could be user-facing features, or internal features used by the headline feature. Remember, we’re trying to design the simplest solution possible.
* For each feature, starting with the headline feature, imagine the scenarios the system would need to handle. Describe each scenario as a simple headline (e.g., “product needs restocking”). Build a high-level test list for each feature.
* The design and development process now works one feature at a time, starting with the headline feature.
  * For each feature’s scenario, describe in more detail how that scenario will work. Capture the set-up for that scenario, the action or event that triggers the scenario, and the outcomes the customer will expect to happen as a result. Feel free to use the Given…When…Then style. (But remember: it’s not compulsory, and won’t make any difference to the end result.)
  * For each scenario, capture at least one example with test data for every input (every variable in the set-up and every parameter of the action or event), and for every expected output or outcome. Be specific. Use the sample data from our warehouse and sales systems as a starting point, then choose values that fit your scenario.
  * Working one scenario at a time, test-drive the code for its core logic using the examples, writing one unit test for each output or outcome. Organise and name your tests and test fixture so it’s obvious which feature, which scenario and which output or outcome they are talking about. Try as much as possible to choose names that appear in the text you’ve written with your customer. You’re aiming for unit tests that effectively explain the customer’s tests.
  * Use test doubles – stubs and mocks – to abstract external dependencies like the sales and warehouse systems, as well as to Fake It Until You Make it for any supporting logic covered by features you’ll work on later.

And that’s Part I of the exercise. 
At the end, you should have the core logic of your solution implemented and ready to incorporate into a complete working system.


A copy of the sample data is part of this project, see guitar_sha-_data.xlsx.
Stick close to it when discussing examples, because this is the data that your system will be consuming in Part II of this kata, which I’ll hopefully write up soon.
