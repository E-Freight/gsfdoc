### AES API

#1. Get API Token

```curl

curl -X POST \
  http://edi.gsf24.com/token \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'grant_type=password&username=test.test1&client_id=test&client_secret=12345&group_code=TEST&branch_code=LAX'

  ```
HttpResponse
```json

 {
    "access_token": "RhGaue4k4du-IJzE3PQ7FqTdQcbXYMiQMmts6SqU1gzL4SrXv_3PhEFXfQ2PHeiv5ECvP1B0QgJ_nFUeqzCyq4n48CBCMksJJkGweFJONqVUEF7JtqAjOu-9FkRR_1IzN0WQ-seCs8ZoJKemeOWNIu5WxOAfjDSWParGRu0plVcKnxkSE1AGZCQ9FrTZ8Q6Difsi9vWOBSwQJG4APw4uC-vQkP7OLjAPp54haXyP5ObdgqowpyDKiFjKGFfnsvN9et3E2RjPCE4pTnQOosi6blxNrYbQlU8X4bKCMDDnBFQ",
    "token_type": "bearer",
    "expires_in": 86399
}
  ```
|Description||
|--|--|
|  URL|http://edi.gsf24.com/token  |
|  Method|Post  |
|Headers| grant_type = password |
|| client_id = [SoftwareVendor]|
|| client_secret = [AppKey]|
|| group_code = [GroupCode] |
|| branch_code = [BranchCode] |
|| username = [SubmitBy] |

#2. Post XML To AES

  ```curl

  curl -X POST \
  http://edi.gsf24.com/api/openapi/xmltogsf \
  -H 'Authorization: bearer Grua8Hj5h1Nnhbnp0tsr3PuRyRM0XVvRje3OvoDTZvbPo21u2K6G3B0zkU7OegTVN3joQGfiRvPdqEweO7CO-AsdfE0bErFnuEaq8CCNtJ-HAVkGlXt4AK6wf7zXUt_S9d5hYNnDD_Vus7nq78kkJp_tcLwTIErZa5ktX16rl-uBqvuDTxNXWSDLnti-q60IJZF30j9s3BXbPYAf_WEpUbYXEQETIkW3CblQdkb71BHe-_PpxT72Elxfzs3fMOx7rCPr55kBn6uFaH-zDHZXAfYmEvLif-nziidsWTb8g9c' \
  -H 'Content-Type: application/xml' \

 ```
HttpResponse Success

```json

{
"Status":true,
"ErrorMsg":"",
"Data":null
}
  ```

HttpResponse Error

```json

{
"Status":false,
"ErrorMsg":"[U.H.F.C.COMPANY] => Party ID Type is invalid ; Party ID (EIN) is required",
"Data":null
}
  ```

|Description||
|--|--|
|  URL|http://edi.gsf24.com/api/openapi/xmltogsf  |
|  Method|Post  |
|Headers| Authorization|
|Boby| Xml Content |

#3. Get ITN Number From AES

  ```curl
curl -X GET \
  'http://aestest.gsf24.com/api/aes/getitn?shipmentref=SHAOE002690' \
  -H 'Authorization: bearer RhGaue4k4du-IJzE3PQ7FqTdQcbXYMiQMmts6SqU1gzL4SrXv_3PhEFXfQ2PHeiv5ECvP1B0QgJ_nFUeqzCyq4n48CBCMksJJkGweFJONqVUEF7JtqAjOu-9FkRR_1IzN0WQ-seCs8ZoJKemeOWNIu5WxOAfjDSWParGRu0plVcKnxkSE1AGZCQ9FrTZ8Q6Difsi9vWOBSwQJG4APw4uC-vQkP7OLjAPp54haXyP5ObdgqowpyDKiFjKGFfnsvN9et3E2RjPCE4pTnQOosi6blxNrYbQlU8X4bKCMDDnBFQ' \
  -H 'Content-Type: application/xml' \
   ```
HttpResponse Success

```json

{
    "Status": true,
    "ErrorMsg": null,
    "Data": "X20190419368617"
}
  ```
|Description||
|--|--|
|  URL|http://aestest.gsf24.com/api/aes/getitn  |
|  Method|Get  |
|Headers| Authorization|
|Params| ShipmentRef |

#4. Show AES Status

http://aes.gsf24.com/aesstatus.aspx?customercode=test&hbl=SHAOE002690

|Description||
|--|--|
|  URL|http://aes.gsf24.com/aesstatus.aspx  |
|  Method|Get  |
|Params| customercode |
|| hbl|