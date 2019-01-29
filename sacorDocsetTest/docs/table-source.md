 As you can see, most of the space is used by precreated data and delta files. SQL Server pre-created one pair of (data, delta) files per logical processor. In addition, data files are pre-sized at 128MB, and delta files at 8MB, in order to make inserting data into these files more efficient.  
  
 The actual data in the memory-optimized tables is in the single data file.  
  
#### After running the workload  
 After a single test run that inserts 10 million sales orders, the overall on-disk size looks something like this (for a 16-core test server):  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|**On-disk size in MB**|  
|8828|  
  
 The on-disk size is close to 9GB, which comes close to the in-memory size of the data.  
  
 Looking more closely at the sizes of the checkpoint files across the various states:  