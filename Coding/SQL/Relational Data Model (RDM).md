- A **relation** is essentially a two-dimensional table that represents some *entity* or *relationship*. It is made up of *attributes* and *tuples*.
	- An **entity** is an object, for instance, a student, a car, etc.
	- A **relationship** defines how entities are interconnected.
	- An **attribute** is a column in a relation.
	- A **tuple** is a row in a relation.

- The following **restrictions** are imposed on the **relations** in the relational data model:
	- The *names* of the *relations* must be **unique** in a database.
	- All *attributes* within the same *relation* have to have different names.
	- There should only be one value in each cell.
	- The order of the rows and columns in the relations is not important.

- **Relationships**
	- 1-1: means that one tuple of the first relation can be associated with no more than one tuple of another relation and vice versa.
	- 1-M: means that a tuple of the first relation can be associated with one or more tuples of the second relation, but the opposite is _not true_. A tuple of the second relation can be associated with no more than one tuple of the first relation.
	- M-M: means that any tuple of the first relation can be associated with one or more tuples of another relation. The opposite is also true.
		- It should also be noted that many-to-many relationships do _not exist_ in RDM. It is split into two one-to-many relationships, so that an intermediate _associative_ relation appears, which has two foreign keys as attributes that indicate the primary keys of the original relations.