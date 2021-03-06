# WASE

WASE is a shortcut for Web Audit Search Engine. It's a framework for indexing HTTP requests/responses while web
application audits in an ElasticSearch instance and enriching it with useful data. The indexed data can then be searched
and aggregated with ElasticSearch queries or with Kibana.

Currently WASE contains the following parts:

* doc\_HttpRequestResponse.py: a library that implements the DocHTTPRequestResponse class. This class is an
  elasticsearch\_dsl-based storage class of HTTP requests/responses (derived from Burps data structures and API).
* ElasticBurp: a Burp plugin that feeds requests/responses into ElasticSearch.

## ElasticBurp

Scared about the weak searching performance of Burp Suite? Are you missing possibilities to search in Burp? ElasticBurp
combines Burp Suite with the search power of ElasticSearch.

### Installation

1. Install ElasticSearch and Kibana.
2. Configure both - For security reasons it is recommend to let them listen on localhost:
  * Set `network.host: 127.0.0.1` in `/etc/elasticsearch/elasticsearch.yml`.
  * Set `host: "127.0.0.1"` in `/opt/kibana/config/kibana.yml`.
3. Load ElasticBurp.py as Python extension in Burp Extender.
  * Jython module folder must be set to WASE source root (for doc_HttpRequestResponse)
  * tzlocal, elasticsearch and elasticsearch_dsl must be installed in the used Jython/Python environment.

## WASEQuery

Search ElasticSearch indices created by WASE for

* responses with missing headers
* responses with missing parameters
* all values that were set for a header (e.g. X-Frame-Options, X-XSS-Protection, X-Content-Type-Options, Content-Security-Policy, ...)

...or do arbitrary search queries.

Invoke WASEQuery.py for help message.
