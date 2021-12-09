********************
Infrastructure Tests
********************

Reproducible Training
=====================


What to test?
-------------

Like all scientific experiments, we want our model experiments to yield the same results whenever or wherever we implement them. Thus we impose the criteria for our modelOps system to ensure reproducibility. To achieve reproducible results, we generally looking at three components:

- Model code/Model Specs
- Data
- Environment (package dependencies, environment setup) Therefore, the reproducible tests would center around how to ensure the correct version of these components are used.



How to test?
------------

To construct a test on the reproducibility, it would be as simple as checking the correct version of aforementioned three components. Yet in practice, we might need to consider the numerical stability of the reproduction since randomness is introduced when training sophisticated models.

Version Model & Serving Specs
=============================


What to test?
-------------

To differentiate this test with the test for versioned model & spec, this test would focus on unit-testing on small sample or synthetic data before serving Model API. This test is a smoke test to see if the model is deployed correctly with the right model and specs.



How to test?
------------

This test came natural once we have inspection on the capability of versioned model and model specs. What we need to ensure is to construct a test that will have inference that met the expectation.

.. figure:: docs/source/images/train_module.png
   :align: center
   A reproducible training module backed by Mlflow and Azure service



Model Validation Pipeline Testing
=================================



What to test?
-------------

This test is designed for model pipeline check for debugging purposes. Usually this test would be automated by CI/CD integration with the model pipeline.




How to test?
------------

This test would largely depends on how you design the pipeline. A simple pass to test this pipeline would be to see if the pipeline would be successfully executed. A more detailed test can be constructed based on the expectation on the entry and the exit of each pipeline component.

Model Quality Validation Testing
================================


What to test?
-------------

In software development when engineers want to deploy new features, a standard practice is to canaried the new feature with incoming traffic and see how it performed against the old ones. We are borrowing a similar approach when designing model quality validation test where we are diverting a portion of the incoming data stream for inference on to the new model and compared that against the old model. This way we are able crisply compare how models are performed in terms of its prediction quality and provide insights to the model deployment decisions.



How to test?
------------

Model quality validation is treated as a design guidance in the ML testing framework were we scrutinize the process of modelOps and see if this idea is adopted.

.. figure:: docs/source/images/canaried.png
   :align: center
   A canaried scenario for software deployment rollout

Roll-back Tests
===============


What to test?
-------------

The roll-back tests are used to ensure that there would always be a back-up model that is ready to go into production if any issues arise. It would provide a safety net for deployment to enhance the robustness of the ML system.


How to test?
------------

There are several considerations when constructing the roll-back tests:

- The deployment environment for the roll-back model should be the same for the deployed model.
- The process of reverting the deployment to the roll-back model should be seamless.
- This process should also considered to be automated when given 'red flag' in the deployment: inference error, in correct prediction and etc.

.. figure:: docs/source/images/roll_back.png
   :align: center
   The workflow to test rollback tests




