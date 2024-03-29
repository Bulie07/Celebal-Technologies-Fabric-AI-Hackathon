# Celebal-Technologies-Fabric-AI-Hackathon

Here's the link to the word document comprising of the problem statement as well as the solution:

https://celebaltech-my.sharepoint.com/:w:/p/aishwarya_walkar/ESqY70cTsGlGoqNOu4L4ZScB_fDD05zQutPo70Hg9SDo-Q?e=LyaN8R

Here's the link to the dataset:

https://celebaltech-my.sharepoint.com/:x:/p/shivam_gaur1/ETwNAhu3eOpCmLsx1FCX0bgBX6EI4q2KLVxK5ZCo0S04ig?e=ZGvs31



Fabric's Data factory Pipeline:

1. Created a lakehouse named "hackathon_lakehouse_celebal."
2. Created a corresponding warehouse, "hackathon_warehouse_celebal."
3. Inside the warehouse, two tables, "allfiles" and "copiedfiles," were created alongside two procedures for managing file names from ADLS to these tables; the first procedure populates "allfiles" with file names, while the second updates "copiedfiles" with names of files processed into the "salesdata" table.
4. Integrated the warehouse with the lakehouse.
5. Developed the pipeline architecture.


![image](https://github.com/Bulie07/Celebal-Technologies-Fabric-AI-Hackathon/assets/91520647/1480742f-7a91-4793-af39-800307c67001)


Pipeline explained:

1. Utilized the "Get Metadata" activity to retrieve file names from Azure Data Lake Storage (ADLS). A "ForEach" loop, initiated by the "Get Metadata" output, executed a stored procedure within, adding these file names to the "Allfiles" table.

2. To manage already processed files, our data fabric warehouse includes the "Copiedfiles" table. A "Lookup" activity was deployed to discern unprocessed files by comparing "Allfiles" and "Copiedfiles" tables.

3. The resulting list of new files from the lookup was processed through another "ForEach" loop, utilizing the "Copy Data" activity to integrate their data into the "salesdata" table. This step was followed by a procedure to update "Copiedfiles" with the names of these newly added files, ensuring an efficient tracking and processing workflow.

  

Azure OpenAI's Steps Followed: 

1.Following the creation of the "salesdata" table, we loaded it into our fabric notebook using the command "spark.read.table". 

2.we loaded the "salesdata" table and Transformed it into a Pandas DataFrame, changed the column types using the fabrics functionality "data wrangler"

3.In the next step, we used Azure OpenAI's GPT-35-Turbo model, wherein we created a prompt which is about using detailed customer data to write a personalized and engaging marketing email that adheres to a set of creative and strategic guidelines, aiming to appeal to the customer's preferences and shopping habits.

![image](https://github.com/Bulie07/Celebal-Technologies-Fabric-AI-Hackathon/assets/91520647/162b453c-e8f7-442d-9fa9-04e9b18fb81f)

Workspace Preview:

![image](https://github.com/Bulie07/Celebal-Technologies-Fabric-AI-Hackathon/assets/91520647/b32703fc-4243-406c-a410-9113a42743e1)


Data Activator:

We also plan to integrate Microsoft Fabric’s Data Activator’s capabilities into our solution in the future. By setting alerts for people who are not following trends, we can send them emails generated by our AI model with the help of data activator. 


Power bi report:

We have also generated a power bi report using the auto create report feature of microsoft fabric on our warehouse's semantics model.

![image](https://github.com/Bulie07/Celebal-Technologies-Fabric-AI-Hackathon/assets/91520647/121b675d-105c-4732-a94b-391aa9867e44)

