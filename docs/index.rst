.. xata-py documentation master file, created by
   sphinx-quickstart on Sat Oct  1 12:34:50 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Python SDK for Xata
===================

This is a the official low-level Python client for the Xata_ service.
Xata is a Serverless Database that is as easy to use as a spreadsheet, has the
data integrity of PostgreSQL, and the search and analytics functionality of
Elasticsearch.


Installation
------------

Install the `xata` package from PyPI:

.. code-block:: bash

    $ pip install xata

While not strictly required, we recommend installing the Xata_CLI_ and initializing
your project with the `xata init` command:

.. code-block:: bash

    $ xata init

This will then interactively ask you to select a Database, and store the required
connection information in `.xatarc` and `.env`. The Python SDK automatically reads those
files, but it's also possible to pass the connection information directly to the
`xata.Client` constructor.

Example Usage
-------------
.. code-block:: python

    import xata

    client = xata.client.XataClient()

    # create a record
    client.create("Posts", record={"title": "Hello World", "slug": "hello-world"})

    # get one record
    post = client.get_first("Posts", filter={"slug": "hello-world"})
    print(post)

    # make a query
    page = client.query("Posts", filter={"title": "Hello World"})
    print page.get("records")

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   api



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

.. _Xata: https://xata.io
.. _Xata_CLI: https://xata.io/docs/cli/getting-started
