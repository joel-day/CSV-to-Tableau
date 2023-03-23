# CSV to Tableau

## Pipeline Processes:
1. The raw CSV files are loaded into a Python Jupyter Notebook and converted to Pandas dataframe objects.
2. The following transformation are applied to the invoices dataframe:
 * White spaces in column names with multiple words are replaced with underscores (for consistency and to prevent syntax issues).
 * The Date and Date_of_Meal fields are converted to Datetime datatypes, where the additional timezone information ("+00:00:00") is dropped to standardize all times to UTC timezone.
 * The hour is extracted from Date_of_Meal and mapped to a part of the day (i.e. Early Morning, Late Morning, Early Afternoon, etc.), and a new field ("Part_of_Day") is created.
3. A new dataframe representing each unique customer is created using the Participants column from of the invoices dataframe. The row index plus one acts as a unique customer identification number.
4. Another dataframe (customer_order) is created to link every order_id to the participating customer_id(s).
5. The pipeline attempts to connect to the user's local MySQL server, prompting the user to enter their  MySQL username and password.

## Pipeline Deployment:
1. Download the csv's. 
2. Execute downloaded file in your preferred python environment (Anaconda, VSCode, etc.).
  *_Note:_ The pipeline assumes that the server is "localhost" and that the port number is 3306. If the server name or port number differs, the script will need to be modified.
3. When prompted, enter your MySQL username (usually, "root") and your corresponding MySQL password.
4. Let the pipeline run to completion.


## Pipeline Monitoring:
* Print statements, such as "print('Invoice Table Created!)," are included at critical points to confirm that the pipeline is functioning as expected.
* If a print statement, confirming the cells successful execution, is not printed, the pipeline will stop its execution and display an error message.


