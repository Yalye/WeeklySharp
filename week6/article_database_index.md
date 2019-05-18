
### Database Index
 * Dense index: every record in the data file has an index entry
 * Sparse index: only some records in the data file have index entry
 * Primary index: a primary index sorts the data file by its search key, don't have to be the primary key
 * Secondary index: not like primary index, it doesn't determince the organization of the data files.
 * single-level index: only one index level
 * multi-level index: several levels of indexes on the same file

### Primary index versus Secondary index
 * we can have multiple secondary indexes, but only one primary index.
 * insertion/deletion are more efficient for secondary index, for we don't have to reorder the index structure to maintain the index order. 
 * both index can be used for point lookups and range queries, but range queries are faster for primary index because of less I/O access.

### Dense index versus Sparse index
 * sparse index is much more space efficient than a dense index
 * finding a record using a dense index is more efficient because of not accessing the data file.













