  
#### <a name="initial-state"></a><span data-ttu-id="e2a87-535">Estado inicial</span><span class="sxs-lookup"><span data-stu-id="e2a87-535">Initial state</span></span>  
 <span data-ttu-id="e2a87-536">Cuando se crean inicialmente el grupo de archivos de ejemplo y las tablas optimizadas para memoria de ejemplo, se crean previamente varios archivos de punto de comprobación y el sistema empieza a rellenar los archivos; el número de archivos de punto de comprobación creados previamente depende del número de procesadores lógicos del sistema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-536">When the sample filegroup and sample memory-optimized tables are created initially, a number of checkpoint files are pre-created and the system starts filling the files - the number of checkpoint files pre-created depends on the number of logical processors in the system.</span></span> <span data-ttu-id="e2a87-537">Como el ejemplo es inicialmente muy pequeño, los archivos creados previamente estarán vacíos en su mayoría después de la creación inicial.</span><span class="sxs-lookup"><span data-stu-id="e2a87-537">As the sample is initially very small, the pre-created files will be mostly empty after initial create.</span></span>  
  
 <span data-ttu-id="e2a87-538">A continuación se muestra el tamaño inicial en disco del ejemplo en un equipo con 16 procesadores lógicos:</span><span class="sxs-lookup"><span data-stu-id="e2a87-538">The following shows the initial on-disk size for the sample on a machine with 16 logical processors:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="e2a87-539">**Tamaño en disco en MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-539">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="e2a87-540">2312</span><span class="sxs-lookup"><span data-stu-id="e2a87-540">2312</span></span>|  
  
 <span data-ttu-id="e2a87-541">Como puede ver, hay una gran discrepancia entre el tamaño en disco de los archivos de punto de comprobación, que es 2,3 GB, y el tamaño de datos real, que es más cercano a 30 MB.</span><span class="sxs-lookup"><span data-stu-id="e2a87-541">As you can see, there is a big discrepancy between the on-disk size of the checkpoint files, which is 2.3GB, and the actual data size, which is closer to 30MB.</span></span>  
  
 <span data-ttu-id="e2a87-542">Para examinar más de cerca de dónde procede la utilización de espacio en disco, puede usar la consulta siguiente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-542">Looking closer at where the disk-space utilization comes from, you can use the following query.</span></span> <span data-ttu-id="e2a87-543">El tamaño del disco devuelto por esta consulta es aproximado en el caso de los archivos que tienen el estado 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE) o 7 (TOMBSTONE).</span><span class="sxs-lookup"><span data-stu-id="e2a87-543">The size on disk returned by this query is approximate for files with state in 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE), or 7 (TOMBSTONE).</span></span>  
  