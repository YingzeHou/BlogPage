# DBMS Notes

{% embed url="https://docs.google.com/document/d/1X_dVoVGJH6fR2RC1bmae-ZCRddc1ht8b1IrLx01mo9M/edit?usp=sharing" %}

### _Transaction_ <a href="#transaction" id="transaction"></a>

Execution of a sequence of operations, basic unit of change in DBMS; No partial transaction is allowed.

### _Strawman System_ <a href="#strawman-system" id="strawman-system"></a>

Sequencial sacrifice parallel <—> Parallel cause possible danger:

* `Temporary Inconsistency`: Unavoidable, not an issue
* `Permanent Inconsistency`: Unacceptable, cause problem with correctness and integrity

### _Definition_ <a href="#definition" id="definition"></a>

Boundaries of transaction defined by the client:\
`BEGIN`: transaction start\
`COMMIT`: all transaction modifications are saved/DBMS overrides this and abort\
`ABORT`: all transaction modifications are undone, looks like the transaction never happens\
`ACID`:

* _**Atomicity**_: Either all changes happen, or all not happen
* _**Consistency**_: If transaction and database at the beginning is consistent, also consistent when transaction finish
* _**Isolation**_: When a transaction is happening, it has illusion of being isolated from other transactions.
* _**Durability**_: If transaction commit, its effect to DBMS is persistent.

### _Atomicity_ <a href="#atomicity" id="atomicity"></a>

1. _**Logging**_: Logs all actions for undo when abort. Maitain undo records on memory and disk
2. _**Shadow Paging**_: DBMS make copies of transaction and change the copy when modification. Copied pages be visible only when commit.

### _Consistency_ <a href="#consistency" id="consistency"></a>

1. _**Database Consistency**_: Real world entities, like age not be negative. Transaction in the future can see effects on past within the databse
2. _**Transaction Consistency**_: If database is consistent before transaction, it should also be consistent after transaction

### _Isolation_ <a href="#isolation" id="isolation"></a>

Concurrency Control:

1. _**Pessimistic**_: DBMS assumes conflict exist, so avoid conflict in the first place.
2. _**Optimistic**_: DBMS assumes conflict rare, so deal with conflict after commit

Execution Schedule:

1. _**Serial Schedule**_: No interleave action
2. _**Equivalent Schedule**_: 1st schedule effect = 2nd schedule effect
3. _**Serializable Schedule**_: == any serial execution of transaction. Different execution –> Different result, but all are correct.

Conflict:

1. _**Read-Write Conflict(Unrepeatable Reads)**_: A transaction not able to get the same value when reading the same object multiple times
2. _**Write-Read Conflict(Dirty Reads)**_: A transaction sees the write effect of another transaction before that other txn is commited.
3. _**Write-Write Conflict(Lost Update)**_: A transaction overwrite the uncommited change of a concurrent txn

Conflict Serializability :

1. _**Conflict Equivalent**_: Involve same operation of same transaction and every pair of conflict operations are in same order. If Schedule A is `Conflict Equivalent` to Schedule B, A can be `Conflict Serialized`.
2. _**Dependency Graph**_: There exists an edge from Ti –> Tj iff an operation Oi conflict with Oj. Schedule is conflict serializable iff the graph is `acyclic`

_ransaction Locks_

1. _**Shared Lock(S-Lock)**_: Allow multiple transactions to read the same object at the same time. If a txn hold the lock, other can still access the lock
2. _**Exclusive Lcok(X-Lock)**_: Prevent other txn from modifying the object. Other txn cannot get both S-Lock and X-Lock

`Lock Manager` is centralized and grants or block request based on what locks are currently held by other txn. NO-NEED to be duriable, since transaction abort when DBMS crash.

### _Two Phase Locking (2PL)_ <a href="#two-phase-locking-2pl" id="two-phase-locking-2pl"></a>

1. _**Phase1: Growing**_: Each txn acquires lock
2. _**Phase2: Shrinking**_: Enter this phase when the first txn free its lock. Txns only release lock.

> 2PL is sufficient to guarantee conflict serializability, but susceptible to `cascading aborts`, when a txn abort but another txn must roll-back.

#### **Strong Strict Two Phase Locking**: <a href="#strong-strict-two-phase-locking" id="strong-strict-two-phase-locking"></a>

Any value written by a txn is never read or overwrite by another txn until the txn first commit. Only release lock when commit.\
Fix `cascading aborts` but limit concurrency

### _Deadlock Handling_ <a href="#deadlock-handling" id="deadlock-handling"></a>

1. _**Deadlock Detection**_: `Wait-for` graph with direct edge from Ti –> Tj if Ti waits for Tj to release the lock.

DBMS pick a victim to abort, using several combinations of heuristic. When aborting a txn, DBMS determine how far to roll-back.

1. _**Deadlock Prevention**_: Kill a txn when two txns are trying to acquire the same lock:
   * _Wait-Die (Old wait for Young)_:If requesting transaction has higher priority than holding transaction, it waits.
   * _Wound-Die (Young wait for Old)_:If requesting transaction has higher priority than holding transaction, it acquire, the holding txn aborts.

### _Lock Granularities_ <a href="#lock-granularities" id="lock-granularities"></a>

Use hierarchy to implicitly assign lock to chidren objects.

#### _Intention Locks_: <a href="#intention-locks" id="intention-locks"></a>

Allow high level node to be locked in shared or exclusive mode, no check on descendent node

* _**Intention-Shared (IS)**_: Explicit locking at lower level with shared locks
* _**Intention-Exclusive (IX)**_: Explicit locking at lower level with shared or exclusive locks
* _**Shared+Intention-Exclusive (SIX)**_: Sub-tree rooted at the node is locked in shared mode, and explicit locking at lower level with exclusive mode

### _Timestamp Ordering Concurrency Control_ <a href="#timestamp-ordering-concurrency-control" id="timestamp-ordering-concurrency-control"></a>

Each transation Ti is assigned with a unique timestamp TS(Ti), monotonically increasing\
If TS(Ti) < TS(Tj) DBMS execute Ti before Tj

* [x] System-Clock: edge case like daylight saving
* [x] Logical-Counter: Overflow and maitanance between multiple machines.

Always a combination of these two.

\
_Basic T/O_

Each object X assigned with the successfully last execution of Read or Write(R-TS(X) & W-TS(X)).Any txn tries to violate the order will abort

* _**Read Operation**_: If TS(Ti) < W-TS(X), violation, cannot read before write; Otherwise, valid, R-TS(X) update to max(R-TS(X), TS(Ti)) —> Copy of X to ensure repeat read for Ti
* _**Write Operation**_ If TS(Ti) < R-TS(X) or TS(Ti) < W-TS(X), Ti must restart; Otherwise, valid, update R-TS(X) and W-TS(X).

### _Optimization: Thomas Write Rule_ <a href="#optimization-thomas-write-rule" id="optimization-thomas-write-rule"></a>

If TS(Ti) < W-TS(X), ignore violation and let Ti continue, since no other txn will read Ti’s write.\
Conflict Serializable for Basic T/O, but may also starvation for long transactions if short transactions keep causing conflict, and permits not `Recovery`: if transactions commits only after all other txns whose change they read from, commit.

### _Optimistic Concurrency Control_ <a href="#optimistic-concurrency-control" id="optimistic-concurrency-control"></a>

Works best when conflicts are low:

* All txns read-only
* Access disjoint subset of data

Each txn has a `Private Space` for read and write. No other txns can access this private space.\
When commit, DBMS check for a txn’s `write-set` for conflicts —> install into global database.

1. _**Read-Phase**_: DBMS tracks read/write sets of txn and store in private space
2. _**Validation-Phase**_: DBMS checks conflict when a txn commits
3. _**Write-Phase**_: If valid, DBMS apply change to global. Otherwise abort & restart the txn.

### _Validation-Phase_ <a href="#validation-phase" id="validation-phase"></a>

Check whether all txns go from older change to younger change;\
If TS(Ti) < TS(Tj):

1. Ti completes all three phases before Tj begin
2. Ti completes before Tj’s write phase, and Ti no write to any object read by Tj.
3. Ti completes read phase before Tj does, and Ti no write to any object read/written by Tj.

### _Isolation Level_ <a href="#isolation-level" id="isolation-level"></a>

_**Anomalies:**_

1. Dirty Read: Reading uncommited data
2. Unrepeatable Read: Redoing a read result differently from another read
3. Phantoms Read: Insertion/Deletion result differently for same range of query scan.

_**Isolation Levels:**_

| Level           | Dirty-Read | Unrepeatable-Read | Phantom-Read |
| --------------- | ---------- | ----------------- | ------------ |
| Serializable    | X          | X                 | X            |
| Repeatable Read | X          | X                 | O            |
| Read-Committed  | X          | O                 | O            |
| Read-Uncomitted | O          | O                 | O            |

Above only focus on 2PL-based DBMS anomalies.

Two additional levels:

1. _**Cursor Stability**_:
   * Between repeatable reads & read-committed.
   * Prevent Lost Update
   * Default in IBM DB2
2. _**Snapshot Isolation**_:
   * Guarantee all txns read the same snapshot of database when start
   * Txn commit only if write do not conflict with any concurrent updates made since the snapshot
   * Susceptible to write skew anomaly.

\
_Multi-Version Concurrency Control (MVCC)_

Allows DBMS to maitain multiple `physical` versions of single `logical` object in database.

* When txn write, DBMS create new version of that object
* When txn read, read the newest version exist

Writer NO block write; Reader NO block read —> Allow modify while other txn read older version.

* _**Time Travel Queries**_: Queries based on state of databse of some arbitrary time point.
* _**Design Decision**_:
  * Concurrency Control Protocol (2PL, T/O, OCC ….)
  * Version Storgae
  * Garbage Collection
  * Index Management

### _Version Storage_ <a href="#version-storage" id="version-storage"></a>

* _**Version Chain**_: Created by tuple’s pointer field —> Linked List of version by timestamp —> Index point to “head” (Newest/Oldest) —> Thread traverse the chain for correct version

1. _**Append-Only Storage**_: All physical versions in one table; Append new version & Update chain;
   * Oldest-to-Newest(O2N) sort: chain traversal for look-ups;
   * Newest-to-Oldest(N2O): update index pointer for new version;
2. _**Time-Travel Storage**_: Seperate table: Time-Travel table <— Older versions. Copy old to main table with new version; Tuple in main table point to older version in time-travel table
3. _**Delta Storage**_: Similar to Time-Travel, only store changes between version (Deltas); Fast in write but Slow in read

### _Garbage Collection_: <a href="#garbage-collection" id="garbage-collection"></a>

Clean `reclaimable`: No active txn can see the version OR Made by txn aborted

1.  _**Tuple-Level GC**_: Direct examine tuples:\
    a. _Background Vacuuming_: Seperate thread periodically scan; Optimization: `Dirty Page Bitmap`: track modified since last scan to skip unchange.

    b. _Cooperative Cleaning_: Worker thread scan when traverse chain; Only for O2N.
2. _**Transaction-Level GC**_: Each txn track their own old version. When txn complete and all older version from the txn not visible, trigger GC by DBMS.

### _Index Management_ <a href="#index-management" id="index-management"></a>

Primary Key (pkey) point to version chain head, If update, treat as DELETE –> INSERT.

Secondary Key Management:

* _**Logical Pointer**_: Map logical ID (Indirection Layer) –> location of tuple: Update Mapping
* _**Physical Pointer**_: Physical address –> version chain head; Update each index

### _History of DBMS_ <a href="#history-of-dbms" id="history-of-dbms"></a>

* IDS: Integrated Data Store:
  * Network data model
  * Tuple-at-a-time queries
* IMS: Information Management System:
  * Hierarchical data model
  * Programmer-defined physical storage format
  * Tupe-at-a-time queries
* Relational-Model:
  * Store database in simple data structures
  * Access data through high-level language
  * Physical storgae left up to implementation
* Object-Oriented Database:
  * JSON & XML
* HTAP: Hybrid Transactional-Analytical Processing:
  * Distributed / Shared-Nothing
  * Relational / SQL
  * Open / Close source

### _On-Disk DBMS_ <a href="#on-disk-dbms" id="on-disk-dbms"></a>

* Storage on non-volatile storgae(HDD, SSD……)
* Organized as a set of fix-length pages
* Buffer pool to cache pages–>Manage movement of pages between disk and memory
  * If no page in memory: Retrive from disk & copy `frame` into its’ buffer pool
  * If no free frame: Find a page to evict
  * If evict page is dirty: Write the page back to disk
* Buffer Pool:
  * Tuple access always in memory
  * Tuple record id–>Memory location
  * Working thread pin pages–>No swap to disk
* Concurrency Control:
  * Txn stall at any time when accessed data not in memory, execute other txm
    * Set Lock ACID
    * Locks in seperate data structure, no swap to disk
* Logging & Recovery:
  * `Steal + No-force` buffer pool policy–>All commit flush to WAL
  * Log read both before & after image
  * Track LSNs in DBMS

### _In-Memory DBMSs_ <a href="#in-memory-dbmss" id="in-memory-dbmss"></a>

#### _Concept and Data Organization_ <a href="#concept-and-data-organization" id="concept-and-data-organization"></a>

Storage location `permanently` in memory –> DRAM

* Not store in slotted pages, but still manage in tuples in block/page
* Direct memory pointer VS record id
* Fixed length VS Variable length data pools
* Use checksum to detect error from trashing the database

Blockid+offset—>Direct mem address of fix-length block—>attributes of tuple—>Variable length data blocks

#### _Index_ <a href="#index" id="index"></a>

* Memory-optimized indexes works worse than B+ tree since they were not cache aware.
* Indexes usually rebuilt when restart to avoid logging overhead

#### _Query Processing_ <a href="#query-processing" id="query-processing"></a>

* Sequential scan are not significantly faster than random access
* Tuple-at-a-time strategy is too slow.

#### _Logging and Recovery_ <a href="#logging-and-recovery" id="logging-and-recovery"></a>

* DMBS need WAL for non-volatile storage
  * Use `group commit` to batch log entry and flush them together to amortize `fsync` cost
  * Possible to use light-weight logging schema
* No “dirty” page, no track on LSNs on whole system.

#### _Concurrency Control_ <a href="#concurrency-control" id="concurrency-control"></a>

A protocol to allow txns to access a database in multi-programmed fashion.\
—>Group of txns=serial txns\
—>Atomicity+Isolation in ACID\
—>Mutex slow: Use Compare & Swap(CAS)



**Two Phase Locking(2PL)**

![](https://yingzehou.github.io/images/img/notes/2PL\_DL.png)

> txns will conflict–>acquire locks before DB access

> Deadlock Detection:
>
> * txn maitain a queure of txn holding locks
> * seperate thread to check the queue
> * if deadlock found, use heuristic(Least Amount of Work) kill txn

> Deadlock Prevention:
>
> * check if the lock requested already hold
> * txn (1) wait, (2) suicide, (3) kill other txn



**Timeastamp Ordering(T/O)**

![](https://yingzehou.github.io/images/img/notes/OCC.png)

> txns will rare conflict–>check conflict when commit

> OCC:
>
> * Store all changes in private workspace
> * Check conflict at commit and merge
> * Copy to private->update private->check conflict->write to global

\
