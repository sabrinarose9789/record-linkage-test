Welcome to Record Linkage (name pending)'s documentation!
===================================

This is a deterministic record linkage tool developed by the Chapin Hall ETL team
for linking administrative data. The tool matches individuals across two datasets
or deduplicates within one dataset using a set of personal identifying information
(names, birthdate, ID, geography, etc.) and a set of rules to identify a set of
unique individuals relevant to the research population.

This tool is applicable for 1-to-1, 1-to-many, many-to-many matches and 
deduplications. Each link is performed under three confidence levels 
(strict, moderate, relaxed), which reflect the level of certainty of match results,
each codified by a specific set of rules. This allows for sensitivity testing of
research results based on the strictness of match logic. The rules used by the
deterministic matching algorithm are based on background knowledge and extensive
testing on IL and Chicago administrative data.

More details about the algorith can be found in `Can we link Sharepoint? <https://world.openfoodfacts.org/>`_

Check out the :doc:`usage` section for further information, including
how to :ref:`installation` the project.
.. note::

   This project is under active development.

Contents
--------

.. toctree::

   usage
   api
