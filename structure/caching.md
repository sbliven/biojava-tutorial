Local PDB Installations
=======================

BioJava can automatically download and install most of the data files that it needs. Those downloads 
will happen only once. Future requests for the data file will re-use the local copy.

The main class that provides this functionality is the [AtomCache](http://www.biojava.org/docs/api/org/biojava/bio/structure/align/util/AtomCache.html).

It is hidden inside the StructureIO class, that we already encountered earlier.

```java
	Structure structure = StructureIO.getStructure("4hhb");			
```

is the same as

```java
	AtomCache cache = new AtomCache();
	cache.getStructure("4hhb");
```


## Where are the files getting written to?

By default the AtomCache writes all files into a temporary location (The system temp directory "java.io.tempdir"). 

If you already have a local PDB installation, or you want to use a more permanent location to store the files,
you can configure the AtomCache by setting the PDB_DIR system property

<pre>
    -DPDB_DIR=/wherever/you/want/
</pre>

An alternative is to hard-code the path in this way (but setting it as a property is better style)

```java
	AtomCache cache = new AtomCache();

	cache.setPath("/path/to/pdb/files/");
```

## File Parsing Parameters

The AtomCache also provides access to configuring various options that are available during the 
parsing of files. The [FileParsingParameters](http://www.biojava.org/docs/api/org/biojava/bio/structure/io/FileParsingParameters.html)
class is the main place to influence the level of detail and as a consequence the speed with which files can be loaded.

This example turns on the use of chemical components when loading a structure. (See also the [next chapter](chemcomp.md))

```java
	AtomCache cache = new AtomCache();

	cache.setPath("/tmp/");
			
	FileParsingParameters params = cache.getFileParsingParams();
	
	params.setLoadChemCompInfo(true);

	StructureIO.setAtomCache(cache);

	Structure structure = StructureIO.getStructure("4hhb");			

```

## Caching of other SCOP, CATH

The AtomCache not only provides access to PDB, it can also fetch Structure representations of protein domains, as defined by SCOP and CATH, and the algorithms Protein Domain Parser (PDP) and Domain Parser (DP).

```java
	// uses a SCOP domain definition
	Structure domain1 = StructureIO.getStructure("d4hhba_");
	
	// Get a specific protein chain, note: chain IDs are case sensitive, PDB IDs are not.
	Structure chain1 = StructureIO.getStructure("4HHB.A");
	
```

There are quite a number of external database IDs that are supported here. See the 
<a href="http://www.biojava.org/docs/api/org/biojava/bio/structure/align/util/AtomCache.html#getStructure(java.lang.String)">AtomCache documentation</a> for more details on the supported options.






[footer]: # (Automatically generated footer. Don't edit below here.)

---

Navigation:
[Home](../README.md)
| [Book 3: The Protein Structure modules](README.md)
| Chapter 4 : Local installations

Prev: [Chapter 3 : data model](structure-data-model.md)

Next: [Chapter 5 : Chemical Component Dictionary](chemcomp.md)
