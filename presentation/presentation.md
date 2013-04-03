---
# Introduction To Elasticsearch at Needle
---
# What is it?

* Distributed RESTful search and analytics 
* Lucene underneath
* Java == Fast
* Schemaless
* JSON
---
# Realtime Data and Analtytics

Elasticsearch can handle many, many inserts. 
It indexes them almost instantly.
---
# Distributed

It is built to scale horizontally out of the box. As we need more capacity, we just add more nodes. 
The cluster will automatically reorganize itself to take advantage of the extra hardware.
---
# High Availability

* Autodetects and removes falied nodes
* Reorganizes shards and nodes accordingly
---
# Multi-tenancy

* Multiple indexes 
* Search independently, or across all indexes with almost no performance penalty
* We use different indexes per partner
---
# Full text search

* Lucene
* Multi language support
* Great query language
* Geolocation capabilities
* Context aware (did you mean...?)
* Autocomplete
* Scoring, keyword highlighting, so many other awesomeness.
---
# Schemaless Documents
Camdan2003
* Auto mapping
* JSON
	
	{
		'unique_id': 0,
		'date': None,
		'partner_date': None,
		'needlers': None,
		'customer': None,
		'customer_email': None,
		'chat_text': chat_text,
		'classification': None,
		'tags': [],
		'questions': [],
	}
---
# Defined Mappings

			{

                "unique_id": {
                    "index": "not_analyzed",
                    "store": "yes",
                    "type": "string"
                },
                "date": {
                    "type": "long",
                    "store": "yes",
                    "index": "analyzed"
                },
                "chat_text": {
                    "type": "string",
                    "store": "yes",
                    "index": "analyzed",
                    "null_value": "NA"
                }
            }
---
# RESTful API

Elasticsearch is API driven. Almost any action can be peformed using a simple RESTful API using JSON over HTTP.

	$ curl -XPUT 'http://localhost:9200/twitter/tweet/1' -d '{
    "user" : "myself",
    "post_date" : "2013-03-129T14:12:12",
    "message" : "Indexing this message"
	}'

	curl -XGET 'http://localhost:9200/skullcandy/transcript/1'
---
# How Does Needle Use It

* Post Insert
* Transformer
* Index references MongoDB

Core > Haystack > Transformer > Index
---

