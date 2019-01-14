# islandora_verify_ingest
This is a set of simple scripts to check that all files were ingested into Islandora correctly.

## [Page Count & Matching - page_count_matching.sh](page_count_matching.sh)
1. Checks if collection is reachable
2. Counts pages on filesystem
3. Gets PIDs of all of the books within the collection
4. Downloads all of the MODS files for the books (not pages)
5. Compares page counts by physical ID
6. List PIDs with mismatched page counts
7. List the number of books on filesystem vs in Solr
8. List the number of pages on filesystem vs in Solr
9. Summarize all file types with count from filesystem

### To run
```bash
$ ./page_count_matching.sh collection_name "/absolute/path/to/books/collection/lobsterBatch*/delivery/*/*"
#                              └── Name of collection in islandora   │
#                                                                    └── Path to original files
```
__NOTE__: using a find pattern for path requires __"__Double quotes __"__ wrapped around the path

### For help
```bash
$ ./page_count_matching.sh -h
# OR
$ ./page_count_matching.sh --help
```
![screen shot of help](https://user-images.githubusercontent.com/2738244/51134866-b2ca8d00-1806-11e9-8c4c-9fddf02b5f62.png)

### output
```bash
'Found some issues with these PIDS with mismatched page count'
vanvactor:1361

'Books found on filesystem | Books found in Solr'
                       475 | 475

'Pages found on filesystem 	| Pages found in Solr including PDFs 	| Solr Records expected Page Count including PDFs'
12431              			| 12431                  				| 12431

'Summary of files on filesystem'
    1 pdf
12431 tif

```
![screen shot of the entire output](https://user-images.githubusercontent.com/2738244/51134808-8adb2980-1806-11e9-8ec6-1d1ac23b217e.png)
