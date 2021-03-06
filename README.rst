=============
ckanext-searchfed
=============

Search additional datasets by your query using CKAN package_search API similar to harvester(url from ``ckan.search_federation``). If
count of found datasets less than ``ckan.search_federation.min_search_results`` federation search will add additional results below
local results from dataportals that set in ``ckan.search_federation`` field at your config file. If field ``ckan.search_federation``
not set than additional search will not run.


------------
Installation
------------

.. Add any additional install steps to the list below.
   For example installing any non-Python dependencies or adding any required
   config settings.

To install ckanext-searchfed:

1. Activate your CKAN virtual environment, for example::

     . /usr/lib/ckan/default/bin/activate

2. Install the ckanext-searchfed Python package into your virtual environment::

     pip install ckanext-searchfed

3. Add ``searchfed`` to the ``ckan.plugins`` setting in your CKAN
   config file (by default the config file is located at
   ``/etc/ckan/default/production.ini``).

4. Restart CKAN. For example if you've deployed CKAN with Apache on Ubuntu::

     sudo service apache2 reload


---------------
Config Settings
---------------

    1. Label and URL for sites where search can take data (if empty default value = {}). This labels will appears to the left of dataset title additional results. For example Label = ``FROM DATA.BRISBANE.GOV.AU``, URL = ``https://data.brisbane.qld.gov.au/data``:

        ckan.search_federation = data.brisbane.gov.au https://data.brisbane.qld.gov.au/data data.gov.au http://data.gov.au

    2. Also use with ckan.search_federation labels for filter query (if empty default value = ""). For example ['data.brisbane.gov.au', 'data.gov.au', 'data.sa.gov.au']:

        ckan.search_federation.label = data.sa.gov.au

    3. Use for filter query when fetch data. In result we will have filter query for search for example ``-harvest_portal:data.brisbane.gov.au`` (if empty default value = 'harvest_portal'):

        ckan.search_federation.extra_keys = harvest_portal search_federation_portal

    4. If true and 'search_facets' in remote search results we will use remote search facets instead local facets (if empty default value = False):

        ckan.search_federation.use_remote_facet_results = false

    5. If local results is less than ``ckan.search_federation.min_search_results`` value, searchfed will run and added more datasets below local results (if empty default value = 20):

        ckan.search_federation.min_search_results = 3


------------------------
Development Installation
------------------------

To install ckanext-searchfed for development, activate your CKAN virtualenv and
do::

    git clone https://github.com//ckanext-searchfed.git
    cd ckanext-searchfed
    python setup.py develop
    pip install -r dev-requirements.txt
