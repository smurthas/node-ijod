## IJoD is Indexed JSON on Disk ##

It is intended to serve as an append only historical data store with basic indexing functionality. All data is stored on disk as raw JSON to be as future proof as possible.

You can only do four things:

1. Append a record
2. Get a record by ID
3. Get records after a given recordID
4. Get records after a value of an indexed field (such as timeStamp)


The basic byte offset record index is in the .index file. The rest of the indices are currently stored in a SQLite database. The intention is that since the indices are merely an optimization for query-ability, they can be stored in a less future proof format (hence SQLite).

Some thoughts: SQLite doesn't seems like a great option because it requires a separate module. Ideally, this should stand alone. Can the indices be built simply in JSON in memory, or even JSON on disk?