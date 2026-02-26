# ADF
Azure Data Factory Project


## Pipelines
### API pipeline
<img width="2316" height="1266" alt="image" src="https://github.com/user-attachments/assets/c9b45b33-159a-455a-92b7-f70c4075f0f2" />
Pipeline takes the output count from web activity and dynamically takes offset range in Copy data activity.


### Ingestion
<img width="2308" height="1288" alt="image" src="https://github.com/user-attachments/assets/694c8746-062b-4af2-8dcb-025f0c82ef71" />
Pipeline takes schema, table and manual load parameters before the pipeline run. Total count activity run the dynamic query based on the parameters and returns the count of records updated after manual load if exists or last load date. If we have new records Data load activity is completed with dynamic inputs and updates last load date to maximum date from the table.


### Schedule 
<img width="2224" height="1286" alt="image" src="https://github.com/user-attachments/assets/3cc1be0a-f9ec-4340-921d-fb67745ac760" />
Pipeline takes another pipeline as input and triggers the pipeline run based on the trigger. Trigger can be used to schedule pipeline at particular time and interval.


### Router
<img width="2304" height="950" alt="image" src="https://github.com/user-attachments/assets/328b5609-f1c5-46bb-a03b-3a70e5288cd5" />
Pipeline run is triggered when file is uploaded in the container. Once the files are uploaded get metadata activity gets name of all the files in the container. Switch case activity loads data into destination container for all items uploaded in the source container and the delete activity deletes all files from the source container to end the pipeline run.


### Schema
<img width="2246" height="1252" alt="image" src="https://github.com/user-attachments/assets/66e91a99-232a-43a5-8c7d-54ead8a9efa8" />
Pipeline takes table schema mapping as input parameters. Get metadata activity gets the name of all files from the source container. For each activity runs copy data activity for all files from source container and mapping is done dynamically based on the file name.  


### Delta Flow
<img width="2380" height="1172" alt="image" src="https://github.com/user-attachments/assets/21a357df-0264-4bb3-9f06-3213f2c54a3b" />
Delta flow runs the data flow that takes the data from source performs the transformations and then stores the data into destination container as delta table.
Tranformation performed in the data flow are just to convert source data into delta table.



