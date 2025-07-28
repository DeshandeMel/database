---
output: 
  pdf_document: default
  html_document: default
---

# Ingest Vector Embedded Data into Oracle Autonomous Database with MongoDB Shell
<Modify/Find Lab 3: Using the Oracle Database API for MongoDB>

## Introduction

In this lab you will connect to Autonomous Database with Mongo Shell, ingest data into a JSON collection, and create vector embeddings with an ONNX model.

You will learn the function and importance of vector AI search.

Estimated Time: 10 Minutes

### Objectives

In this lab you will:

* Connection to Autonomous Database with MongoDB Shell

* Create Vector Embeddings with ONNX model

* Ingest Data into JSON Collections through MongoDB API

### Prerequisites

* Have provisioned an Autonomous JSON Database instance and saved the URLs for Database API for MongoDB

* Have installed the MongoDB Shell

You will need the following information, saved from previous labs:

* The URL for the MongoDB API

## Task 1: Create Vector Embeddings with ONNX model

We will start by downloading this JSON file of popular library books.

<Insert Downloadable Link of Wiki Books>

No matter the wealth of books available in the library. A library is only as good as its ability to provide readers with a desirable book.

As the newly appointed librarian of this collection of books, you will need to create a system to best service your patrons.

To do so, first click the **Database actions** button in your Autonomous Database Details page, and select **SQL**.

Now in the Worksheet create a table:

  <copy>
  CREATE TABLE books (
    title         VARCHAR2(200),
    author        VARCHAR2(200),
    published     NUMBER,
    fiction       CHAR(1),
    plot          CLOB,
    availability  CHAR(1)
  );
  </copy>

Right Click the BOOKS Table and select Data Loading then Upload Data

  !["created books table](./images/books-table.png " ")

Select or Drop the JSON file of popular library books and select Upload

  !["upload books table](./images/books-upload.png " ")

Your system must quick and efficiently organize and suggest available books—perhaps managing books across languages and media such as audiobooks in French and comics in Mandarin.

<Insert Image of Books on 2 Light\Transparent Shelves with Vector pointing towards them and a Query Vector Between 2 with Cosine or Euclidean Similarity being implemented**>

The beauty of Vector AI Search is the ability and efficacy of handling unstructured data. By mathematically representating our books as vectors, it becomes simple to search across our library at the behest of our patrons.

We create the vector embeddings of our books using a large language model (LLM) model enhanced by retrieval augmented generation (RAG). While LLMs are powerful being trained upon an expansive volume of data, they benefit from RAG models providing context and a structure to convert book plots into vectors retaining the semantic meaning of the stories.

To download the pre-trained ONNX model, navigate to [HuggingFace ONNX model](https://huggingface.co/sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2/tree/main/onnx)

<Download a sentencetransformer ONNX model>

Open your Autonomous Database homepage and select the menu icon in the top left. Select Storage and then click Bucket  

  !["navigate to buckets](./images/books-upload.png " ")

<Continue ...>

## Task 2: Ingest Vector Embeddings into JSON collection

Edit URL you copied to clipboard in a text editor.

1. Change the [user:password@] to admin:YourPassword@ at the start of the URL. Substitute the password you chose earlier for the YourPassword.

2. Change the [user] string in the middle to admin

For example, let's say your password is "Password123", and your original connection string is mongodb://[user:password@]MACHINE-JSONDB.oraclecloudapps.com:27017/[user]?authMechanism=PLAIN&authSource=$external&ssl=true&retryWrites=false&loadBalanced=true

Your resulting URL would look similar to

<copy>
mongodb://admin:Password123@MACHINE-JSONDB.oraclecloudapps.com:27017/admin?authMechanism=PLAIN&authSource=$external&ssl=true&retryWrites=false&loadBalanced=true
</copy>

IMPORTANT NOTE: if your password contains any special characters in the set / : ? # [ ] @, you will need to escape them as follows:

**IMPORTANT NOTE:** If your password contains any special characters in the set / : ? # [ ] @, you will need to escape them as follows:

	| Character | Escape Sequence |
	| :---:     | :---: |
	| /	 | %25 |
	| :	 | %3A |
	| #	 | %23 |
	| [	 | %5B |
	| ]  | %5D |
	| @	 | %40 |

So if your password was **P@ssword#123** you would encode it as **P%40ssword%23123**.

Download the sample dataset we will use [here](github URL)

Open Terminal or Command Prompt and using mongoimport, subsituting mongoAPI-URI for your edited connection string:

<copy>
mongoimport <mongoAPI-URI> --collection library wiki_books.json --tlsInsecure
</copy>

## Task 3: Connect MongoDB shell to Autonomous Database

Navigate to Terminal or Command Prompt. Type "mongosh" space the edited URL from the previous task in single-quotes on a Mac or Double-quotes on Windows.

  !["mongosh login](./images/mongosh-login.png " ")

If succesful you will see an "admin>" prompt. Otherwise, carefully check your URL:

* Is it enclosed in single quotes?
* Is your password correct, with any special characters quoted as above?
* Did you leave any [ square brackets ] in the URL where they should have been removed?
* Do you have the : sign between the user and password, and the @ sign after the password? 
* Is the whole command on a single line with no line breaks?



## Task 4: Check Whether Data was Succesfully Ingested

Check if the sample data was successfully ingested:
    ```
    <copy>
    use library
    </copy>
    ```
    ```
    <copy>
    db.books.find({}, {title: 1, author: 1, illustrator: 1, published: 1, fiction: 1}).pretty().limit(3)
    </copy>
    ```

You should see 3 books returned with their title, author, illustrator, publication, and whether fiction or nonfiction. If not, check if you succesfully downloaded the sample data and imported the documents with a valid connection string.

  !["ingested data successfully](./images/ingested-data.png " ")

## Learn More

* [Oracle Database API for MongoDB](https://blogs.oracle.com/database/post/mongodb-api)
* [Simple example to test your MongoDB connection using a node.js application](https://docs.oracle.com/en/cloud/paas/autonomous-database/serverless/adbsb/mongo-using-oracle-database-api-mongodb.html#GUID-935C72EB-5ECF-4663-9BCA-860708EFAE2A__SUBSTEPS_BQL_R2Y_BRB)

## Acknowledgements

* **Author** - Deshan de Mel
* **Contributors** -  Roger Ford, Kamryn Vinson, Andres Quintana, Madhupriya Ravishankar, Hermann Baer, Beda Hammerschmidt
- **Last Updated By/Date** - Deshan de Mel, July 2025
