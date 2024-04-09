# Structure of Relational Databases

It consistes of a collection of **tables**. Each row records information about one entity (or, in other words, a relation between all the data of the columns) belonging to that table, and, each column belongs to one "attribute". Moreover, each table has a column or "attribute" known as the **primary key**. The value stored in this column will be unique for each row on the table, and therefore, we could say that we can access a concrete row by using this unique key.

But, this primary key will not necessary be in all the tables. Therefore, more than one column could be a primary key, so then we can ensure that what's unique is the combination of this column. This primary key is not compulsory.

Tables can also be used to establish relationships (between other tables or between the elements of the same table). A relationship between *n* values is represented mathematically by an *n-tuple* of values (or, a tuple of *n* that corresponds to a row in the table). The term **relation instance** is used to refer to a specific instance of a relation. Therefore, a table of **u** with 10 rows contains 10 **u** instances.

For each attribute of a relation, there's a set of permitted values called the **domain** of that attribute. A domain is **atomic** if elements of the domain are considered to be indivisible units. The **null value** is a special value that determines that the value is unknown or does not exist. 

# Database schema

We must differentiate between the **database schema**, that's the **logical design** of the database and the **database instance**, which is a snapshot of the database at a given instant of time. The concept of a **relation schema** corresponds to the programming-language notion of type definition. A relation schema consists of a list of attributes and their corresponding domains.

# Keys

