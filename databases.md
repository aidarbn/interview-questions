# Databases

<details>
<summary>What are transaction isolation levels?</summary>

Isolation levels define the degree to which a transaction must be isolated from the data modifications made by any other transaction in the database system. A transaction isolation level is defined by the following phenomena: **Dirty Read**, **Non Repeatable read**, **Phantom Read**.

Based on these phenomena, The SQL standard defines four isolation levels:  

1. **Read Uncommitted** – Read Uncommitted is the lowest isolation level. In this level, one transaction may read not yet committed changes made by other transactions, thereby allowing dirty reads. At this level, transactions are not isolated from each other.
2. **Read Committed** – This isolation level guarantees that any data read is committed at the moment it is read. Thus it does not allow dirty read. The transaction holds a read or write lock on the current row, and thus prevents other transactions from reading, updating, or deleting it.
3. **Repeatable Read** – This is the most restrictive isolation level. The transaction holds read locks on all rows it references and writes locks on referenced rows for update and delete actions. Since other transactions cannot read, update or delete these rows, consequently it avoids non-repeatable read.
4. **Serializable** – This is the highest isolation level. A serializable execution is guaranteed to be serializable. Serializable execution is defined to be an execution of operations in which concurrently executing transactions appears to be serially executing.

[https://www.geeksforgeeks.org/transaction-isolation-levels-dbms/](https://www.geeksforgeeks.org/transaction-isolation-levels-dbms/)
</details>

<details>
<summary>What is an index?</summary>

A database index is a data structure that improves the speed of data retrieval operations on a database table at the cost of additional writes and storage space to maintain the index data structure. Indexes are used to quickly locate data without having to search every row in a database table every time said table is accessed. Indexes can be created using one or more columns of a database table, providing the basis for both rapid random lookups and efficient access of ordered records.

An index is a copy of selected columns of data, from a table, that is designed to enable very efficient search. An index normally includes a "key" or direct link to the original row of data from which it was copied, to allow the complete row to be retrieved efficiently. Some databases extend the power of indexing by letting developers create indexes on column values that have been transformed by functions or expressions. For example, an index could be created on upper(last_name), which would only store the upper-case versions of the last_name field in the index. Another option sometimes supported is the use of partial index, where index entries are created only for those records that satisfy some conditional expression. A further aspect of flexibility is to permit indexing on user-defined functions, as well as expressions formed from an assortment of built-in functions.

[https://en.wikipedia.org/wiki/Database_index](https://en.wikipedia.org/wiki/Database_index)
</details>

<details>
<summary>What kind indexes do you know?</summary>

- Bitmap index
- Dense index
- Sparse index
- Reverse index
- Inverted index
- Primary index
- Secondary index
- Hash index
- Linear hashing

[https://en.wikipedia.org/wiki/Database_index](https://en.wikipedia.org/wiki/Database_index)
</details>
