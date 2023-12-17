- 👋 Hi, I’m @debayo64
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
debayo64/debayo64 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import pandas as pd
from sqlalchemy import create_engine

# The data file path and file name need to be configured.
PATH = "C:\\Python.py\\Dataset"
CSV_DATA = "retailerDB.csv"
df = pd.read_csv(PATH + "\\" + CSV_DATA)  # Escape the backslashes

# Placed query in this function to enable code re-usability.
def showQueryResult(sql):
    # This code creates an in-memory SQLite database and a table called 'Inventory'.
    engine = create_engine('sqlite:///:memory:', echo=False)
    connection = engine.connect()
    df.to_sql(name='Inventory', con=connection, if_exists='replace', index=False)

    # This code performs the query.
    queryResult = pd.read_sql(sql, connection)

    # Close the connection after use.
    connection.close()

    return queryResult


# Read all rows from the table.
SQL = "SELECT * FROM Inventory"
results = showQueryResult(SQL)
print(results)

