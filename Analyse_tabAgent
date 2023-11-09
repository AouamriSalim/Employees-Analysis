import sqlalchemy
import pandas as pd

# Define your SQL Server connection string
server = 'yourservername'
database = 'yourdatabse'
username = 'yourusername'
password = 'yourpassword'

# Create an SQLAlchemy engine
engine = sqlalchemy.create_engine(f"mssql+pyodbc://{username}:{password}@{server}/{database}?driver=ODBC Driver 17 for SQL Server")
# Create a connection string
#connection_string = f'DRIVER={{ODBC Driver 17 for SQL Server}};SERVER={server};DATABASE={database};UID={username};PWD={password}'

# Connect to the database
#conn = pyodbc.connect(connection_string)
# Define your SQL query to select data from the table
sql_query = 'SELECT * FROM Tab_Agent'

# Use pandas to read the data into a DataFrame
df = pd.read_sql_query(sql_query, engine)

# Use pandas to read the data into a DataFrame
#df = pd.read_sql_query(sql_query, conn)

# Close the database connection
#conn.close()

# Now you have your data in the 'df' DataFrame, and you can perform various analyses using Pandas
print(df.head())
print(df.tail())

print(df.describe())
print(df.info())

print(df[df['Nbr_Enfant'] > 2])

selected_columns = df[['Matricule', 'Prenom', 'Nom', 'Date_Naissance']]
print(selected_columns)

group_by_gender = df.groupby('Genre')['Nbr_Enfant'].mean()
print(group_by_gender)

sort_by_values =df.sort_values(by='Code_Dossier', ascending=False)
print(sort_by_values)

group_by_column = df.groupby('Code_Dossier').count()
print(group_by_column)

#corr_values = df.corr()
#print(corr_values)

import matplotlib.pyplot as plt

group_by_column.plot(kind='hist')
plt.xlabel('Columns')
plt.ylabel('Frequency')
plt.title('Distribution of Columns grouped by Code Dossier')
plt.show()




