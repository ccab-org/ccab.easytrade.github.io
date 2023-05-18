# Guia Rápido


## <b>Como autenticar na API do Ellos</b>
As APIs disponibilizadas pela plataforma utilizam o protocolo Bearer Token para realizar a autenticação e autorização de acesso das APIs. Siga os passos abaixo para se autenticar e consumir a API.


<h2>1. Primeiro passo - Solicite o Bearer Token</h2>

Para consultar as APIs, é necessário obter um token de acesso temporário (Bearer). Esse token possui um tempo de validade e sempre que expirado, este passo de requisição de um novo token de acesso deve ser repetido.

<b>Como solicitar o Token de Acesso (Bearer)</b>

Para solicitar o token temporário é necessário realizar uma requisição HTTP POST para o endpoint https://api.hom.ellos.org.br/ellos/associate/api/Associate/login.

Fornecendo o email e a senha, faça a requisição a API.
```

curl -X POST "https://api.hom.ellos.org.br/ellos/associate/api/Associate/login"\
-H "accept: application/json" \
-H "Authorization: Bearer eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21" \

```

No exemplo acima foram utilizados os seguintes parâmetros:

- [HEADER] Accept: application/json
Informamos o tipo de dados que estamos requerendo, nesse caso JSON

- [HEADER] Authorization: Bearer eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21
Informamos o token de acesso recebido

- [POST] https://api.hom.ellos.org.br/ellos/associate/api/Associate/login

Exemplo de requisição esperada:

```
{
    "email": "yourEmail.com"
    "password": "Your Name",
}
```

Exemplo de resposta esperada:

```
{
    {
    "success": true,
    "data": {
        "email": "yourEmail.com",
        "name": "Your Name",
        "token": "eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21lM1wveTNcL1hzPSIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiI0MTBjYTg3My1lY2VjLTQwMTktOTc4ZC04OWQxOTc0OGI2MjYiLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwiaXNzIjoiaHR0cHM6XC9cL2NvZ25pdG8taWRwLnVzLWVhc3QtMS5hbWF6b25hd3MuY29tXC91cy1lYXN0LTFfY1lQTEhwNVQ5IiwiY29nbml0bzp1c2VybmFtZSI6Imxlb25hcmRvY29yZWl4YXNAZ21haWwuY29tIiwiYXVkIjoiMmszazdnMjkxNzZxaTFqZ3F0Ym5oOG1qOWoiLCJldmVudF9pZCI6ImNjZjQ0ZDY5LTBhMjUtNGMxNy05YTgyLWMxNGQxZjYwYjlmZiIsInRva2VuX3VzZSI6ImlkIiwiYXV0aF90aW1lIjoxNjc3NjgyNjQ2LCJuYW1lIjoiTGVvbmFyZG8gQ29yZWl4YXMiLCJleHAiOjE2Nzc2ODYyNDYsImlhdCI6MTY3NzY4MjY0NiwiZW1haWwiOiJsZW9uYXJkb2NvcmVpeGFzQGdtYWlsLmNvbSJ9.QxiY2MjfODXmljDJvK0QhDf6p9kvaBuLI6BRQWA0LocPWOA6Gkdv-mNSYkGWYB1RxlQMQSSQoUz77pPLO_YqEqy5qPjrFhSoItaKf8m3hFKvxTLKa7Q4aiHgwq5Qgn-RagxfHldUe8JxwEfEx94JMMtXKajxNwoTgNIQ1yBtI58ewYQMmmHO0sE0mpr9Yu2fc-0Xl_k9Hk8hjdUqC1h_J9cCgPircYEQAQgPkafE-_oC0nT9tq3MyJZYbqND5INn4pcpkeOVCAKjbUy1GII6WWBB08Vw4QUg-tdu8ISnjOYM62QRt3Z4eOrCPIs3zHEyjOMhfwVpRSgiXYllWwpO1w",
        "profilePicture": null,
        "refreshToken": "bGVvbmFyZG9jb3JlaXhhc0BnbWFpbC5jb20sIENvcmVpeGFzMjkxMiE="
    },
    "errors": null
}
```

<h2>2. Segundo passo - Fazendo uma requisição no sistema Ellos</h2>

De posse do Token de Acesso, faça a requisição a API.
```

curl -X GET "https://api.hom.ellos.org.br/ellos/easytrade-exportation/api/Exportation/details/145292508cc6c1b4347fe05cdc4a36bc98025cec532a8e5c24fe46de057c2b56"\
-H "accept: application/json" \
-H "Authorization: Bearer eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21" \

```

No exemplo acima foram utilizados os seguintes parâmetros:

- [HEADER] Accept: application/json
Informamos o tipo de dados que estamos requerendo, nesse caso JSON

- [HEADER] Authorization: Bearer eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21
Informamos o token de acesso recebido

- [GET] https://api.hom.ellos.org.br/ellos/easytrade-exportation/api/Exportation/details/145292508cc6c1b4347fe05cdc4a36bc98025cec532a8e5c24fe46de057c2b56

Chamamos a url da API e o método desejado. No caso, a url base é
 "https://api.hom.ellos.org.br/ellos/easytrade/api/”, e o método é o 
 "Exportation/details/145292508cc6c1b4347fe05cdc4a36bc98025cec532a8e5c24fe46de057c2b56".

 Exemplo de resposta esperada:

```
{
    "success": true,
    "data": {
        "exportation": {
            "id": "145292508cc6c1b4347fe05cdc4a36bc98025cec532a8e5c24fe46de057c2b56",
            "idReference": "75D09A6D507DD4DA509DF34F671608B4",
            "date": "2023-03-02T13:36:16.936Z",
            "status": "PENDING_CERTIFIERS",
            "rejectMessage": null,
            "consularApproval": false,
            "physicalSealing": false,
            "processStatus": null
        },
        "incoterm": {
            "incotermType": "CIF",
            "cost": 600000.0,
            "freightCost": 600000.0,
            "insurance": 600000.0,
            "landingFee": 600000.0,
            "others": 6000000.0,
            "processStatus": null
        },
        "exporter": {
            "idEllos": 1,
            "name": "BRF Foods LTDA",
            "city": "SÃO PAULO ",
            "state": "SP",
            "address": "AV. PAULISTA 3",
            "complement": "Em frente ao MASP",
            "zipCode": "01311-000",
            "poBox": "po-box134",
            "district": "CERQUEIRA CESAR 2",
            "processStatus": null
        },
        "importer": {
            "idEllos": 1018,
            "name": "Mark Fish Foods",
            "city": "MAHAR",
            "state": "",
            "address": "SIR TAKOL MIJAR, 154",
            "complement": "District JORONH",
            "zipCode": "",
            "poBox": "16451",
            "district": "",
            "processStatus": null
        },
        "buyer": {
            "idEllos": 1018,
            "name": "Mark Fish Foods",
            "city": "MAHAR",
            "state": "",
            "address": "SIR TAKOL MIJAR, 154",
            "complement": "District JORONH",
            "zipCode": "",
            "poBox": "16451",
            "district": "",
            "processStatus": null
        },
        "consignee": {
            "idEllos": 1018,
            "name": "Mark Fish Foods",
            "city": "MAHAR",
            "state": "",
            "address": "SIR TAKOL MIJAR, 154",
            "complement": "District JORONH",
            "zipCode": "",
            "poBox": "16451",
            "district": "",
            "processStatus": null
        },
        "shipment": {
            "shipmentType": "PLANE",
            "blAwb": "15151515",
            "shipmentDate": "2023-03-02T03:00:00+00:00",
            "imo": 0.0,
            "processStatus": null
        },
        "products": [
            {
                "ncm": {
                    "id": 81,
                    "ncmCode": "02032900",
                    "description": "Other swine meat, frozen"
                },
                "unitMeasure": {
                    "id": 12,
                    "code": "BAL",
                    "description": "Bales"
                },
                "unitMeasureWeight": {
                    "id": 39,
                    "code": "MT",
                    "description": "Metric Tonne"
                },
                "quantity": 151515151,
                "grossWeight": 151515.1515,
                "netWeight": 15.1515,
                "marksAndNumbers": "",
                "sif": 15151515.0,
                "manufactoringDate": "2023-03-02T03:00:00.000Z",
                "expirationDate": "2023-03-31T03:00:00.000Z",
                "description": "Other swine meat, frozen",
                "productValue": 15151515.15,
                "processStatus": null
            }
        ],
        "stopPoints": [
            {
                "id": 1,
                "code": "ATL",
                "name": "Hartsfield Jackson Atlanta Intl",
                "processStatus": null
            },
            {
                "id": 2,
                "code": "ORD",
                "name": "Chicago Ohare Intl",
                "processStatus": null
            }
        ],
        "invoice": {
            "idInvoice": "15478858",
            "totalWeight": 55555.5555,
            "totalValue": 55555.55,
            "emissionDate": "2023-03-02T03:00:00+00:00",
            "destinationCountryCode": "JOR",
            "originCountryCode": "BRA",
            "certifiedLanguage": "2",
            "email": "teste@teste.com.br",
            "comments": "teste",
            "processStatus": null,
            "numberOfCopies": {
                "consularApproval": 0,
                "physicalSealing": 1,
                "processStatus": null
            },
            "numberOfPages": 1
        },
        "certificates": [
            {
                "id": 1,
                "number": "",
                "uid": "68e30c2e-14c3-488f-89f4-ac0cf1c574c0",
                "rejectMessage": null,
                "name": "Health Certificate",
                "code": "health",
                "filePath": "https://ellos-exportation-docs.s3.amazonaws.com/75D09A6D507DD4DA509DF34F671608B4/cert_health_15478858_v1.pdf",
                "status": "PENDING",
                "numberOfCopies": {
                    "consularApproval": 0,
                    "physicalSealing": 1,
                    "processStatus": null
                },
                "certifier": null,
                "certificateNeedsConsularApproval": false,
                "numberOfPages": 1
            },
            {
                "id": 3,
                "number": "15478858",
                "uid": "b852d839-deef-4c20-9f1e-e5fcdd2fde6d",
                "rejectMessage": null,
                "name": "Origin Certificate",
                "code": "origin",
                "filePath": "https://ellos-exportation-docs.s3.amazonaws.com/75D09A6D507DD4DA509DF34F671608B4/cert_origin_15478858_v1.pdf",
                "status": "PENDING",
                "numberOfCopies": {
                    "consularApproval": 0,
                    "physicalSealing": 1,
                    "processStatus": null
                },
                "certifier": null,
                "certificateNeedsConsularApproval": false,
                "numberOfPages": 1
            },
            {
                "id": 5,
                "number": "",
                "uid": "07067293-88d0-4cfb-b3ad-fbed5dfff22e",
                "rejectMessage": null,
                "name": "Proforma Invoice",
                "code": "proformaInvoice",
                "filePath": "https://ellos-exportation-docs.s3.amazonaws.com/75D09A6D507DD4DA509DF34F671608B4/cert_proformaInvoice_15478858_v1.pdf",
                "status": "PENDING",
                "numberOfCopies": {
                    "consularApproval": 0,
                    "physicalSealing": 1,
                    "processStatus": null
                },
                "certifier": null,
                "certificateNeedsConsularApproval": false,
                "numberOfPages": 1
            },
            {
                "id": 6,
                "number": "",
                "uid": "64f06c97-cb6d-4fee-888a-4368dfb38657",
                "rejectMessage": null,
                "name": "Packing List",
                "code": "packingList",
                "filePath": "https://ellos-exportation-docs.s3.amazonaws.com/75D09A6D507DD4DA509DF34F671608B4/cert_packingList_15478858_v1.pdf",
                "status": "PENDING",
                "numberOfCopies": {
                    "consularApproval": 0,
                    "physicalSealing": 1,
                    "processStatus": null
                },
                "certifier": null,
                "certificateNeedsConsularApproval": false,
                "numberOfPages": 1
            }
        ],
        "documents": [],
        "stampedDoc": null,
        "payment": {
            "totalValue": 1600.0,
            "valueDetails": [
                {
                    "name": "Despacho Easytrade",
                    "value": 1600.0
                }
            ],
            "paymentStatus": "REGISTRED",
            "processStatus": null
        },
        "embassyPayment": null,
        "consularApproval": false,
        "needsPhysicalSealing": false,
        "processStatus": null
    },
    "errors": null
}
```

