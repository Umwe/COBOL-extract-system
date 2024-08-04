# COBOL-extract-system
this is  dedicated micro service built in Cobol to perform business transactions such as loading daily financial transactions


This repository contains examples of CRUD (Create, Read, Update, Delete) operations using COBOL with a DB2 database. COBOL is a legacy programming language widely used in business applications, particularly in the banking and finance sectors. These examples demonstrate how to perform basic database operations in COBOL.

Prerequisites
Before running these examples, ensure you have the following installed:

COBOL compiler (e.g., IBM COBOL, GnuCOBOL)
DB2 database and client tools
Access to a DB2 database with appropriate credentials
Directory Structure
CreateRecord.cob: Example COBOL program to create (insert) a new record in the database.
ReadRecord.cob: Example COBOL program to read (select) a record from the database.
UpdateRecord.cob: Example COBOL program to update an existing record in the database.
DeleteRecord.cob: Example COBOL program to delete a record from the database.
data_definitions.cpy: Example COBOL copybook containing reusable data definitions.
Usage
1. Setup the Environment
Ensure your environment is set up with access to the COBOL compiler and DB2 database. Set your DB2 credentials in the programs where indicated.

2. Establish Database Connection
Each program includes a section to connect to the DB2 database using the EXEC SQL CONNECT statement. Ensure your database credentials are correctly specified.

cobol
Copy code
EXEC SQL
    CONNECT TO 'yourdatabase'
    USER :WS-USERID
    USING :WS-PASSWORD
END-EXEC.
3. Create Operation
The CreateRecord.cob program demonstrates how to insert a new record into the EMPLOYEE table.

cobol
Copy code
EXEC SQL
    INSERT INTO EMPLOYEE (EMP_ID, EMP_NAME)
    VALUES (:EMP-ID, :EMP-NAME)
END-EXEC.
Run the program:

bash
Copy code
cobol CreateRecord.cob -o CreateRecord
./CreateRecord
4. Read Operation
The ReadRecord.cob program demonstrates how to select and retrieve a record from the EMPLOYEE table.

cobol
Copy code
EXEC SQL
    SELECT EMP_NAME INTO :EMP-NAME
    FROM EMPLOYEE
    WHERE EMP_ID = :EMP-ID
END-EXEC.
Run the program:

bash
Copy code
cobol ReadRecord.cob -o ReadRecord
./ReadRecord
5. Update Operation
The UpdateRecord.cob program demonstrates how to update an existing record in the EMPLOYEE table.

cobol
Copy code
EXEC SQL
    UPDATE EMPLOYEE
    SET EMP_NAME = :EMP-NAME
    WHERE EMP_ID = :EMP-ID
END-EXEC.
Run the program:

bash
Copy code
cobol UpdateRecord.cob -o UpdateRecord
./UpdateRecord
6. Delete Operation
The DeleteRecord.cob program demonstrates how to delete a record from the EMPLOYEE table.

cobol
Copy code
EXEC SQL
    DELETE FROM EMPLOYEE
    WHERE EMP_ID = :EMP-ID
END-EXEC.
Run the program:

bash
Copy code
cobol DeleteRecord.cob -o DeleteRecord
./DeleteRecord
7. Copybook File
The data_definitions.cpy file contains reusable data definitions that can be included in multiple COBOL programs.

cobol
Copy code
COPY 'data_definitions.cpy'.
Conclusion
These examples demonstrate basic CRUD operations using COBOL with a DB2 database. COBOL's robust handling of business data makes it a reliable choice for enterprise applications. For more complex scenarios, consider exploring COBOL's advanced features and DB2's powerful querying capabilities.

Resources
IBM COBOL Documentation
DB2 Documentation
GnuCOBOL
