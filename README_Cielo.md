[checkmark]: https://raw.githubusercontent.com/mozgbrasil/mozgbrasil.github.io/master/assets/images/logos/logo_32_32.png "MOZG"
![valid XHTML][checkmark]

# Mozg\Cielo

## Cielo API 3.0 - https://developercielo.github.io/Webservice-3.0/

-

Abaixo temos uma requisição de transação

-

curl --request POST https://apisandbox.cieloecommerce.cielo.com.br/1/sales/ --header 'Content-Type: application/json' --header 'MerchantId: a2133427-a0f8-4fe8-b605-6469161e7711' --header 'MerchantKey: XUMUBMGQBPNUAYIESMSHTCNLVTNEXIDPHXQRZYOC' --header 'RequestId: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' --data '{
   "MerchantOrderId":"145000484",
   "Customer":{
      "Name":"Eula Jackson",
      "Email":"mailer@mozg.com.br",
      "Birthdate":"1987-03-25",
      "Address":{
         "Street":"Avenida Córrego do Jacuu",
         "Number":"12",
         "Complement":"ap. 23 B",
         "ZipCode":"08215-070",
         "District":"Itaquera",
         "City":"São Paulo",
         "State":"CE",
         "Country":"BR"
      },
      "DeliveryAddress":{
         "Street":"Avenida Córrego do Jacuu",
         "Number":"12",
         "Complement":"ap. 23 B",
         "ZipCode":"08215-070",
         "District":"Itaquera",
         "City":"São Paulo",
         "State":"CE",
         "Country":"BR"
      },
      "Identity":"25739569000102",
      "IdentityType":"CNPJ"
   },
   "Payment":{
      "Type":"CreditCard",
      "Amount":"12084",
      "Currency":"BRL",
      "Country":"BRA",
      "Provider":"Simulado",
      "ServiceTaxAmount":"0",
      "Installments":"1",
      "Interest":"ByMerchant",
      "Capture":"false",
      "Authenticate":"false",
      "ReturnUrl":"https://apisandbox.cielo.com.br/v2/sales/",
      "CreditCard":{
         "CardNumber":"4111111111111111",
         "Holder":"Mike Miers",
         "ExpirationDate":"08/2018",
         "SecurityCode":"123",
         "Brand":"Visa",
         "SaveCard":false
      },
      "FraudAnalysis":""
   }
}' --verbose

-

Foi retornado

-

{"MerchantOrderId":"145000484","Customer":{"Name":"Eula Jackson","Identity":"25739569000102","IdentityType":"CNPJ","Email":"mailer@mozg.com.br","Birthdate":"1987-03-25","Address":{"Street":"Avenida Córrego do Jacuu","Number":"12","Complement":"ap. 23 B","ZipCode":"08215-070","City":"São Paulo","State":"CE","Country":"BR","District":"Itaquera"},"DeliveryAddress":{"Street":"Avenida Córrego do Jacuu","Number":"12","Complement":"ap. 23 B","ZipCode":"08215-070","City":"São Paulo","State":"CE","Country":"BR","District":"Itaquera"}},"Payment":{"ServiceTaxAmount":0,"Installments":1,"Interest":0,"Capture":false,"Authenticate":false,"Recurrent":false,"CreditCard":{"CardNumber":"411111******1111","Holder":"Mike Miers","ExpirationDate":"08/2018","SaveCard":false,"Brand":"Visa"},"Tid":"0413034426394","ProofOfSale":"4426394","AuthorizationCode":"561816","ReturnUrl":"https://apisandbox.cielo.com.br/v2/sales/","Provider":"Simulado","PaymentId":"19587687-6dac-4bd8-a186-3b4c46dfe04d","Type":"CreditCard","Amount":12084,"Rec* Closing connection 0
eivedDate":"2017-04-13 15:44:26","Currency":"BRL","Country":"BRA","ReturnCode":"4","ReturnMessage":"Operation Successful","Status":1,"Links":[{"Method":"GET","Rel":"self","Href":"https://apiquerysandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d"},{"Method":"PUT","Rel":"capture","Href":"https://apisandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d/capture"},{"Method":"PUT","Rel":"void","Href":"https://apisandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d/void"}]}}

-

Vemos no retorno o ""Status":1"

Na URL a seguir é esclarecido sobre o status da transação

https://developercielo.github.io/Webservice-3.0/?shell#status---status-de-uma-transação

-

Abaixo temos uma consulta da transação

-

curl --request GET https://apiquerysandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d --header 'Content-Type: application/json' --header 'MerchantId: a2133427-a0f8-4fe8-b605-6469161e7711' --header 'MerchantKey: XUMUBMGQBPNUAYIESMSHTCNLVTNEXIDPHXQRZYOC' --header 'RequestId: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' --verbose

-

Foi retornado

-

{"MerchantOrderId":"145000484","Customer":{"Name":"Eula Jackson","Identity":"25739569000102","Email":"mailer@mozg.com.br","Birthdate":"1987-03-25","Address":{"Street":"Avenida Córrego do Jacuu","Number":"12","Complement":"ap. 23 B","ZipCode":"08215-070","City":"São Paulo","State":"CE","Country":"BR","District":"Itaquera"}},"Payment":{"ServiceTaxAmount":0,"Installments":1,"Interest":"ByMerchant","Capture":false,"Authenticate":false,"CreditCard":{"CardNumber":"411111******1111","Holder":"Mike Miers","ExpirationDate":"08/2018","Brand":"Visa"},"ProofOfSale":"4426394","Tid":"0413034426394","AuthorizationCode":"561816","PaymentId":"19587687-6dac-4bd8-a186-3b4c46dfe04d","Type":"CreditCard","Amount":12084,"ReceivedDate":"2017-04-13 15:44:26","Currency":"BRL","Country":"BRA","Provider":"Simulado","Status":1,"Links":[{"Method":"GET","Rel":"self","Href":"https://apiquerysandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d"},{"Method":"PUT","Rel":"capture","Href":"https://apisandbox.cieloeco* Closing connection 0
mmerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d/capture"},{"Method":"PUT","Rel":"void","Href":"https://apisandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d/void"}]}}

-

Abaixo temos uma requisição de captura

-

curl --request PUT https://apisandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d/capture -d '{"amount":"12084","serviceTaxAmount":"0"}' --header 'Content-Type: application/json' --header 'MerchantId: a2133427-a0f8-4fe8-b605-6469161e7711' --header 'MerchantKey: XUMUBMGQBPNUAYIESMSHTCNLVTNEXIDPHXQRZYOC' --header 'RequestId: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' --verbose

-

Foi retornado

-

{"Status":2,"ReasonCode":0,"ReasonMessage":"Successful","ProviderReturnCode":"6","ProviderReturnMessage":"Operation Successful","ReturnCode":"6","ReturnMessage":"Operation Successful","Links":[{"Method":"GET","Rel":"self","Href":"https://apiquerysandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d"},{"Method":"PUT","Rel":"void","Href":"https://apisandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d/void"}]}

-

Abaixo temos novamente a consulta da transação

-

curl --request GET https://apiquerysandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d --header 'Content-Type: application/json' --header 'MerchantId: a2133427-a0f8-4fe8-b605-6469161e7711' --header 'MerchantKey: XUMUBMGQBPNUAYIESMSHTCNLVTNEXIDPHXQRZYOC' --header 'RequestId: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' --verbose

-

Foi retornado

-

{"MerchantOrderId":"145000484","Customer":{"Name":"Eula Jackson","Identity":"25739569000102","Email":"mailer@mozg.com.br","Birthdate":"1987-03-25","Address":{"Street":"Avenida Córrego do Jacuu","Number":"12","Complement":"ap. 23 B","ZipCode":"08215-070","City":"São Paulo","State":"CE","Country":"BR","District":"Itaquera"}},"Payment":{"ServiceTaxAmount":0,"Installments":1,"Interest":"ByMerchant","Capture":false,"Authenticate":false,"CreditCard":{"CardNumber":"411111******1111","Holder":"Mike Miers","ExpirationDate":"08/2018","Brand":"Visa"},"ProofOfSale":"4915486","Tid":"0413034426394","AuthorizationCode":"20170413034915486","PaymentId":"19587687-6dac-4bd8-a186-3b4c46dfe04d","Type":"CreditCard","Amount":12084,"ReceivedDate":"2017-04-13 15:44:26","CapturedAmount":12084,"CapturedDate":"2017-04-13 15:49:15","Currency":"BRL","Country":"BRA","Provider":"Simulado","Status":2,"Links":[{"Method":"GET","Rel":"self","Href":"https://apiquerysandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04* Closing connection 0
d"},{"Method":"PUT","Rel":"void","Href":"https://apisandbox.cieloecommerce.cielo.com.br/1/sales/19587687-6dac-4bd8-a186-3b4c46dfe04d/void"}]}}

-

Nesse caso vemos que após a captura foi retornado o devido status "Status":2" que equivale e pagamento confirmado

-