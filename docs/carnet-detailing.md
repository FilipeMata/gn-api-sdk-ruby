## Detailing carnets

In order to retrieve carnets, just provide the id:

```ruby
params = {
  id: 1000
}

gerencianet = Gerencianet.new(options)
puts gerencianet.detail_carnet(params: params)
```

The response you'll receive contains all the information about the carnet:

```ruby
{
  "code": 200,
  "data": {
    "carnet_id": 6,
    "status": "active",
    "repeats": 4,
    "cover": "https://visualizacao.gerencianet.com.br/emissao/28333_2385_ZEMAL5/A5CC-28333-61428-LEENA9/28333-61428-LEENA9",
    "value": 4000,
    "split_items": false,
    "charges": [{
        "charge_id": 357,
        "parcel": "1",
        "status": "waiting",
        "value": 2000,
        "expire_at": '2015-06-01',
        "url": "https://visualizacao.gerencianet.com.br/emissao/28333_2385_ZEMAL5/A5CL-28333-61428-LEENA9/28333-61428-LEENA9",
        "barcode": "00190.00009 01523.894002 00061.428181 1 64780000002000"
      }, {
        "charge_id": 358,
        "parcel": "2",
        "status": "waiting",
        "value": 2000,
        "expire_at": '2015-07-01',
        "url": "https://visualizacao.gerencianet.com.br/emissao/28333_2385_ZEMAL5/A5CL-28333-61428-LEENA9/28333-61429-CORZE4",
        "barcode": "00190.00009 01523.894002 00061.428181 8 65090000002000"
      }, {
        "charge_id": 359,
        "parcel": "3",
        "status": "waiting",
        "value": 2000,
        "expire_at": '2015-08-01',
        "url": "https://visualizacao.gerencianet.com.br/emissao/28333_2385_ZEMAL5/A5CL-28333-61428-LEENA9/28333-61430-HIRRA4",
        "barcode": "00190.00009 01523.894002 00061.428181 7 65400000002000"
      }, {
        "charge_id": 360,
        "parcel": "4",
        "status": "waiting",
        "value": 2000,
        "expire_at": '2015-09-01',
        "url": "https://visualizacao.gerencianet.com.br/emissao/28333_2385_ZEMAL5/A5CL-28333-61428-LEENA9/28333-61431-HIRRA4",
        "barcode": "00190.00009 01523.894002 00061.428181 5 65400000002000"
      }
    ]
  }
}
