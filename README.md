# dsc-202-fraud-analytics
Fraud analytics for detecting potentially fraudulent merchants based on transaction patterns. 

# Team Members
1. Tarun Kumar Gupta (A69033596)
2. Aryan Bansal
3. Jude Mariadas
4. David Lurie


## Instructions to run  
0. Pull the repo. 

1. Create and setup environment  
```
conda create --name dsc-202 python=3.10.16
conda activate dsc-202
pip install -r requirements.txt
```  

2. Launch neo4j (Command Prompt)
```
docker run --name neo4j-with-plugins^ -p 7474:7474 -p 7687:7687^ -e NEO4J_AUTH=neo4j/password^ -e NEO4JLABS_PLUGINS="[\"apoc\", \"graph-data-science\"]"^ -e NEO4J_dbms_security_procedures_unrestricted="apoc.*,gds.*"^ -e NEO4J_dbms_security_procedures_allowlist="apoc.*,gds.*"^ -v "%cd%/neo4j-import:/import"^ -v neo4j_data:/data^ neo4j:latest
```

3. Run python notebook  
Once neo4j has been set up and is running, run the `neo4j-data-ingestion.ipynb` to ingest the `neo4j-import/fraudTestSample.csv` file into the database. To limit the number of rows that are ingested, add `LIMIT 10` after the `WITH ROW` line in the query. 


## Resetting neo4j  
Just stopping and removing the neo4j container will not be enough. The data volume needs to be removed as well. Run the following commands to completely delete the container and saved data. 
```
docker stop neo4j-with-plugins
docker rm neo4j-with-plugins
docker volume rm neo4j_data
```
