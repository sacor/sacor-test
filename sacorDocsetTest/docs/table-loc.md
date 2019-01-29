#### <a name="initial-state"></a>Estado inicial  
 Cuando se crean inicialmente el grupo de archivos de ejemplo y las tablas optimizadas para memoria de ejemplo, se crean previamente varios archivos de punto de comprobación y el sistema empieza a rellenar los archivos; el número de archivos de punto de comprobación creados previamente depende del número de procesadores lógicos del sistema. Como el ejemplo es inicialmente muy pequeño, los archivos creados previamente estarán vacíos en su mayoría después de la creación inicial.  
  
 A continuación se muestra el tamaño inicial en disco del ejemplo en un equipo con 16 procesadores lógicos:  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|**Tamaño en disco en MB**|  
|2312|  
  
 Como puede ver, hay una gran discrepancia entre el tamaño en disco de los archivos de punto de comprobación, que es 2,3 GB, y el tamaño de datos real, que es más cercano a 30 MB.  
  
 Para examinar más de cerca de dónde procede la utilización de espacio en disco, puede usar la consulta siguiente. El tamaño del disco devuelto por esta consulta es aproximado en el caso de los archivos que tienen el estado 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE) o 7 (TOMBSTONE).  