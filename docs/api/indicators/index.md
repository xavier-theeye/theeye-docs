# API for Indicators

[![theeye.io](../../images/logo-theeye-theOeye-logo2.png)](https://theeye.io/en/index.html)

## API URL for Indicators

URL: `https://supervisor.theeye.io/indicator?access_token={token}&customer={organization_name}`


## Examples

#### [GET All indicators from an organization](#get)

Method: `GET`

URL: `https://supervisor.theeye.io/indicator?access_token={token}&customer={organization_name}`

*Request*
```bash
customer="customer"
token="integrationToken"

curl -X GET 'https://supervisor.theeye.io/indicator?access_token={token}&customer={organization_name}'
```

#### [Create an Indicator](#create)

Method: `POST`

Properties: `title (required, unique), type (required), state, value, acl`

Check the following example, used to create the text indicator shown at the begining of this page.

*Request*
```bash
customer="customer"
token="integrationToken"

curl -X POST 'https://supervisor.theeye.io/indicator?access_token={token}&customer={organization_name}' --header 'Content-Type: application/json' --data '{"title":"Currency Exchange
Dollar/Peso","state":"normal","type":"text","value":"37.56","acl":["example_user_email@theeye.io"]}'
```

The request response will look like this, where customer\_id, customer\_name, user\_id and id values were replaced for security reasons:

*Response*
```json
{
   "enable":true,
   "acl":[
      "example_user_email@theeye.io"
   ],
   "severity":"HIGH",
   "alerts":true,
   "state":"normal",
   "sticky":false,
   "value":"37.56",
   "type":"text",
   "_type":"TextIndicator",
   "title":"Currency Exchange Dollar/Peso",
   "customer_id":"AAA",
   "customer_name":"BBB",
   "user_id":"CCC",
   "creation_date":"2018-10-22T23:10:31.912Z",
   "last_update":"2018-10-22T23:10:31.915Z",
   "id":"{indicator_id}"
}
```


#### [Update an Indicator by ID](#update)

Method: `PATCH`

Properties: `title, state, value`

URL: `https://supervisor.theeye.io/indicator/{indicator_id}`

Check the following example, used to update the text indicator value shown at the begining of this page.

*Request*
```bash
curl -X PATCH 'https://supervisor.theeye.io/indicator/{indicator_id}?access_token={token}&customer={organization_name}' --header 'Content-Type: application/json' --data '{"value":"39.99"}'
```

The request response will look like this, where customer\_id, customer\_name, user\_id and id values were replaced for security reasons:

*Response*
```json
{
   "enable":true,
   "acl":[

   ],
   "severity":"HIGH",
   "alerts":true,
   "state":"normal",
   "sticky":false,
   "value":"39.96",
   "type":"text",
   "_type":"TextIndicator",
   "creation_date":"2018-10-22T23:10:31.912Z",
   "last_update":"2018-10-22T23:48:07.515Z",
   "title":"Exchange Dollar/Peso",
   "customer_id":"AAA",
   "customer_name":"BBB",
   "user_id":"CCC",
   "id":"{indicator_id}"
}
```


#### 

#### [Update an Indicator by Title](#updateByTitle)

Method: `PATCH`

Properties: `title, state, value`

URL: `https://supervisor.theeye.io/indicator/title/{urlencoded_title}`

Check the following example, used to update the text indicator value shown at the begining of this page.

*Request*
```
curl -X PATCH 'https://supervisor.theeye.io/indicator/title/Currency%20Exchange Dollar%2fPeso?access_token={token}&customer={organization_name}' --header 'Content-Type: application/json' --data '{"value":"34"}'
```


**Update a Counter Indicator**

Method: ****`PATCH`

Actions: `increase, decrease, restart`

URL: `https://supervisor.theeye.io/indicator/{indicator_id}/[action]`

Check the following example, used to increase the value of a counter indicator.

*Request*
```bash
curl -X PATCH 'https://supervisor.theeye.io/indicator/{indicator_id}/increase?access_token={TOKEN}&customer={organization_name}'
```

#### More Examples

Please, check out the indicators recipe example. After importing It, fulfill the api-key and then run it, It covers the most common requirements.

Check the [Recipes Documentation](/assets/recipes/) for more details.
