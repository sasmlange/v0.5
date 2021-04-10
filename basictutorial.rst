Basic Tutorial
===============

Introduction
-------------

In this tutorial you will make a Table Base **Table** object that contains
names of cities and their population. We will then filter the table
for cities that have a population greater then a value.


Step 1: Importing and Installing Table Base
--------------------------------------------

The first step to use Table Base is to install it. If you have already
installed Table Base skip to step two.

You can install Table Base with pypi (pip). Run the following code in the
terminal

.. code-block:: bash

    pip install tablebase

This code should have an output like this:

.. code-block:: bash

    Collecting tablebase
      Using cached tablebase-0.5.tar.gz (1.5 kB)
    Using legacy 'setup.py install' for tablebase, since package 'wheel' is not installed.
    Installing collected packages: tablebase
        Running setup.py install for tablebase ... done
    Successfully installed tablebase-0.5

Great! You have installed table base!

Not working? `Report a bug. <https://github.com/sasmlange/tablebase/issues>`_

Lets test that we really installed Table Base. In a python script, execute
this line of code.

.. code-block:: python
    :emphasize-lines: 1

    import tablebase

If this code has no output, then you have installed Table Base successfully!

`Report a bug. <https://github.com/sasmlange/tablebase/issues>`_


Step 2: Make a blank table
---------------------------

To make a table you must make a Table Base **Table** object. What is the
**Table** object? The **Table** object is a blank table with all the
commands (filter, new row, ect.).

To make a **table** object do the following:

.. code-block:: python
    :emphasize-lines: 3

    import tablebase

    My_Table = tablebase.Table()

What did we do in the code above? We imported Table Base. We then set
**My_Table** to a blank table.

Step 3: Add Columns
--------------------

We made a blank table, we now want to add columns. To do this we use the
**add_col** method.

Lets add the following columns: City, Founder, Population

.. code-block:: python
    :emphasize-lines: 5, 6, 7

    import tablebase

    My_Table = tablebase.Table()

    My_Table.add_col("City")
    My_Table.add_col("Founder")
    My_Table.add_col("Population")

Step 4: Adding Rows
--------------------------

To add a row we use the **add_row** method. The **add_row** method adds a
list to the takes that the user provides.

Lets add the following rows: Los Angeles, New York, Plymouth

.. code-block::
    :emphasize-lines: 9, 10, 11

    import tablebase

    My_Table = tablebase.Table()

    My_Table.add_col("City")
    My_Table.add_col("Founder")
    My_Table.add_col("Population")

    My_Table.add_row(["Los Angeles", "Felipe de Neve", "3967000"])
    My_Table.add_row(["New York", "Peter Minuit", "8419000"])
    My_Table.add_row(["Plymouth", "William Bradford", "60803"])


Step 5: Print Table to Console
------------------------------

We have made our table with all the rows and columns we want. We now just
want to see our table.

To do this we will use the **table_content** variable.

.. code-block:: python
    :emphasize-lines: 13

    import tablebase

    My_Table = tablebase.Table()

    My_Table.add_col("City")
    My_Table.add_col("Founder")
    My_Table.add_col("Population")

    My_Table.add_row(["Los Angeles", "Felipe de Neve", "3967000"])
    My_Table.add_row(["New York", "Peter Minuit", "8419000"])
    My_Table.add_row(["Plymouth", "William Bradford", "60803"])

    print(My_Table.table_content)

This code should give a result like this:

.. code-block:: bash

    [['City', 'Founder', 'Population'], ['Los Angeles', 'Felipe de Neve', '3967000'], ['New York', 'Peter Minuit', '8419000'], ['Plymouth', 'William Bradford', '60803']]

Wait a minute. Is this a table? Yes it is. Lets make it look nicer:

.. code-block:: bash

    [
        ['City', 'Founder', 'Population'],
        ['Los Angeles', 'Felipe de Neve', '3967000'],
        ['New York', 'Peter Minuit', '8419000'],
        ['Plymouth', 'William Bradford', '60803']
    ]

Ahh. Now it looks like a table. The first row is the column header and the
next are the rows. The table is one big list. The rows are also lists


.. tip::

    You can use **table_content** to overwrite the table with a new one.

        My_Table.table_content = [["Col1", "Col2"], ["11", "12"], ["21", "22"]]

Step 6: Filter the table
-------------------------

We now want to filter the table by population the is greater then 1
million.

We will use the **filter** method to filter the table and then print out the result.

.. code-block:: python
    :emphasize-lines: 15

    import tablebase

    My_Table = tablebase.Table()

    My_Table.add_col("City")
    My_Table.add_col("Founder")
    My_Table.add_col("Population")

    My_Table.add_row(["Los Angeles", "Felipe de Neve", "3967000"])
    My_Table.add_row(["New York", "Peter Minuit", "8419000"])
    My_Table.add_row(["Plymouth", "William Bradford", "60803"])

    print(My_Table.table_content)

    print(My_Table.filter("Population", "1000000", "greaterthan"))

What did we just do? We filtered the **Population** column in **My_Table**
with the **filter** method for cities that have a population greater than
1 million (1000000) people. For more information see
:ref:`Introduction <the filter method>`

The result should look something like this (Note: This result is
formatted to be more readable):

.. code-block:: bash

    [
        ['City', 'Founder', 'Population'],
        ['Los Angeles', 'Felipe de Neve', '3967000'],
        ['New York', 'Peter Minuit', '8419000'],
        ['Plymouth', 'William Bradford', '60803']
    ]

    [
        ['City', 'Founder', 'Population'],
        ['Los Angeles', 'Felipe de Neve', '3967000'],
        ['New York', 'Peter Minuit', '8419000']
    ]

Notice how the second table does not have Plymouth because it does not have a
population greater than 1 million.