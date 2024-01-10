# SQLite-Data-Base-module

This is a simple Python class for interacting with SQLite databases. It provides functionality to create tables, insert data, query data, and more. 

## Installation

To use this module, you need to have Python installed. Additionally, ensure that the `sqlite3` and `pandas` modules are available. If not, you can install them using:

pip install sqlite3 pandas


## Usage
```
from data_base import Database

# Creating a Database object
db = Database("invest_tracker_data_base")

# Creating a table
db.create_table("Transactions", "id INTEGER PRIMARY KEY AUTOINCREMENT",
                                "account_id INTEGER",
                                "date_of_purchase",
                                "operation_ticker",
                                "type_of_transaction_value",
                                "currency",
                                "number_of_units INTEGER",
                                "price_of_one_unit REAL",
                                "commission REAL",
                                "yahoo_ticker",
                                "tax REAL",
                                "total_cost REAL",
                                "total_number_of_units_after_transaction INTEGER",
                                "account_balance_after_operation REAL",
                                "type_of_investment",
                                "FOREIGN KEY(account_id) REFERENCES Accounts(id)")

# Inserting data
db.insert_row("Transactions", (None, 1, "2023-09-19", "BUY", "EDO0933", "PLN", 42, 100.0, 0, "EDO0933", "OBLIGACJE SKARBOWE"))

# Querying data
Transaction_df = db.get_table_df_with_conditions("Transactions", "type_of_transaction_value", "currency", "yahoo_ticker", "total_number_of_units_after_transaction", "total_cost", "type_of_investment", account_id = f"{self.id}")
print(data)

# Update data
db.update_data(table_name="Transactions", attribute_name= "total_number_of_units_after_transaction", attribute_value= updated_value, item_id= self.id)    

# List of available methods:
    - create_table(self, table_name: str, *columns): Creates a new table in the database with the specified name and columns.

    - check_table_exists(self, table_name): Checks if a table with the given name already exists in the database.

    - drop_table(self, table_name: str): Drops (deletes) a table from the database.

    - get_all_table_names(self): Retrieves a list of all table names in the database.

    - get_column_names(self, table_name: str): Retrieves a list of column names for a given table.

    - is_table_empty(self, table_name: str): Checks if a table is empty.

    - get_table(self, table_name: str): Retrieves all rows from a specified table.

    - get_table_df(self, table_name: str, *column_names, sort_col: str = None, sort_order: str = None, where_condition: str = None): 
        Retrieves data from a specified SQLite table and returns it as a pandas DataFrame.

    - get_table_df_with_conditions(self, table_name: str, *column_names, condition_operator: str = "AND", limit: int = None, **kwargs): 
        Retrieves data from a specified table with specified conditions and returns it as a pandas DataFrame.

    - insert_row(self, table_name: str, *values): Inserts a new row into the specified table in the database.

    - get_first_row_value(self, table_name: str, *column_names): Retrieves values from the first row of specified columns.

    - get_last_row_value(self, table_name: str, *column_names): Retrieves values from the last row of specified columns.

    - get_last_id(self, table_name: str): Retrieves the last ID from a specified table.

    - update_data(self, table_name: str, attribute_name: str, attribute_value: str, item_id: int): Updates data in a specified table.

    - update_table(self, table_name: str, update_dict, where_dict): Updates rows in a specified table based on given key-value pairs.
'''

## Documentation
Detailed documentation for each method and its parameters can be found in the code as docstrings. 

## Contributing
If you find any issues or have suggestions for improvements, feel free to open an issue or submit a pull request.

## License
This project is licensed under the MIT License
