# Entity Soft Reference

## Overview

This addon can be used for referencing entities without a foreign key in the database.

### What is a Soft Reference?

A soft reference is a reference in the data model, which does not create a foreign key in the database as well as not creating referential integrity for it. Instead, it is just a "weak" or "soft" reference to another entity.

#### Example: Customer - Order

Let's take the `Customer <>--> Order` example. A customer can have multiple orders. We model that as an composition in CUBA. This means, that there will be a column `CUSTOMER_ID` in the Order table, which stores the primary key of the customer in the Order Table. For every Order, there is a Customer associated to it.

In the soft reference example, it will be different. There will be a `CUSTOMER_ID` column as well in the Order table. But instead there will be no foreign key association on the database. Instead, the following String will be stored in this soft reference column: `app_Customer."4e4c5ca2-9a6e-43aa-8e67-3572b674f7c0"`.

### Foreign keys are valuable, why would someone not want to have them?

Correct. For pretty much every case, there is no need to use soft references. Since it misses all the cool features of referential integrity, there are a lot of downsides. Why do we still need them? Here is an example:

#### Example: Customer - Order - Comment

Let's assume we want to have a column called "Comment". Comments can be created for a lot of different entities. There can be comments for customers as well as comments for orders, products etc. The common way to handle that in a programming language like Java is that you would create an interface called `Commentable`. This interface marks all classes that want to be commentable as such. Then the Comment class could have a reference to a Commentable object. This is what polymorphism is all about.

However - there is no native equivalent in a relational database. The reason is that when you want to create a foreign key, you need to point it to a destination table. But there is no generic table that you could point to. Instead, you want to point to totally different tables.

For cross-cutting functionality, these soft references can be the solution here.

## Example Usage

To see this application component in action, check out this example: [jmix-entity-soft-reference-example](https://github.com/mariodavid/jmix-entity-soft-reference-example).