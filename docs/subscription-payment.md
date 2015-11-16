## Paying subscriptions

### 1. Banking billets

```ruby
params = {
  id: 1113
}

var body = {
  payment: {
    banking_billet: {
      expire_at: "2016-12-12",
      customer: {
        name: "Gorbadoc Oldbuck",
        email: "oldbuck@gerencianet.com.br",
        cpf: "04267484171",
        birth: "1977-01-15",
        phone_number: "5144916523"
      }
    }
  }
}

gerencianet = Gerencianet.new(options)
gerencianet.pay_subscription(params: params, body: body)
```

### 2. Credit card

Here it's necessary to use the customer's *credit card* to submit the payment. A `payment_token` represents a credit card, as explained at the end of this page.

```ruby
params = {
  id: 1113
}

body = {
  payment: {
    credit_card: {
      payment_token: "e0c210bb679fea225a586256234f8ce179fd16c5",
      billing_address: {
        street: "Av. JK",
        number: 909,
        neighborhood: "Bauxita",
        zipcode: "35400000",
        city: "Ouro Preto",
        state: "MG"
      },
      customer: {
        name: "Gorbadoc Oldbuck",
        email: "oldbuck@gerencianet.com.br",
        cpf: "04267484171",
        birth: "1977-01-15",
        phone_number: "5144916523"
      }
    }
  }
}

gerencianet = Gerencianet.new(options)
gerencianet.pay_subscription(params: params, body: body)
```

Response:

```js
{
  "code": 200,
  "data": {
    "subscription_id": 11,
    "status": "active",
    "plan": {
      "id": 1000,
      "interval": 2,
      "repeats": null
    },
    "charge": {
      "id": 1053,
      "status": "waiting"
    },
    "total": 1150,
    "payment": "credit_card"
  }
}
```

For getting installment values, including interests, check [Getting Installments](/docs/payment-data.md).

##### Payment tokens

A `payment_token` represents a credit card number at Gerencianet.

For testing purposes, you can go to your application playground in your Gerencianet's account. At the payment endpoint you'll see a button that generates one token for you. This payment token will point to a random test credit card number.

When in production, it will depend if your project is a web app or a mobile app.

For web apps you should follow this [guide](https://api.gerencianet.com.br/checkout/card). It basically consists of copying/pasting a script tag in your checkout page.

For mobile apps you should use this [SDK for Android](https://github.com/gerencianet/gn-api-sdk-android) or this [SDK for iOS](https://github.com/gerencianet/gn-api-sdk-ios).