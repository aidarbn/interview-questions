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

<details>
<summary>What are clustered and non-clustered indexes?</summary>

**Non-clustered.** The data is present in arbitrary order, but the logical ordering is specified by the index. The data rows may be spread throughout the table regardless of the value of the indexed column or expression. The non-clustered index tree contains the index keys in sorted order, with the leaf level of the index containing the pointer to the record (page and the row number in the data page in page-organized engines; row offset in file-organized engines).

In a non-clustered index,

The physical order of the rows is not the same as the index order.
The indexed columns are typically non-primary key columns used in JOIN, WHERE, and ORDER BY clauses.
There can be more than one non-clustered index on a database table.

**Clustered.** Clustering alters the data block into a certain distinct order to match the index, resulting in the row data being stored in order. Therefore, only one clustered index can be created on a given database table. Clustered indices can greatly increase overall speed of retrieval, but usually only where the data is accessed sequentially in the same or reverse order of the clustered index, or when a range of items is selected.

Since the physical records are in this sort order on disk, the next row item in the sequence is immediately before or after the last one, and so fewer data block reads are required. The primary feature of a clustered index is therefore the ordering of the physical data rows in accordance with the index blocks that point to them. Some databases separate the data and index blocks into separate files, others put two completely different data blocks within the same physical file(s).

[https://en.wikipedia.org/wiki/Database_index](https://en.wikipedia.org/wiki/Database_index)
</details>

<details>
<summary>What are optimistic and pessimistic locks?</summary>

Answer:

Source: [link](link)
</details>
