freesound.py
============

A python client for the [Freesound](http://freesound.org) APIv2.

Find the API documentation at http://www.freesound.org/docs/api/. 
Apply for an API key at https://www.freesound.org/apiv2/apply/. 

The client automatically maps function arguments to http parameters of the API. 
JSON results are converted to python objects, but are also available in their original form (JSON loaded into dictionaries) using the method `.as_dict()` of returned objets (see [examples file](https://github.com/MTG/freesound-python/blob/master/examples.py)). 
The main object types (`Sound`, `User`, `Pack`) are augmented with the corresponding API calls.

Note that POST resources are not supported. Downloading full quality sounds requires Oauth2 authentication (see http://freesound.org/docs/api/authentication.html). Oauth2 authentication is supported, but you are expected to implement the workflow.

Example usage:

```python
import freesound, sys,os

client = freesound.FreesoundClient()
client.set_token("<your_api_key>","token")

results = client.text_search(query="dubstep",fields="id,name,previews")

for sound in results:
    sound.retrieve_preview(".",sound.name+".mp3")
    print(sound.name)

```

Installation
============
1) clone or download

2) run:
```
python setup.py install
```
