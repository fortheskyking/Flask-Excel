================================================================================
Flask-Excel - Let you focus on data, instead of file formats
================================================================================

.. image:: https://raw.githubusercontent.com/pyexcel/pyexcel.github.io/master/images/patreon.png
   :target: https://www.patreon.com/chfw

.. image:: https://travis-ci.org/pyexcel-webwares/Flask-Excel.svg?branch=master
   :target: http://travis-ci.org/pyexcel-webwares/Flask-Excel

.. image:: https://codecov.io/gh/pyexcel-webwares/Flask-Excel/branch/master/graph/badge.svg
   :target: https://codecov.io/gh/pyexcel-webwares/Flask-Excel

.. image:: https://badge.fury.io/py/Flask-Excel.svg
   :target: https://pypi.org/project/Flask-Excel


.. image:: https://pepy.tech/badge/Flask-Excel/month
   :target: https://pepy.tech/project/Flask-Excel/month


.. image:: https://img.shields.io/gitter/room/gitterHQ/gitter.svg
   :target: https://gitter.im/pyexcel/Lobby

.. image:: https://readthedocs.org/projects/flask-excel/badge/?version=latest
   :target: http://flask-excel.readthedocs.org/en/latest/

Support the project
================================================================================

If your company has embedded pyexcel and its components into a revenue generating
product, please support me on `github <https://github.com/sponsors/chfw>`_, `patreon <https://www.patreon.com/bePatron?u=5537627>`_
or `bounty source <https://salt.bountysource.com/teams/chfw-pyexcel>`_ to maintain
the project and develop it further.

If you are an individual, you are welcome to support me too and for however long
you feel like. As my backer, you will receive
`early access to pyexcel related contents <https://www.patreon.com/pyexcel/posts>`_.

And your issues will get prioritized if you would like to become my patreon as `pyexcel pro user`.

With your financial support, I will be able to invest
a little bit more time in coding, documentation and writing interesting posts.


Known constraints
==================

Fonts, colors and charts are not supported.

Introduction
================================================================================
Here is a typical conversation between the developer and the user::

 User: "I have uploaded an excel file"
       "but your application says un-supported file format"
 Developer: "Did you upload an xlsx file or a csv file?"
 User: "Well, I am not sure. I saved the data using "
       "Microsoft Excel. Surely, it must be in an excel format."
 Developer: "OK. Here is the thing. I were not told to support"
            "all available excel formats in day 1. Live with it"
            "or delay the project x number of days."

**Flask-Excel** is based on `pyexcel <https://github.com/pyexcel/pyexcel>`_ and makes
it easy to consume/produce information stored in excel files over HTTP protocol as
well as on file system. This library can turn the excel data into a list of lists,
a list of records(dictionaries), dictionaries of lists. And vice versa. Hence it
lets you focus on data in Flask based web development, instead of file formats.

The idea originated from the common usability problem: when an excel file
driven web application is delivered for non-developer users (ie: team assistant,
human resource administrator etc). The fact is that not everyone knows (or cares) about the
differences between various excel formats: csv, xls, xlsx are all the same to them. Instead of training those users
about file formats, this library helps web developers to handle most of the excel file
formats by providing a common programming interface. To add a specific excel file format type
to you application, all you need is to install an extra pyexcel plugin. Hence no code changes
to your application and no issues with excel file formats any more. Looking at the
community, this library and its associated ones try to become a small and easy to
install alternative to Pandas.


The highlighted features are:

#. excel data import into and export from databases
#. turn uploaded excel file directly into Python data structure
#. pass Python data structures as an excel file download
#. provide data persistence as an excel file in server side
#. supports csv, tsv, csvz, tsvz by default and other formats are supported via
   the following plugins:

.. _file-format-list:
.. _a-map-of-plugins-and-file-formats:

.. table:: A list of file formats supported by external plugins

   ======================== ======================= ================= ==================
   Package name              Supported file formats  Dependencies     Python versions
   ======================== ======================= ================= ==================
   `pyexcel-io`_            csv, csvz [#f1]_, tsv,                    2.6, 2.7, 3.3,
                            tsvz [#f2]_                               3.4, 3.5, 3.6
                                                                      pypy
   `pyexcel-xls`_           xls, xlsx(read only),   `xlrd`_,          same as above
                            xlsm(read only)         `xlwt`_
   `pyexcel-xlsx`_          xlsx                    `openpyxl`_       same as above
   `pyexcel-ods3`_          ods                     `pyexcel-ezodf`_, 2.6, 2.7, 3.3, 3.4
                                                    lxml              3.5, 3.6
   `pyexcel-ods`_           ods                     `odfpy`_          same as above
   ======================== ======================= ================= ==================

.. table:: Dedicated file reader and writers

   ======================== ======================= ================= ==================
   Package name              Supported file formats  Dependencies     Python versions
   ======================== ======================= ================= ==================
   `pyexcel-xlsxw`_         xlsx(write only)        `XlsxWriter`_     Python 2 and 3
   `pyexcel-xlsxr`_         xlsx(read only)         lxml              same as above
   `pyexcel-xlsbr`_         xlsx(read only)         pyxlsb            same as above
   `pyexcel-odsr`_          read only for ods, fods lxml              same as above
   `pyexcel-odsw`_          write only for ods      loxun             same as above
   `pyexcel-htmlr`_         html(read only)         lxml,html5lib     same as above
   `pyexcel-pdfr`_          pdf(read only)          pdftables         Python 2 only.
   ======================== ======================= ================= ==================


.. _pyexcel-io: https://github.com/pyexcel/pyexcel-io
.. _pyexcel-xls: https://github.com/pyexcel/pyexcel-xls
.. _pyexcel-xlsx: https://github.com/pyexcel/pyexcel-xlsx
.. _pyexcel-ods: https://github.com/pyexcel/pyexcel-ods
.. _pyexcel-ods3: https://github.com/pyexcel/pyexcel-ods3
.. _pyexcel-odsr: https://github.com/pyexcel/pyexcel-odsr
.. _pyexcel-odsw: https://github.com/pyexcel/pyexcel-odsw
.. _pyexcel-pdfr: https://github.com/pyexcel/pyexcel-pdfr

.. _pyexcel-xlsxw: https://github.com/pyexcel/pyexcel-xlsxw
.. _pyexcel-xlsxr: https://github.com/pyexcel/pyexcel-xlsxr
.. _pyexcel-xlsbr: https://github.com/pyexcel/pyexcel-xlsbr
.. _pyexcel-htmlr: https://github.com/pyexcel/pyexcel-htmlr

.. _xlrd: https://github.com/python-excel/xlrd
.. _xlwt: https://github.com/python-excel/xlwt
.. _openpyxl: https://bitbucket.org/openpyxl/openpyxl
.. _XlsxWriter: https://github.com/jmcnamara/XlsxWriter
.. _pyexcel-ezodf: https://github.com/pyexcel/pyexcel-ezodf
.. _odfpy: https://github.com/eea/odfpy

.. table:: Other data renderers

   ======================== ======================= ================= ==================
   Package name              Supported file formats  Dependencies     Python versions
   ======================== ======================= ================= ==================
   `pyexcel-text`_          write only:rst,         `tabulate`_       2.6, 2.7, 3.3, 3.4
                            mediawiki, html,                          3.5, 3.6, pypy
                            latex, grid, pipe,
                            orgtbl, plain simple
                            read only: ndjson
                            r/w: json
   `pyexcel-handsontable`_  handsontable in html    `handsontable`_   same as above
   `pyexcel-pygal`_         svg chart               `pygal`_          2.7, 3.3, 3.4, 3.5
                                                                      3.6, pypy
   `pyexcel-sortable`_      sortable table in html  `csvtotable`_     same as above
   `pyexcel-gantt`_         gantt chart in html     `frappe-gantt`_   except pypy, same
                                                                      as above
   ======================== ======================= ================= ==================

.. _pyexcel-text: https://github.com/pyexcel/pyexcel-text
.. _tabulate: https://bitbucket.org/astanin/python-tabulate
.. _pyexcel-handsontable: https://github.com/pyexcel/pyexcel-handsontable
.. _handsontable: https://cdnjs.com/libraries/handsontable
.. _pyexcel-pygal: https://github.com/pyexcel/pyexcel-chart
.. _pygal: https://github.com/Kozea/pygal
.. _pyexcel-matplotlib: https://github.com/pyexcel/pyexcel-matplotlib
.. _matplotlib: https://matplotlib.org
.. _pyexcel-sortable: https://github.com/pyexcel/pyexcel-sortable
.. _csvtotable: https://github.com/vividvilla/csvtotable
.. _pyexcel-gantt: https://github.com/pyexcel/pyexcel-gantt
.. _frappe-gantt: https://github.com/frappe/gantt

In order to manage the list of plugins installed, you need to use pip to add or remove
a plugin. When you use virtualenv, you can have different plugins per virtual
environment. In the situation where you have multiple plugins that does the same thing
in your environment, you need to tell pyexcel which plugin to use per function call.
For example, pyexcel-ods and pyexcel-odsr, and you want to get_array to use pyexcel-odsr.
You need to append get_array(..., library='pyexcel-odsr').

.. rubric:: Footnotes

.. [#f1] zipped csv file
.. [#f2] zipped tsv file


This library makes information processing involving various excel files as easy as
processing array, dictionary when processing file upload/download, data import into
and export from SQL databases, information analysis and persistence. It uses
**pyexcel** and its plugins:

#. to provide one uniform programming interface to handle csv, tsv, xls, xlsx, xlsm and ods formats.
#. to provide one-stop utility to import the data in uploaded file into a database and to export tables in a database as excel files for file download.
#. to provide the same interface for information persistence at server side: saving a uploaded excel file to and loading a saved excel file from file system.



Tested Flask Versions
========================

.. image:: https://img.shields.io/badge/Flask-0.12.2-green.svg
    :target: http://travis-ci.org/pyexcel/Flask-Excel

.. image:: https://img.shields.io/badge/Flask-0.11.1-green.svg
    :target: http://travis-ci.org/pyexcel/Flask-Excel

.. image:: https://img.shields.io/badge/Flask-0.10.1-green.svg
    :target: http://travis-ci.org/pyexcel/Flask-Excel



Installation
================================================================================

You can install Flask-Excel via pip:

.. code-block:: bash

    $ pip install Flask-Excel


or clone it and install it:

.. code-block:: bash

    $ git clone https://github.com/pyexcel-webwares/Flask-Excel.git
    $ cd Flask-Excel
    $ python setup.py install



Usage
================================================================================

Here are some example codes:

.. code-block:: python

    from flask import Flask, request, jsonify
    import flask_excel as excel

    app=Flask(__name__)
    flask_excel.init_excel(app)

    @app.route("/upload", methods=['GET', 'POST'])
    def upload_file():
        if request.method == 'POST':
            return jsonify({"result": request.get_array(field_name='file')})
        return '''
        <!doctype html>
        <title>Upload an excel file</title>
        <h1>Excel file upload (csv, tsv, csvz, tsvz only)</h1>
        <form action="" method=post enctype=multipart/form-data>
        <p><input type=file name=file><input type=submit value=Upload>
       </form>
        '''

    @app.route("/export", methods=['GET'])
    def export_records():
        return excel.make_response_from_array([[1,2], [3, 4]], "csv",
                                              file_name="export_data")

    if __name__ == "__main__":
        app.run()


Development guide
================================================================================

Development steps for code changes

#. git clone https://github.com/pyexcel/Flask-Excel.git
#. cd Flask-Excel

Upgrade your setup tools and pip. They are needed for development and testing only:

#. pip install --upgrade setuptools pip

Then install relevant development requirements:

#. pip install -r rnd_requirements.txt # if such a file exists
#. pip install -r requirements.txt
#. pip install -r tests/requirements.txt

Once you have finished your changes, please provide test case(s), relevant documentation
and update CHANGELOG.rst.

.. note::

    As to rnd_requirements.txt, usually, it is created when a dependent
    library is not released. Once the dependecy is installed
    (will be released), the future
    version of the dependency in the requirements.txt will be valid.


How to test your contribution
------------------------------

Although `nose` and `doctest` are both used in code testing, it is adviable that unit tests are put in tests. `doctest` is incorporated only to make sure the code examples in documentation remain valid across different development releases.

On Linux/Unix systems, please launch your tests like this::

    $ make

On Windows systems, please issue this command::

    > test.bat

How to update test environment and update documentation
---------------------------------------------------------

Additional steps are required:

#. pip install moban
#. make your changes in `.moban.d` directory, then issue command `moban`

What is pyexcel-commons
---------------------------------

Many information that are shared across pyexcel projects, such as: this developer guide, license info, etc. are stored in `pyexcel-commons` project.

What is .moban.d
---------------------------------

`.moban.d` stores the specific meta data for the library.



License
================================================================================

New BSD License
