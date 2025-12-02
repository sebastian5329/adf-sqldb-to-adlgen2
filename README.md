*Sample SQL Tables to ADLS Gen2*

This is a small learning project built to practice Azure Data Factory (ADF) by copying sample tables from an Azure SQL Database into Azure Data Lake Storage Gen2.
The pipeline uses a configuration-driven approach to decide which tables should be copied.

*Project Overview*

	•	Source: Azure SQL Database
	•	Destination: Azure Data Lake Storage Gen2 (ADLS Gen2)
	•	ADF Activities Used:
	•	Lookup
	•	ForEach
	•	Copy Data
	•	A configuration table (tblconfig) was used to store table names, schema names, sink file path, sink file name and an active flag
  Only the tables marked as Active were copied to the Data Lake.

*How the Pipeline Works*
 
    1.Lookup Activity
	    •	Reads all active records from the tbl_configuration table.
	    •	Each record contains:
	    •	Table name
	    •	Schema name
	    •	Active flag
    
    2.ForEach Activity
	    •	Loops through each active table returned by the Lookup.
    
	3.Copy Data Activity (inside ForEach)
	    •	Dynamically picks the table name and schema name.
	    •	Copies data from SQL Database to ADLS Gen2.
