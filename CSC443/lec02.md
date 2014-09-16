First Homework Assignemnt
=========================

##### Must be able to:
- Scan all records (select)
- Insert
- Delete
- Update

##### record Serialization
...

Indexing
========

##### Intro
- Lets you find specific files fast.
- Uses data enetries - <key, value> or k*
    - THe value can be the record, the record id or a set of record ids.
    - e.g. rid points to page where area of page points to offset of record on the page.
- Simplest form is a file with every existing value of a key, we had a rid.
    - Smaller to scan than records.
    - Good if it doesn't change much, otherwise resort on insert and delete....oh god.
- B+ tree is an index designed for dynamic files, much more effeciently. We want constant time!
    - Internal nodes are made of page pointers and key values.
        - Left arow less than, right arrow is greater than or eqaul to.
    - Add/Delete/Reogranize based ofn books/notes.

##### Hush function
#- Bucketing stuff.
#    - Linked list or directory based collisions.
#    - Pick buckets to avoid too many collisions.
#    - Grow by +1 dgiit. 00 -> 100, 000.
     - Skewed deta means we keep doublingg. ineffecient.

##### Static Hashing
- Overflow pages or osemthing liek that to store extra.
- Can't get rid ofo lots of skew on one value but it can for close files.

##### Linear Hashing
#- More distributed.


##### Extendible Hashing
- Cost split instead of all at once.

Sorting
=======

- Naive 3 page algorithm to compare 2 pages at a time to create n sorted pages of saize 1 page, n/2 sorted pages of size 2 .....untiil we have 1 sorted page of size n pages.
- Better version uses B pages to get more done faster.
    - Pass 0 gets runs of length B pages
    - Pass 1 merges B-1 pages for length B(B-1).
    - Log_2 -> Log_(B-1)
    - e.g.
```SQL
Select distinct Sname
From Students
Order by Sname
```
    - In that case we don't need to write all the info in temp files of sort, only the Sname.
        - Distinct will pass back sorted data as it needs to sort to ensure that.
