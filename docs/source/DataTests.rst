***********
Data Tests
***********

Schema-based Data Validation
============================

.. _what_to_test:

What to test?
-------------
The schema based validation tests are designed to encapsulate the intuition of the data in a schema automatically. 
Once the schema is setup, it is used as a baseline data model to test training  and serving data to prevent potential data drift / concept drift. 

.. code-block:: console

   (.venv) $ pip install lumache

.._how_to_test:
How to test?
------------

The schema should at least capture the following information:
The schema should at least capture the following information:

- descriptive statistics
- correlation coefficient to check feature dependency
- data characteristics (types, range) 

To perform schema-based validation, the basic logic for this tests would be only if the incoming training / serving data pass the test, we then will continue to pass the data to model training or making inference. 
The process of generating the schema creation should be agnostic, which is portable to another platforms, either in local or in cloud