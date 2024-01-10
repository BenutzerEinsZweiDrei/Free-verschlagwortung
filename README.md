# Free-verschlagwortung
Remember cortical io


```python
import requests
import time

# import nltk # if you need hypernyms
# from nltk.corpus import wordnet as wn


def keyword(text):
	url = "https://gw.cortical.io/nlp/keywords"
	headers = { "Content-Type": "application/json", "Authorization": ""}
	data = { "text": text, "language": "en"}

	# send request
	r = requests.post(url, headers=headers, json=data)
	# print(r.status_code)

	# read response
	j = r.json()
	
	if r.status_code == 200 and j["keywords"]:
		# print(j["keywords"][0]["word"])
		
		time.sleep(0.6) # wait for only 2 requests per minute
		return j["keywords"][0]["word"]
	else:
	    return ""

text = "lorem ipsum"
print(keyword(text))
```
