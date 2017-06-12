# integracao-stone-nodejs
Exemplo de Integração via NodeJS com a Stone Pagamentos

## Requisição JSON Básica para Autorização com Cartão de Crédito
```javascript
var transacao = {
      "BoletoTransactionCollection": null,
      "Buyer": null,
      "CreditCardTransactionCollection": [
        {
          "AmountInCents": 0,
          "CreditCard": {
            "BillingAddress": null,
            "CreditCardBrand": "Visa",
            "CreditCardNumber": 1234123412341234,
            "ExpMonth": 10,
            "ExpYear": 2018,
            "HolderName": 'LUKE SKYWALKER',
            "SecurityCode": 123
            },
          "CreditCardOperation": "AuthAndCapture",
          "InstallmentCount": 0,
          "Options": {
            "CurrencyIso": "BRL",
            "PaymentMethodCode": 1,
            "SoftDescriptorText": "DESCRIÇÃO DO COBRADOR"
          },
          "Recurrency": null,
          "TransactionDateInMerchant": null,
          "TransactionReference": null
        }
      ],
      "Merchant": null,
      "Options": null,
      "Order": {"OrderReference": "Numero Do Pedido"},
      "RequestData": null,
      "RequestKey": "00000000-0000-0000-0000-000000000000",
      "ShoppingCartCollection": null
    };
```

## Fetch Padrão das Requisições
```javascript
    fetch('https://transaction.stone.com.br/Sale', {
      headers: {
        'MerchantKey' : 'F2A1F485-CFD4-49F5-8862-0EBC438AE923',
        'Content-Type' : 'application/json',
        'Accept' : 'application/json'
      },
      mode: 'cors',
      redirect: 'follow',
      method: 'POST',
      body: JSON.stringify(transacao),
    }).then((result) => {
      console.log(result.json());
    });
```
