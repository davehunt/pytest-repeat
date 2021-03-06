pytest-repeat
===================

pytest-repeat is a plugin for `py.test <http://pytest.org>`_ that makes it easy
to repeat a single test, or multiple tests, a specific number of times.

.. image:: https://img.shields.io/badge/license-MPL%202.0-blue.svg
   :target: https://github.com/pytest-dev/pytest-repeat/blob/master/LICENSE
   :alt: License
.. image:: https://img.shields.io/pypi/v/pytest-repeat.svg
   :target: https://pypi.python.org/pypi/pytest-repeat/
   :alt: PyPI
.. image:: https://img.shields.io/travis/pytest-dev/pytest-repeat.svg
   :target: https://travis-ci.org/pytest-dev/pytest-repeat/
   :alt: Travis
.. image:: https://img.shields.io/github/issues-raw/pytest-dev/pytest-repeat.svg
   :target: https://github.com/pytest-dev/pytest-repeat/issues
   :alt: Issues
.. image:: https://img.shields.io/requires/github/pytest-dev/pytest-repeat.svg
   :target: https://requires.io/github/pytest-dev/pytest-repeat/requirements/?branch=master
   :alt: Requirements

Requirements
------------

You will need the following prerequisites in order to use pytest-repeat:

- Python 2.6, 2.7, 3.2, 3.3, 3.4, 3.5 or PyPy
- py.test 2.8 or newer

Installation
------------
To install pytest-repeat:

.. code-block:: bash

  $ pip install pytest-repeat

Repeating a test
----------------

Use the :code:`--count` command line option to specify how many times you want
your test, or tests, to be run:

.. code-block:: bash

  $ py.test --count=10 test_file.py

Each test collected by py.test will be run :code:`count` times.

If you want to mark a test in your code to be repeated a number of times, you
can use the :code:`@pytest.mark.repeat(count)` decorator:

.. code-block:: python

   import pytest


   @pytest.mark.repeat(3)
   def test_repeat_decorator():
       pass

Repeating a test until failure
------------------------------

If you are trying to diagnose an intermittent failure, it can be useful to run the same
test over and over again until it fails. You can use py.test's :code:`-x` option in
conjunction with pytest-repeat to force the test runner to stop at the first failure.
For example:

.. code-block:: bash

  $ py.test --count=1000 -x test_file.py

This will attempt to run test_file.py 1000 times, but will stop as soon as a failure
occurs.

UnitTest Style Tests
--------------------

Unfortunately pytest-repeat is not able to work with unittest.TestCase test classes.
These tests will simply always run once, regardless of :code:`--count`, and show a warning.

Resources
---------

- `Release Notes <http://github.com/pytest-dev/pytest-repeat/blob/master/CHANGES.rst>`_
- `Issue Tracker <http://github.com/pytest-dev/pytest-repeat/issues>`_
- `Code <http://github.com/pytest-dev/pytest-repeat/>`_
