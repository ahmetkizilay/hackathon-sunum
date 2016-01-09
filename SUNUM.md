# SUNUM

#### API DOKUMANLARI

> http://graphcommons.github.io/api-v1/

#### API ILE KESIF

Bir arama yapalim.
```sh
# calling: /search
# query=third wave
# limit=2
http 'http://localhost:3000/api/v1/search?query=third wave&limit=2' \
	   'Authentication:sk_0tPydJjFUebHd3lD501sag' \
	   'Content-type:application/json'
```

Graph'in tum bilgilerine bakalim.
```sh
# calling: /graphs/:id
# graph-id=c7a0590c-60cf-49ca-910a-1bd5940ce2c2
http 'http://localhost:3000/api/v1/graphs/c7a0590c-60cf-49ca-910a-1bd5940ce2c2' \
	   'Authentication:sk_0tPydJjFUebHd3lD501sag' \
	   'Content-type:application/json'
```

Graph'in sadece tiplerine bakalim.
```sh
# calling: /graphs/:id/types
# graph-id=c7a0590c-60cf-49ca-910a-1bd5940ce2c2
http 'http://localhost:3000/api/v1/graphs/c7a0590c-60cf-49ca-910a-1bd5940ce2c2/types' \
	   'Authentication:sk_0tPydJjFUebHd3lD501sag' \
	   'Content-type:application/json'
```

Node'a detayli bakalim
```sh
# calling: /nodes/:id
# node-id-id=046eec3f-11ab-3598-cd52-5d68b4235348 (dara)
http 'http://localhost:3000/api/v1/nodes/046eec3f-11ab-3598-cd52-5d68b4235348' \
	   'Authentication:sk_0tPydJjFUebHd3lD501sag' \
	   'Content-type:application/json'
```

Iki node arasi patikalar
```sh
# calling /graphs/:id/paths
# graph-id=c7a0590c-60cf-49ca-910a-1bd5940ce2c2 (Third Wave Coffee)
# from=626fe375-d55a-873f-91c4-5f6df6f0d560 (Ahmet)
# to=046eec3f-11ab-3598-cd52-5d68b4235348 (Dara)
http 'http://localhost:3000/api/v1/graphs/c7a0590c-60cf-49ca-910a-1bd5940ce2c2/paths?from=626fe375-d55a-873f-91c4-5f6df6f0d560&to=046eec3f-11ab-3598-cd52-5d68b4235348' \
	   'Authentication:sk_0tPydJjFUebHd3lD501sag' \
	   'Content-type:application/json'
```

Detayli patikalar
```sh
# calling: /graphs/:id/paths
# graph-id=c7a0590c-60cf-49ca-910a-1bd5940ce2c2 (Third Wave Coffee)
# from=626fe375-d55a-873f-91c4-5f6df6f0d560 (Ahmet)
# totype=Restaurant
# via=FAVORS,SERVES
# strict=true
http 'http://localhost:3000/api/v1/graphs/c7a0590c-60cf-49ca-910a-1bd5940ce2c2/paths?from=626fe375-d55a-873f-91c4-5f6df6f0d560&via=FAVORS,SERVES&totype=Restaurant&strict=true' \
	   'Authentication:sk_0tPydJjFUebHd3lD501sag' \
	   'Content-type:application/json'
```


#### API ILE YARATMA

Sinyal ornekleri
```json
[
  {
    "action": "node_create",
    "type": "person",
    "name": "ahmet",
    "properties": {
      "age": 30
    }
  },
  {
    "action": "edge_create",
    "from_type": "person",
    "from_name": "ahmet",
    "name": "BUYS_COFFEE_FROM",
    "from_type": "Coffee Shop",
    "to_name": "Be Coffee"
  }
]
```

Yeni graph yaratalim
```sh
# first_graph.json icinde sinyaller
http POST 'http://localhost:3000/api/v1/graphs' \
'Authentication:sk_0tPydJjFUebHd3lD501sag' \
'Content-type:application/json' < first_graph.json \
--verbose
```

Graph'a yeni sinyaller ekleyelim
```sh
# sinyalleri guncelle
# graph-id ?
# add_more.json icinde sinyaller
http PUT 'http://localhost:3000/api/v1/graphs/36e44c55-728d-4bb8-8911-0ca99f6450f7/add' \
'Authentication:sk_0tPydJjFUebHd3lD501sag' \
'Content-type:application/json' < add_more.json \
--verbose
```

Graph'i adi ve tanimini degistirelim
```sh
# graph-id=36e44c55-728d-4bb8-8911-0ca99f6450f7
# update_graph_name.json icinde sinyaller
http PUT 'http://localhost:3000/api/v1/graphs/36e44c55-728d-4bb8-8911-0ca99f6450f7' \
'Authentication:sk_0tPydJjFUebHd3lD501sag' \
'Content-type:application/json' < update_graph_name.json \
--verbose
```

### Ornek Uygulamalar

#### Linked-in entegrasyonu

> http://52.34.250.205/

#### Slack entegrasyonu

> https://graphcommons.slack.com


#### API Kutuphaneleri

> http://graphcommons.github.io/api-v1/#libraries-amp-examples
