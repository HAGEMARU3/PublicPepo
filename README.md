# dev
import os
import requests
import json
import time

os.environ['HTTP_PROXY']
os.environ['HTTPS_PROXY']

def main():
    alerturl = 'https://api.mackerelio.com/api/v0/alerts'
    
    pjdapi = '9HdYfKoyrxk8RX7KmfgPiADoVV3JJ5f41fynoe5QtSEw'
    headers = {'X-API-KEY' : pjdapi}
    r = requests.get(alerturl, headers=headers) 
    x = r.json()
    pjdcri = len([alt for alt in x['alerts'] if alt['status'] == 'CRITICAL'])
    print(pjdcri) 
    pjdwarn = len([alt for alt in x['alerts'] if alt['status'] == 'WARNING'])
    print(pjdwarn) 

    kibanapi = '27PocmNEt1qcZmbgSzqpRniwNXyJJPj9M7RastFCZoPe'
    headers = {'X-API-KEY' : kibanapi}
    r = requests.get(alerturl, headers=headers) 
    x = r.json()
    kibancri = len([alt for alt in x['alerts'] if alt['status'] == 'CRITICAL'])
    print(kibancri) 
    kibanwarn = len([alt for alt in x['alerts'] if alt['status'] == 'WARNING'])
    print(kibanwarn)

    senbeiapi = '27PocmNEt1qcZmbgSzqpRniwNXyJJPj9M7RastFCZoPe'
    headers = {'X-API-KEY' : senbeiapi}
    r = requests.get(alerturl, headers=headers) 
    x = r.json()
    senbeicri = len([alt for alt in x['alerts'] if alt['status'] == 'CRITICAL'])
    print(senbeicri) 
    senbeiwarn = len([alt for alt in x['alerts'] if alt['status'] == 'WARNING'])
    print(senbeiwarn)



    url = 'https://api.mackerelio.com/api/v0/services/AlertOverview/tsdb'
    api = '9HdYfKoyrxk8RX7KmfgPiADoVV3JJ5f41fynoe5QtSEw'
    headers = {'X-API-KEY' : api}
    headers['Content-Type'] = 'application/json'
    
    altinfo = {
        "name": "SeNBeI",
        "time": 158587652,
        "value": 1
        }

    po = requests.post(url, data=json.dumps(altinfo), headers=headers)
    po.status_code
    print(po)

if __name__== '__main__':
    main()
    
    *******************
    import requests #POSTリクエストを送信する
import json #POST入力をJSON形式で行う
 
url = 'https://api.mackerelio.com/api/v0/monitors'
api = '9HdYfKoyrxk8RX7KmfgPiADoVV3JJ5f41fynoe5QtSEw'
 
headers = {'X-API-KEY' : api}
headers['Content-Type'] = 'application/json'
 
moninfo = {
  "type": "host",
  "name": "API TESTだよーん",
  "duration": 3,
  "warning": 200,
  "critical": 400,
  "operator": ">",
  "metric": "disk.aa-00.writes.delta",
  "memo": "APIテストだよーんThis monitor is TEST",
  "maxCheckAttempts": 3,
  "notificationInterval": 60,
  "isMute": True
  }

po = requests.post(url, data=json.dumps(moninfo), headers=headers)
po.status_code  
print(po)

*****
import os
import requests #POSTリクエストを送信する
import json #POST入力をJSON形式で行う

os.environ['HTTP_PROXY'] #環境変数を参照
os.environ['HTTPS_PROXY'] #環境変数から参照
 
url = 'https://api.mackerelio.com/api/v0/graph-defs/create'
api = '9HdYfKoyrxk8RX7KmfgPiADoVV3JJ5f41fynoe5QtSEw'
 
headers = {'X-API-KEY' : api}
headers['Content-Type'] = "application/json"
 
graphDef = {
  "name": "custom.ping-A100.*",
  "displayName": "コロナ拡大拠点",
  "unit": "float"
}

metric = {
    "name": "demodemo",
    "displayName": "コロナ拡大拠点",
    "isStacked": True
    }

json_data=json.dumps({'graphDef': graphDef, 'metric': metric})
po = requests.post(url, json_data, headers=headers)
po.status_code
print(po)

    
    
