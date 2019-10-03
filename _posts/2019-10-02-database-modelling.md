---
layout: default
title: Database Modeling
author: Levi West
---
# Database Modeling
It was immediately clear how to implement Items as an entity, since we were
given all the parameters for them. My next thought was that in an auction,
it's definitely important to keep track of who bids on what, so I figured
that having an entity keep track of bidders would be important. Ultimately, the
details about the people themselves aren't that important, so just a name and
ID suffice. What is important about bidders, in this case, are the bids the make.

From this, I concluded that we would need a table to keep track of bids. Winning bids are decided by both the time they're made and the amount they're worth, so these two elements needed to be columns in that table. As far as relationships, each bid needed to be associated with exactly one bidder and exactly one item.

The auction company wants to keep track of sales as well, so that needs to be represented somehow. I figured that a sale would be best represented as a relationship between an item and a person. Of course, it's theoretically possible for an item to receive no bids, in which case there would be no sale, so this relationship is modeled such that either none or many items can be sold, but each one can only be sold to one person.

![schema]({{site.baseurl}}/assets/img/Auction.png)
![ERD]({{site.baseurl}}/assets/img/auctionERD.png)

I'm not sure that my crows-feet/relationship notation is perfectly accurate, but I think that these models are sufficient for implementing a database that fulfills the client's needs. The only ambiguity I can see is the process by which the winning bid would be determined, but it seems like all the information to do that is already accessible in this model, so I don't think it would be a major issue.
