************************
Model (Validation) Tests
************************

Version-controlled Model & Specs
================================

.. _what_to_test:

What to test?
-------------

This tests is an inspection of the modelOps system design to evaluate if the current system met capability to version-controlled model and specs. Ideally, the system is capable of tracking model experiments and allows for reproducibility in the future.


.._how_to_test:

How to test?
------------

This inspection provides answer to the following questions:

- Does the system allows version control the model code? This would include model training code and the model specs.
- Does the system has the capability to check and store the code?
- Does the code undergo code review?

Evaluation Tests
================

.. _what_to_test:

What to test?
-------------

The evaluation test is conducted that we regularly check our new model to a very simple baseline. The purpose of doing this is not only compare to see if the new model, usually with more sophisticated techniques, will perform better than the baseline, but also evaluate the trade-off to achieve this level of performance. Also, by having this test we can ensure the functionality of the larger model pipeline and debug if necessary.

.._how_to_test:

How to test?
------------

To find such baseline, we recommend to have a simple model with few features. This test that will compare the metrics of baseline model and the new model to check if the new model will perform better than the baseline. In this way, baseline will act as a safety net for other models so that the performance can not go worse than the baseline.


Data Slicing
============

What to test?
-------------

This test is to check the model quality on specific data slices. It is designed to test if there are any bias on each of these slice in terms of model performance. Usually we would combine data slicing tests with the evaluation tests so that we have a comparison on the metrics for each data slices to have a better understanding of the model quality.

How to test?
------------

To construct a data slicing unit tests, we first need to identify the data slices. Once we have the slices defined, we will evaluate the model performance on these data slices versus predefined data slices metrics. (add some examples about data slices and how does it compare)

- If we are combining the evaluation tests, we would then use the slice on both baseline and the current model and evaluate the metrics.
- If we want to use standalone tests, we need to first using a predefined metrics to compare the slices performance. It can be an advanced model like xgboost that we want to check against and using the model performance to set standards for the data slicing tests.


Single Batch Test
=================

What to test?
-------------

Single batch test is a technique to debug deep learning models to check correctness of the model code. The idea of this test is to train your DL models with a single epoch or single batch and see if the model code will overfit. The purpose of implementing this test is to evaluate if we need to debug our code before stepping further into model development. Although it is designed for DL models, it is also a generalizable test that can be performed on tree-based or linear models.

How to test?
------------

This tests may require additional dependencies & environment to call model package API to ensure the model code will function correctly. To construct such tests, a rule of thumb would be to check we are overfitting the training data. So in this case, we have a higher confidence to continue with the model code and proceed with the model development.


