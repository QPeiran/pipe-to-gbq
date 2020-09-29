# Data pipeline intro and user guide
## Before start
Put `API key.json` in the `./creds` folder.

Install google python clients -- `bigquery`, `cloud storage`, `OAuth`

Run *"set-env"*: 
1. Test connection to **GCP**
2. Check the **PowerBI** source table
3. Always make sure to limit the query size by `bq_client.QueryJobConfig`

## Step 1 - Upload the prepared data from local machine to *Cloud Storage*: 

Run *"upload_from_local"*:

The `local_path` and the `storage_path` need to change according to our **production week**

## Step 2 - Pipe data from **Cloud Storage** to **Bigquery**

Run *"pipe"*:

1. Pull the current production week's data from **Cloud Storage**
2. Creat a new table in the **Bigquery** as `weekly backup`
3. Auto detect data schema from `Bolb` then push the current week's data to the newly created table.

## Step 3 - Extract the data from the **Bigquery** historical tables

Run "PowerBI_source_data":

1. Union historical production weeks' data together
2. Overwirte *"PowerBI source tabel"* (`WRITE_RUNCATE`)



# TODOs

* Integrate data processing/transforming code to the pipe line then deprecate the  *"upload_from_local"*


* Integrate **Cloud Funtion** to make the whole process fullly automatic ( **Cloud Funtion** in used pulling data from scanning system will directly push the data to the **Cloud Storage**, then fire the `on submit` trigger)


# Beware conda no longer in use, pipenv "pipe-to-gbq" now need to be reset as the jupyter kernel
