Usage
=====

Set up
------
 
Clone this Git repository.

Add the subdirectory `/shared` to your `.bashrc` file located in your root directory. 
This directory contains code used by other modules in this repository and needs 
to be added to the user's `PYTHONPATH`. This can be done by adding the following 
line to `.bashrc`:

.. code-block:: console

    (.venv) $ export PYTHONPATH='<root_directory>/record-linkage/shared'


where `<root_directory>` is the path from the root directory to
the record-linkage directory.

Define match parameters
-----------------------

Edit ``config.py`` to define parameters of the input data, the match, and output.

** Note:** if using the preprocessing scripts, please define the variable mapping 
for each dataset based on the preprocessed variable names.

Preprocess data
---------------

For each dataset to be preprocessed, create a script based on ``preprocess_file_template.py``. If multiple files need to be processed, a preprocessing script must be created for each file. For the project for which the linkage is being completed, store the preprocessing script(s) in the corresponding project repository. Update the filepath "project_repo" in the config path with the path from your home directory to the directory the preprocessing scripts are stored for each dataset. Make sure to include the datasource's name in the name of each script created.

For any dataset that is in csv format and already processed to be combined with others, include the filepath in the config file under the "combine_prev_csv" for each dataset. Include any dataset currently in the database schema that has already been preprocessed in the config file under "combine_prev_tbl" for each dataset.

From the top level of the record linkage repository, run:

.. code-block:: console

    (.venv) $ python preprocessing/run_preprocess.py

If using files that can be used as is and need to be imported to a database,
you can use the following script instead:

.. code-block:: console

    (.venv) $ python ./preprocessing/import_prepped_data.py

Run a match from beginning to end
---------------------------------

Run the following at the root of this directory:

.. code-block:: console

    (.venv) $ python run_match.py [-c <path to config.py>]

A path to a copy of the config.py can be defined here if the configuration file
is saved in a different directory with a different file name than the root. 
Note that this script can run for some time, so consider using a terminal multiplexer
(such as `tmux <https://github.com/tmux/tmux/wiki>`).

Run a match by stage
--------------------

``run_match.py`` can be run  with the flags ``-sb`` to skip blocking and ``-sm`` to skip matching.

Alternatively, each of the following stage of the match can be run separately. See the scripts' doc string for how to run them.
- ``matching/block.py``
- ``matching/match.py``
- ``postprocessing/postprocess.py``

Analyze match results
---------------------

Run the following script to print summary statistics about the match 
(currently not applicable to M:M matches).

.. code-block:: console

    (.venv) $ python ./match_rates/get_match_rates.py
