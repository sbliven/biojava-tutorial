# Lists of PDB IDs and PDB Status Information

## Get a list of all current PDB IDs

The following code connects to one of the PDB servers and fetches a list of all current PDB IDs.

```java
    SortedSet<String> currentPDBIds = PDBStatus.getCurrentPDBIds();
```     

## The current status of a PDB entry

The following provides information about the status of a PDB entry

```java
    Status status = PDBStatus.getStatus("4hhb");

    // get the current ID for an obsolete entry
    String currentID = PDBStatus.getCurrent("1hhb"); 
```   


[footer]: # (Automatically generated footer. Don't edit below here.)

---

Navigation:
[Home](../README.md)
| [Book 3: The Protein Structure modules](README.md)
| Chapter 14 : status information

Prev: [Chapter 13 : Special Cases](special.md)
