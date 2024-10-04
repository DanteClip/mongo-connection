# MongoDB to Databricks Pipeline

This repository contains a notebook that establishes a connection to a **MongoDB 3.0** database using **Apache Spark**. The goal of this pipeline is to extract collections from MongoDB, store them in **Parquet** format, and upload them to a specific volume in **Databricks**.

## Pipeline

### Pipeline Flow:
1. Establish a connection to the MongoDB database.
2. Retrieve the following collections from MongoDB:
   - `State`
   - `Country`
   - `Municipality`
   - `ZipCode`
   - `User`
   - `PocketBalance`
   - `Location`
   - `Transaction`
3. Each collection is stored in **Parquet** format.
4. The generated Parquet files are uploaded to the **Databricks** (banking dev) environment using the **Databricks API**.
5. The files are stored in the following Databricks volume:
   ```
   sandbox_banking/mutt_data_banking/mongo
   ```

## Configuration

### `.env` File
You need to create a `.env` file at the root of the project containing the following environment variables for MongoDB and Databricks connection:

```bash
MONGO_DB='MONGO DB NAME'   # Name of the MongoDB database
MONGO_URI='MONGO DB URI'   # MongoDB connection URI
DBKS_TOKEN='DBKS TOKEN'    # Authentication token for the Databricks API
```

Be sure to replace the values in quotes with the correct credentials for your environment.

## Requirements

The following libraries are required to run the notebook:

- **`pyspark`**: for working with Apache Spark.
- **`python-dotenv`**: for loading environment variables from a `.env` file.
- **`requests`**: for making HTTP requests (useful for interacting with the Databricks API).

### Installation

To install the necessary dependencies, run the following command:

```bash
pip install -r requirements.txt
```

This will install all the required libraries listed in the `requirements.txt` file.

## Execution

1. Set up the `.env` file with your credentials.
2. Run the notebook, which will:
   - Connect to MongoDB.
   - Extract the specified collections.
   - Save them as Parquet files.
   - Upload the files to the specified Databricks volume.
