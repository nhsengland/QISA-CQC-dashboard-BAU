# CQC GP and Care Homes monthly reporting
Repository to store all codes used to process CQC ratings data required for monthly CQC GP and Care Homes ratings reporting. This is part of the BAU process for refreshing two of the products that the Quality Improvement Strategic Analysis team own: CQC GP dashboard: https://future.nhs.uk/Quality/view?objectID=33056464 and CQC Care Homes dashboard: https://future.nhs.uk/Quality/view?objectID=33114832


## About this project
The Care Quality Commission (CQC) is the regulator that monitors and inspects all health and social care services in England to ensure standards are being met. 
After an inspection, they rate the quality of care for their five key questions: are they safe, effective, caring, responsive and well-led? There is a rating for each question and an overall rating. Ratings will be based on a four-point scale; Outstanding, Good, Requires Improvement or Inadequate. More information can be found on the CQC website: https://www.cqc.org.uk/about-us/how-we-do-our-job/inspection-reports

This repository contains codes to produce analysis for the CQC GP and Care Homes dashboards. 
The code retrieves the latest CQC ratings data from the UKHF_CQC tables in the UDAL Lake/main warehouse to produce monthly CQC dashboards. The code contains some conditions to obtain the most recent information from the UKHF_CQC tables on the day the code is executed. 

## Requirements
-  Access to Azure Databricks in UDAL
-  Access to Azure Storage Explorer/ NHS National Data Platform/ Quality Improvement Data Lake (Q&I Lake)

## Summary of the code	
-	Databricks Notebook - Max_API_Call_Date: 
This notebook contains code to obtain the most recent API call date from the UKHF CQC location_SCD table and save it in the Q&I Lake. Max_API_Call_Date indicates when the data was last refreshed. 

-	Databricks Notebook – CQC dashboard – GP Ratings data:
The notebook contains code to retrieve the latest CQC GP ratings data, which is required to produce the monthly CQC GP dashboard. 
The code is mainly written in SQL, with some parts in Python. The code consists of three parts. The first part retrieves the latest GP ratings and saves the output in a temporary table. 
However, the new SAF ratings are not included in this data, so the second part of the codes obtains new SAF ratings separately from the JSON plain text contained in the UKHF tables and saves them in a temporary table. 
Finally, these two outputs are combined to produce the final output, which is then saved in the Q&I Lake for use in the GP Tableau workbook.

-	Databricks Notebook - CQC dashboard – CH Ratings data:
The notebook contains code to retrieve the latest Care Homes CQC ratings data, which is required to produce the monthly CQC Care Homes dashboard. 
The code is mainly written in SQL, with some parts in Python. The code consists of three parts. The first part retrieves the latest CQC Care Homes ratings and saves the output in a temporary table. 
However, the new SAF ratings are not included in this data, so the second part of the codes obtains new SAF ratings separately from the JSON plain text contained in the UKHF tables and saves them in a temporary table. 
Finally, these two outputs are combined to produce the final output, which is then saved in the Q&I Lake for use in the Care Homes Tableau workbook.

## Data sources
CQC API - Home - [CQC Developer Portal](https://api.service.cqc.org.uk)

For more information about the data tables used, please see the data flow charts.

## License
Unless stated otherwise, the codebase is released under the MIT LICENSE This covers both the codebase and any sample code in the documentation.
See LICENSE for more information.
The documentation is © Crown copyright and available under the terms of the Open Government 3.0 licence. https://github.com/nhsengland/Maternity-reading-the-signals/blob/Gary-QA/LICENSE

## Author
Geoffrey Sharpe
Kirsty Walker
Shalika De Silva - shalikadesilva@nhs.net

## Contact
To get in touch with us and find out more about the Quality Improvement Strategic Analysis Team please email us at england.da-qis-analysis@nhs.net 

