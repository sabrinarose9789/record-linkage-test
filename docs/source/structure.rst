Repository Structure
====================

``./``

- ``run_match.py``: central workflow script to run a match
- ``config.py``: template for configuration file

``archive/``
Archived code and configurations from prototyping.

``match_rates/``
Code for analyzing match results.

``matching/``
Code for blocking and generating pair-wise match results.

``postprocessing/``
Code for postprocessing the match, generating ID crosswalks, and joining crosswalk to original data.

``preprocessing/``
Code for preprocessing and importing data to Postgres.

``shared/``
Code for shared functions used by scripts
