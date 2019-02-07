

```python
# import python modules 
import requests
import time
import urllib3
import pprint
import json
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

# Set the request inputs
token = "fd8b3f95-adc6-406d-9c18-bdb155de2ced"
nb_url = "http://192.168.28.79"

#mgmIP1 = "10.1.13.2"
#mgmIP2 = "123.1.1.1"
#mgmIP3 = "10.1.14.2"
#mgmIP4 = "123.203.3.3"
#mgmIP5 = "123.204.4.4"
#mgmIP6 = "123.20.1.3"

mgmIP1 = "10.1.13.2"
mgmIP2 = "123.1.1.1"
mgmIP3 = "10.1.14.2"
mgmIP4 = "123.203.3.200"# no such device exist
mgmIP5 = "123.204.4.200"# no such device exist
mgmIP6 = "123.20.1.200"# no such device exist
taskID = "34124e63-31d6-dfad-f5fa-05ae0ebb4b49"
##OR##
#taskName = "testGDL_DT1"

body = {
    "seeds" : 
        [
            {"mgmtIP": mgmIP1},
            {"mgmtIP": mgmIP2},
            {"mgmtIP": mgmIP3},
            {"mgmtIP": mgmIP4},
            {"mgmtIP": mgmIP5},
            {"mgmtIP": mgmIP6}
        ]
    }
 
headers = {'Content-Type': 'application/json', 'Accept': 'application/json'}
headers["Token"]=token
full_url= nb_url + "/ServicesAPI/API//V1/CMDB/Discovery/Tasks/"+str(taskID)+"/Seeds"

try:
    # Do the HTTP request
    response = requests.post(full_url, data = json.dumps(body), headers=headers, verify=False)
    # Check for HTTP codes other than 200
    if response.status_code == 200:
        # Decode the JSON response into a dictionary and use the data
        result = response.json()
        print (result)
    else:
        print("IP Add Failed - " + str(response.text))
    
except Exception as e:
    print (str(e)) 

```

    IP Add Failed - {"statusCode":795005,"statusDescription":"Invalid token."}
    


```python

```
