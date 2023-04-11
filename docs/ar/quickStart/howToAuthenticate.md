# مرشد سريع


## <b>كيفية المصادقة على Ellos API</b>
تستخدم واجهات برمجة التطبيقات التي توفرها المنصة بروتوكول Bearer Token للمصادقة وتفويض الوصول إلى واجهات برمجة التطبيقات. اتبع الخطوات أدناه لمصادقة واستخدام واجهة برمجة التطبيقات.


<h2>1. الخطوة الأولى - المطالبة بالرمز الحامل</h2>

للاستعلام عن واجهات برمجة التطبيقات ، تحتاج إلى الحصول على رمز وصول مؤقت (Bearer). هذا الرمز المميز له وقت انتهاء صلاحية ، وعندما تنتهي صلاحيته ، يجب تكرار هذه الخطوة لطلب رمز وصول جديد.

<b>كيفية طلب رمز الوصول (الحامل)</b>

لطلب الرمز المميز المؤقت ، من الضروري تقديم طلب HTTP POST إلى نقطة النهاية https://api.dev.casaarabe.org.br/ellos/associate/api/Associate/login.

تقديم البريد الإلكتروني وكلمة المرور ، قم بتقديم الطلب إلى API.
```

curl -X POST "https://api.dev.casaarabe.org.br/ellos/associate/api/Associate/login"\
-H "accept: application/json" \
-H "Authorization: Bearer eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21" \

```

في المثال أعلاه ، تم استخدام المعلمات التالية:

- [HEADER] يقبل: application/json
نبلغ عن نوع البيانات التي نطلبها ، في هذه الحالة JSON

- [HEADER] تفويض: Bearer eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21
نبلغ رمز الوصول المستلم

- [POST] https://api.dev.casaarabe.org.br/ellos/associate/api/Associate/login

مثال على الطلب المتوقع:

```
{
    "email": "yourEmail.com"
    "password": "Your Name",
}
```

مثال على الاستجابة المتوقعة:

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

<h2>2. الخطوة الثانية - تقديم طلب في نظام Ellos</h2>

في حالة امتلاك رمز الوصول ، قم بتقديم الطلب إلى واجهة برمجة التطبيقات.
```

curl -X GET "https://api.dev.casaarabe.org.br/ellos/easytrade-customs/api/Exportation/details"\
-H "accept: application/json" \
-H "Authorization: Bearer eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21" \

```

في المثال أعلاه ، تم استخدام المعلمات التالية:

- [HEADER] يقبل: application/json
Informamos o tipo de dados que estamos requerendo, nesse caso JSON

- [HEADER] تفويض: Bearer eyJraWQiOiI4aTV5cndFMVlreGc4M0FWXC9MTWFacHk0b0J0TEJ6a01yN21
Informamos o token de acesso recebido

- [GET] https://api.dev.casaarabe.org.br/ellos/easytrade-customs/api/Exportation/details

نحن نسمي عنوان url الخاص بواجهة برمجة التطبيقات (API) والطريقة المطلوبة. في هذه الحالة ، عنوان url الأساسي هو
 "https://api.dev.casaarabe.org.br/ellos/easytrade-customs/api/”, والطريقة هي
 "Exportation/details?idCompany=147&idExportation=edb65905c98da3cd5f55d0c251ec582254ecd353a0a257aec2b33e6f384b5b28".

 مثال على الاستجابة المتوقعة:

```
{
"success": true,
"data": {
"exportation": {
    "id": "edb65905c98da3cd5f55d0c251ec582254ecd353a0a257aec2b33e6f384b5b28",
    "date": "2023-02-23T23:52:17.207Z",
    "status": "ACCEPTED",
    "rejectMessage": null
},
"incoterm": {
    "incotermType": "CIF",
    "cost": 255.55,
    "freightCost": 5555.5,
    "insurance": 555.5,
    "landingFee": 555550,
    "others": 55550
},
"exporter": {
    "idEllos": 433,
    "name": "Denilson OP",
    "city": "Rio de janeiro",
    "state": "RJ",
    "address": "Av. Rio Branco",
    "complement": "Em frente ao MASP",
    "zipCode": "20090-000",
    "poBox": "po-box134",
    "district": "Barra da Tijuca"
},
"importer": {
    "idEllos": 2030,
    "name": "Teste task 1551",
    "city": "teste",
    "state": "",
    "address": "rua do teste",
    "complement": "teste",
    "zipCode": "",
    "poBox": "101010",
    "district": ""
},
"buyer": {
    "idEllos": 2030,
    "name": "Teste task 1551",
    "city": "teste",
    "state": "",
    "address": "rua do teste",
    "complement": "teste",
    "zipCode": "",
    "poBox": "101010",
    "district": ""
},
"consignee": {
    "idEllos": 2030,
    "name": "Teste task 1551",
    "city": "teste",
    "state": "",
    "address": "rua do teste",
    "complement": "teste",
    "zipCode": "",
    "poBox": "101010",
    "district": ""
},
"shipment": {
    "shipmentType": "PLANE",
    "blAwb": "3434",
    "shipmentDate": "2023-02-09T00:00:00-03:00",
    "imo": 3434
},
"products": [
    {
    "ncm": {
        "id": 13711,
        "ncmCode": "97051000",
        "description": "Collections and collection pieces that present an archaeological, ethnographic or historical interest"
    },
    "unitMeasure": {
        "id": 12,
        "code": "BAL",
        "description": "Bales"
    },
    "unitMeasureWeight": null,
    "quantity": 34343,
    "grossWeight": 34.3434,
    "netWeight": 34.3434,
    "marksAndNumbers": "343434",
    "sif": 3434,
    "manufactoringDate": "2023-02-09T03:00:00.000Z",
    "expirationDate": "2023-02-22T03:00:00.000Z",
    "description": "Collections and collection pieces that present an archaeological, ethnographic or historical interest"
    }
],
"stopPoints": [
    {
    "code": "PEK",
    "name": "Capital Intl"
    },
    {
    "code": "LAX",
    "name": "Los Angeles Intl"
    }
],
"invoice": {
    "idInvoice": "645645",
    "totalWeight": 23.2323,
    "totalValue": 54544.54,
    "emissionDate": "2021-10-29T00:00:00-03:00",
    "destinationCountryCode": "JOR",
    "originCountryCode": "BRA",
    "certifiedLanguage": "2",
    "email": "esae@ese.v",
    "comments": "kijij"
},
"certificates": [],
"stampedDoc": null
},
"errors": null
}
```

