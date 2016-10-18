---
title: DocIt API Reference

language_tabs:
  - json


includes:
  - errors

search: true
---

# Introduction

Welcome to the DocIt API. You can use this API to access DocIt API endpoints, which can get information on various students, teachers, documents, and notes in the database.

Each endpoint is mapped out with parameters available for each request. You can view request and response examples in the dark area to the right.


# Authentication

> To authorize, use this code:



```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization": "Token token=bce6d3ccf35424628ec997e4ff199437"
```

> Make sure to replace `bce6d3ccf35424628ec997e4ff199437` with your API key.

DocIT uses API keys to allow access to the API. 

DocIT expects for the API key to be included in all API requests to the server in a header that looks like the following:

`"Authorization": "Token token=bce6d3ccf35424628ec997e4ff199437"`

<aside class="notice">
You must replace <code>bce6d3ccf35424628ec997e4ff199437</code> with your personal API key.
</aside>

## Login

> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/login",
  "request_body": "user[license_name]=dolorem2&user[username]=teacher20&user[password]=Password1",
  "request_headers": {
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"auth_token\":\"bce6d3ccf35424628ec997e4ff199437\",\"first_name\":\"Rosalee\",\"last_name\":\"Leannon\",\"has_accepted_eula\":false,\"type\":\"Teacher\",\"language_code\":\"en\"}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"9144e34eb434ebb745c6bfac5ffe16bf\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "94b4eb0d-5300-4b84-8377-162480dd958a",
    "X-Runtime": "0.102852",
    "Content-Length": "158"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```

The login with DocIT authorization endpoint validates the authorization/authentication request and responds with the user's API key to use in further signed requests.


### HTTP Request

`POST /api/v2/login`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
license_name | true | string
username | true | string
password | true | string


## Logout

> Example request & response:

```json
{
  "request_method": "DELETE",
  "request_path": "/api/v2/logout",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=bce6d3ccf35424628ec997e4ff199437",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 204,
  "response_status_text": "No Content",
  "response_body": null,
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Cache-Control": "no-cache",
    "X-Request-Id": "95ab9bf3-9ba9-4edc-8e01-c7df02642004",
    "X-Runtime": "0.040197"
  },
  "response_content_type": null,
  "curl": null
}
```

Logout of the current user session.


### HTTP Request

`DELETE /api/v2/logout`




# Assessments


## Create a New Group Assessment

> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/assessments/bulk-set",
  "request_body": "assessment[strand_id]=21&assessment[document_id]=7&assessment[is_group]=true",
  "request_headers": {
    "Authorization": "Token token=9a4b6aecc78dd1f8411e8225b1e2501e",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": " ",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json",
    "ETag": "\"7215ee9c7d9dc229d2921a40e899ec5f\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "8de35d20-8444-4f59-8ea2-25a2b1edaec1",
    "X-Runtime": "0.070257",
    "Content-Length": "1"
  },
  "response_content_type": "application/json",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/assessments/bulk-set`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
strand_id | true | integer
document_id | true | integer
is_group | true | boolean
assessments | true | json_object



## Create a New Individual Assessment

> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/assessments/bulk-set",
  "request_body": "assessment[strand_id]=21&assessment[document_id]=7&assessment[is_group]=false&assessment[assessments][][student_id]=3&assessment[assessments][][grade]=5&assessment[assessments][][student_id]=1&assessment[assessments][][grade]=3",
  "request_headers": {
    "Authorization": "Token token=9a4b6aecc78dd1f8411e8225b1e2501e",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": " ",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json",
    "ETag": "\"7215ee9c7d9dc229d2921a40e899ec5f\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "280acd8a-053d-45c9-aa28-68565cf0308e",
    "X-Runtime": "0.080596",
    "Content-Length": "1"
  },
  "response_content_type": "application/json",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/assessments/bulk-set`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
strand_id | true | integer
document_id | true | integer
is_group | true | boolean
assessments | true | json_object



## Show a Specific Assessment

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/assessments/4",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=9a4b6aecc78dd1f8411e8225b1e2501e",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"assessment\":{\"id\":4,\"strand_id\":19,\"document_id\":4,\"student_ids\":[11],\"grade\":3,\"is_group\":false}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"eade4669f680159cb10421a6729892e2\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "72e6d0b5-5e1d-459a-a0e4-615fffee86fd",
    "X-Runtime": "0.061489",
    "Content-Length": "100"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/assessments/:id`


## Delete an Assessment

> Example request & response:

```json
{
  "request_method": "DELETE",
  "request_path": "/api/v2/assessments/12",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=9a4b6aecc78dd1f8411e8225b1e2501e",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 204,
  "response_status_text": "No Content",
  "response_body": null,
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Cache-Control": "no-cache",
    "X-Request-Id": "82e171ba-598f-46e2-8b9e-799f06780767",
    "X-Runtime": "0.036114"
  },
  "response_content_type": null,
  "curl": null
}
```


### HTTP Request

`DELETE /api/v2/assessments/:id`



## Show a Classroom's List of Assessments For a Particular Student or Strand

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/assessments?include[]=strand_description&classroom_id=2&strand_id=4&student_id=1",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=9a4b6aecc78dd1f8411e8225b1e2501e",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include[]": "strand_description",
    "classroom_id": "2",
    "strand_id": "4",
    "student_id": "1"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"assessments\":[{\"id\":2,\"document_id\":1,\"grade\":3,\"created_at\":\"2016-10-03T15:47:54.120Z\",\"strand_id\":7,\"strand_description\":\"Accusamus architecto sit praesentium. Eveniet asperiores numquam quidem sequi error maxime est.\"},{\"id\":1,\"document_id\":1,\"grade\":2,\"created_at\":\"2016-10-03T15:47:54.108Z\",\"strand_id\":6,\"strand_description\":\"Consequatur recusandae fuga tempore voluptatem minima doloribus ut. Aperiam deserunt et ut magnam.\"}],\"level_name\":\"Overall Expectation\",\"total_count\":2}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"65b40ece20f8d571c1797bafaeded670\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "6f12fb7e-3414-48cc-b735-e9c830c52d48",
    "X-Runtime": "0.064296",
    "Content-Length": "487"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/assessments`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
classroom_id | false | integer
strand_id | false | integer
document_id | false | integer
student_id | false | integer
include | false | array of options (Options: students, strand_description)
order | false | json_object
page | false | integer
per_page | false | integer



## Show a Document's List of Assessments

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/assessments?document_id=1",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=9a4b6aecc78dd1f8411e8225b1e2501e",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "document_id": "1"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"assessments\":[{\"id\":3,\"document_id\":1,\"grade\":4,\"created_at\":\"2016-10-03T15:47:54.132Z\",\"strand_id\":12,\"student_ids\":[1],\"is_group\":false},{\"id\":2,\"document_id\":1,\"grade\":3,\"created_at\":\"2016-10-03T15:47:54.120Z\",\"strand_id\":7,\"student_ids\":[1],\"is_group\":false},{\"id\":1,\"document_id\":1,\"grade\":2,\"created_at\":\"2016-10-03T15:47:54.108Z\",\"strand_id\":6,\"student_ids\":[1],\"is_group\":false}],\"total_count\":3}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"4d3357ac4277b38ebd0df18627487dc3\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "e8e9afde-0757-46bb-8810-378e447d7dba",
    "X-Runtime": "0.916798",
    "Content-Length": "406"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/assessments`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
classroom_id | false | integer
strand_id | false | integer
document_id | false | integer
student_id | false | integer
include | false | array of options (Options: students, strand_description)
order | false | json_object
page | false | integer
per_page | false | integer


# Classrooms


## Create a Classroom

> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/classrooms",
  "request_body": "classroom[name]=Monserrat&classroom[license]&classroom[curriculum_ids][]=34&classroom[curriculum_ids][]=35&classroom[type]=Classroom&classroom[total_disk_space]=0&classroom[used_disk_space]=0&classroom[public_id]=8839177&classroom[school_id]=46&classroom[teacher_ids][]=47&classroom[teacher_ids][]=48&classroom[student_ids][]=49&classroom[student_ids][]=50&",
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"classroom\":{\"id\":59,\"local_admin_ids\":[],\"teacher_ids\":[48,47],\"student_ids\":[49,50],\"name\":\"Monserrat\",\"curriculum_ids\":[34,35],\"license_id\":9,\"is_archived\":false,\"school\":{\"id\":46,\"name\":\"Accusamus Voluptatem Quidem Necessitatibus Et Esse Tempore Iusto Ea Expedita.\",\"is_archived\":false}}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/classrooms/59",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"84cb7d68a1756b8e8f74fc6bbd9cfa3c\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "19fc9736-9bf5-4114-9f53-f5eba602912d",
    "X-Runtime": "0.187577",
    "Content-Length": "293"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/classrooms`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
teacher_ids | false | array of integers
student_ids | false | array of integers
local_admin_ids | false | array of integers
name | true | string
curriculum_ids | true | array of integers
school_id | true | integer


## Delete a Classroom

> Example request & response:

```json
{
  "request_method": "DELETE",
  "request_path": "/api/v2/classrooms/41",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=3cfc60ca29ee644bdb7c09ee09dfecaa",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 204,
  "response_status_text": "No Content",
  "response_body": null,
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Cache-Control": "no-cache",
    "X-Request-Id": "33335cdf-6a7c-440a-becd-dcdfbc81d999",
    "X-Runtime": "0.072061"
  },
  "response_content_type": null,
  "curl": null
}
```


### HTTP Request

`DELETE /api/v2/classrooms/:id`


## Show a Classroom

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/classrooms/47?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"classroom\":{\"id\":47,\"local_admin_ids\":[51,52],\"teacher_ids\":[47],\"student_ids\":[49,50],\"name\":\"Ipsam Impedit Et A Soluta Et Libero.\",\"curriculum_ids\":[34,35],\"license_id\":9,\"is_archived\":false,\"school\":{\"id\":46,\"name\":\"Accusamus Voluptatem Quidem Necessitatibus Et Esse Tempore Iusto Ea Expedita.\",\"is_archived\":false}}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"c610482d37b13f746a65238844bc243b\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "dab4ecdc-1763-4ce3-8a42-1347f0a69423",
    "X-Runtime": "0.082677",
    "Content-Length": "322"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/classrooms/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | false | array of options (Options: students, curriculums, overview, recent_activity)


## Update a Classroom

> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/classrooms/48",
  "request_body": "classroom[name]=Necessitatibus+Ipsum+Voluptates+Reprehenderit+Ad+Consequatur.&classroom[license]&classroom[curriculum_ids][]=34&classroom[curriculum_ids][]=35&classroom[type]=Classroom&classroom[total_disk_space]=0&classroom[used_disk_space]=0&classroom[public_id]=8839177&classroom[teacher_ids][]=47&classroom[teacher_ids][]=48&classroom[student_ids][]=49&classroom[student_ids][]=50",
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"classroom\":{\"id\":48,\"local_admin_ids\":[53],\"teacher_ids\":[48,47],\"student_ids\":[49,50],\"name\":\"Necessitatibus Ipsum Voluptates Reprehenderit Ad Consequatur.\",\"curriculum_ids\":[34,35],\"license_id\":9,\"is_archived\":false,\"school\":{\"id\":46,\"name\":\"Accusamus Voluptatem Quidem Necessitatibus Et Esse Tempore Iusto Ea Expedita.\",\"is_archived\":false}}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/classrooms/48",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "febb528a-07da-4803-a3dc-efe49bf6667e",
    "X-Runtime": "0.087362",
    "Content-Length": "347"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/classrooms/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
teacher_ids | false | array of integers
student_ids | false | array of integers
local_admin_ids | false | array of integers
name | false | string
curriculum_ids | false | array of integers


## Show a List of Classroom

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/classrooms?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"classrooms\":[{\"id\":53,\"name\":\"Ratione Nulla Eius Nihil Neque Est Culpa Facilis Amet Enim.\",\"is_archived\":true,\"created_at\":\"2016-10-03T15:48:12.552Z\",\"teacher_ids\":[55],\"student_ids\":[56]},{\"id\":52,\"name\":\"Occaecati Possimus Exercitationem Eum Atque Culpa Quidem Aut Distinctio Sunt Sunt.\",\"is_archived\":false,\"created_at\":\"2016-10-03T15:48:12.491Z\",\"teacher_ids\":[55],\"student_ids\":[56]},{\"id\":51,\"name\":\"Laboriosam Enim Quasi Facilis Incidunt Praesentium Magni Dolorem.\",\"is_archived\":false,\"created_at\":\"2016-10-03T15:48:12.430Z\",\"teacher_ids\":[54,55],\"student_ids\":[57]},{\"id\":49,\"name\":\"Optio Dolores Dolores Modi Amet In.\",\"is_archived\":true,\"created_at\":\"2016-10-03T15:48:12.126Z\",\"teacher_ids\":[47,48],\"student_ids\":[50]},{\"id\":48,\"name\":\"Sapiente Maxime Autem Asperiores Illum Dolorem.\",\"is_archived\":false,\"created_at\":\"2016-10-03T15:48:12.024Z\",\"teacher_ids\":[47],\"student_ids\":[49,50]},{\"id\":47,\"name\":\"Ipsam Impedit Et A Soluta Et Libero.\",\"is_archived\":false,\"created_at\":\"2016-10-03T15:48:11.935Z\",\"teacher_ids\":[47],\"student_ids\":[49,50]}],\"total_count\":6}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"f5c05e386df7b77b8f1113d3fbe76fd8\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "76fe5ff3-2d58-4b6b-8157-efcdca25f177",
    "X-Runtime": "0.068564",
    "Content-Length": "1074"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```



### HTTP Request

`GET /api/v2/classrooms`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
school_id | false | integer
show_archived | false | boolean
license_id | false | integer
include | false | array of strings


## Show Classroom's Students

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/classrooms/47/students?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":50,\"first_name\":\"Enrico\",\"last_name\":\"Rempel\",\"is_archived\":false,\"has_consent\":false,\"birthday\":\"2001-10-03T15:48:11.758Z\",\"grade_level\":12,\"public_id\":\"6366042\"},{\"id\":49,\"first_name\":\"Valerie\",\"last_name\":\"Kulas\",\"is_archived\":false,\"has_consent\":false,\"birthday\":\"2001-10-03T15:48:11.707Z\",\"grade_level\":12,\"public_id\":\"1485134\"}],\"total_count\":2}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"8d4312f639b1d5fd48ee2b92efec8d51\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "0879f251-4820-4c2a-a315-b3c760cf374e",
    "X-Runtime": "0.243282",
    "Content-Length": "367"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```



### HTTP Request

`GET /api/v2/classrooms/:id/students`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
exclude_ids| false | array of student ids
include | false | array of options (Options: school_count, classroom_count, status)



## Show Classroom's Teachers

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/classrooms/47/teachers?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":47,\"first_name\":\"Icie\",\"last_name\":\"Reichert\",\"is_archived\":false,\"type\":\"Teacher\",\"username\":\"teacher26\",\"email\":\"test9896@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"}],\"total_count\":1}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"3c7ea860da5147f4ce52514d22c5eb7f\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "3aeff236-60bf-4a24-af0b-57b56a31c234",
    "X-Runtime": "0.128881",
    "Content-Length": "238"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```



### HTTP Request

`GET /api/v2/classrooms/:id/teachers`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
exclude_ids| false | array of teacher ids
include | false | array of options (Options: classroom_count, status)


## Add or Remove Local Admins from a Classroom

> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/classrooms/47/update-local-admins",
  "request_body": "classroom[add_ids][]=73",
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"classroom\":{\"id\":47,\"local_admin_ids\":[52,73],\"teacher_ids\":[47,72],\"student_ids\":[49,50,71],\"name\":\"Ipsam Impedit Et A Soluta Et Libero.\",\"curriculum_ids\":[34,35],\"license_id\":9,\"is_archived\":false,\"school\":{\"id\":46,\"name\":\"Accusamus Voluptatem Quidem Necessitatibus Et Esse Tempore Iusto Ea Expedita.\",\"is_archived\":false}}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/classrooms/47",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "a9ccaa71-3725-4cde-8e32-7a0aaa7fc0bd",
    "X-Runtime": "0.131771",
    "Content-Length": "328"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/classrooms/:id/update-local-admins`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
remove_ids | false | array of integers
add_ids | false | array of integers




## Add or Remove Students from a Classroom

> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/classrooms/47/update-students",
  "request_body": "classroom[add_ids][]=71",
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"classroom\":{\"id\":47,\"local_admin_ids\":[52],\"teacher_ids\":[47],\"student_ids\":[49,50,71],\"name\":\"Ipsam Impedit Et A Soluta Et Libero.\",\"curriculum_ids\":[34,35],\"license_id\":9,\"is_archived\":false,\"school\":{\"id\":46,\"name\":\"Accusamus Voluptatem Quidem Necessitatibus Et Esse Tempore Iusto Ea Expedita.\",\"is_archived\":false}}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/classrooms/47",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "669d7aa9-4b50-4868-a321-fa744ff600b8",
    "X-Runtime": "0.147449",
    "Content-Length": "322"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/classrooms/:id/update-students`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
remove_ids | false | array of integers
add_ids | false | array of integers



## Add or Remove Teachers from a Classroom

> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/classrooms/47/update-teachers",
  "request_body": "classroom[add_ids][]=72",
  "request_headers": {
    "Authorization": "Token token=2234442be74b91df4d7a3d8f8638457e",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"classroom\":{\"id\":47,\"local_admin_ids\":[52],\"teacher_ids\":[47,72],\"student_ids\":[49,50,71],\"name\":\"Ipsam Impedit Et A Soluta Et Libero.\",\"curriculum_ids\":[34,35],\"license_id\":9,\"is_archived\":false,\"school\":{\"id\":46,\"name\":\"Accusamus Voluptatem Quidem Necessitatibus Et Esse Tempore Iusto Ea Expedita.\",\"is_archived\":false}}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/classrooms/47",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "84705c05-af1e-496e-b66d-37fc04617681",
    "X-Runtime": "0.167313",
    "Content-Length": "325"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/classrooms/:id/update-teachers`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
remove_ids | false | array of integers
add_ids | false | array of integers






# Documents


## Create a Document

> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/documents",
  "request_body": "document[title]=New+Document+Title&document[student_ids][]=90&document[student_ids][]=91&document[classroom_id]=68&document[date]=1990-03-14+15%3A48%3A39+UTC",
  "request_headers": {
    "Authorization": "Token token=2c0b01fe85c6aa2bb1525dc5e9dd027d",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"document\":{\"tags\":[],\"id\":59,\"title\":\"New Document Title\",\"date\":\"1990-03-14T15:48:39.000Z\",\"is_template\":false,\"student_ids\":[90,91],\"note_ids\":[],\"strand_ids\":[],\"classroom_id\":68,\"preferences\":{}},\"students\":[{\"id\":90,\"first_name\":\"Anika\",\"last_name\":\"Lesch\",\"has_consent\":false},{\"id\":91,\"first_name\":\"Kavon\",\"last_name\":\"Bashirian\",\"has_consent\":false}],\"notes\":[],\"media\":[],\"group_assessment\":null}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/documents/59",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"626fa4526608fde4b5ce55f88cf2e48a\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "9c168420-801f-4631-81ae-7d8c82e0c50c",
    "X-Runtime": "0.136958",
    "Content-Length": "407"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/documents`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
title | true | string
date | true | datetime
student_ids | false | array
medium_ids | false | array
strand_ids | false | array
classroom_id | false | integer
note_ids | false | array



## Delete a Document

> Example request & response:

```json
{
  "request_method": "DELETE",
  "request_path": "/api/v2/documents/66",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2c0b01fe85c6aa2bb1525dc5e9dd027d",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 204,
  "response_status_text": "No Content",
  "response_body": null,
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Cache-Control": "no-cache",
    "X-Request-Id": "bb0cf2f4-f95c-4334-9a7f-a5225f325fa4",
    "X-Runtime": "0.049834"
  },
  "response_content_type": null,
  "curl": null
}
```


### HTTP Request

`DELETE /api/v2/documents/:id`


## Show a Document

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/documents/45",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2c0b01fe85c6aa2bb1525dc5e9dd027d",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"document\":{\"tags\":[{\"id\":5,\"name\":\"homework\",\"color\":\"aut\"},{\"id\":3,\"name\":\"english\",\"color\":\"dolorum\"}],\"id\":45,\"title\":\"Main document\",\"date\":\"1994-07-05T15:48:29.560Z\",\"is_template\":false,\"student_ids\":[90,91],\"note_ids\":[12,11],\"strand_ids\":[],\"classroom_id\":68,\"preferences\":{\"note_show\":true}},\"students\":[{\"id\":90,\"first_name\":\"Anika\",\"last_name\":\"Lesch\",\"has_consent\":false},{\"id\":91,\"first_name\":\"Kavon\",\"last_name\":\"Bashirian\",\"has_consent\":false}],\"notes\":[{\"id\":11,\"title\":\"Iure quidem qui impedit possimus hic.\",\"category\":\"reflection\",\"content\":\"Ea quia odio architecto in temporibus. Corporis et omnis dolor. Deserunt qui tempore quos facilis incidunt. Vitae velit laboriosam minus aliquam amet quibusdam. Distinctio aspernatur illum ipsum est. Sit tempore impedit dolor rerum ut. Et assumenda sed tenetur doloribus laborum. Totam placeat itaque. Et dolores quam reiciendis. Voluptas quo totam.\",\"created_at\":\"2016-10-03T15:48:29.900Z\"},{\"id\":12,\"title\":\"Corrupti ad voluptates error rerum aliquam aliquid accusamus dolor repudiandae omnis.\",\"category\":\"opportunity\",\"content\":\"Sit quidem est pariatur et officiis. Qui et necessitatibus quae dolores quasi placeat voluptatem. Quo autem sit optio libero molestiae voluptatibus sit. Omnis aut repellendus assumenda nulla saepe. Odio ipsa dicta labore dolor sint sit. Nobis repellat pariatur. Eius non voluptatibus voluptatem laudantium totam ut accusamus. Eos dolore velit consequuntur saepe eaque. Veniam praesentium sed illum. Autem quidem ad maiores facere doloribus. Harum ut similique dignissimos voluptatem. Nostrum qui dolores error sit.\",\"created_at\":\"2016-10-03T15:48:29.904Z\"}],\"media\":[{\"id\":1,\"category\":\"image\"},{\"id\":2,\"category\":\"image\"},{\"id\":3,\"category\":\"image\"}],\"group_assessment\":false}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"15c3bfa3f4fae4afd31ba1c29ec0437c\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "a029a037-e091-480a-97fc-32e8058f74c0",
    "X-Runtime": "0.156860",
    "Content-Length": "1772"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/documents/:id`



## Update a Document

> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/documents/65/",
  "request_body": "document[title]=New+Document+Title&document[student_ids][]=90&document[student_ids][]=91&document[classroom_id]=68&document[date]=2013-06-15+15%3A48%3A41+UTC",
  "request_headers": {
    "Authorization": "Token token=2c0b01fe85c6aa2bb1525dc5e9dd027d",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"document\":{\"tags\":[],\"id\":65,\"title\":\"New Document Title\",\"date\":\"2013-06-15T15:48:41.000Z\",\"is_template\":false,\"student_ids\":[90,91],\"note_ids\":[],\"strand_ids\":[],\"classroom_id\":68,\"preferences\":{\"note_show\":true}},\"students\":[{\"id\":90,\"first_name\":\"Anika\",\"last_name\":\"Lesch\",\"has_consent\":false},{\"id\":91,\"first_name\":\"Kavon\",\"last_name\":\"Bashirian\",\"has_consent\":false}],\"notes\":[],\"media\":[],\"group_assessment\":null}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/documents/65",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "c349cc51-a88f-4665-b770-91ff6450e693",
    "X-Runtime": "0.058913",
    "Content-Length": "423"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/documents/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
title | false | string
date | false | datetime
student_ids | false | array
medium_ids | false | array
strand_ids | false | array
note_ids | false | array




## Add Notes to a Document

> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/documents/45/add-notes",
  "request_body": "document[note_ids][]=23",
  "request_headers": {
    "Authorization": "Token token=2c0b01fe85c6aa2bb1525dc5e9dd027d",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"document\":{\"tags\":[{\"id\":5,\"name\":\"homework\",\"color\":\"aut\"},{\"id\":3,\"name\":\"english\",\"color\":\"dolorum\"},{\"id\":6,\"name\":\"doloremque corporis illo quo. tempora ipsum voluptatem optio aut. laborum rem hic doloremque.\",\"color\":\"#FFFFFF\"}],\"id\":45,\"title\":\"Main document\",\"date\":\"1994-07-05T15:48:29.560Z\",\"is_template\":false,\"student_ids\":[90,91],\"note_ids\":[23,12,11],\"strand_ids\":[43],\"classroom_id\":68,\"preferences\":{\"note_show\":true}},\"students\":[{\"id\":90,\"first_name\":\"Anika\",\"last_name\":\"Lesch\",\"has_consent\":false},{\"id\":91,\"first_name\":\"Kavon\",\"last_name\":\"Bashirian\",\"has_consent\":false}],\"notes\":[{\"id\":11,\"title\":\"Iure quidem qui impedit possimus hic.\",\"category\":\"reflection\",\"content\":\"Ea quia odio architecto in temporibus. Corporis et omnis dolor. Deserunt qui tempore quos facilis incidunt. Vitae velit laboriosam minus aliquam amet quibusdam. Distinctio aspernatur illum ipsum est. Sit tempore impedit dolor rerum ut. Et assumenda sed tenetur doloribus laborum. Totam placeat itaque. Et dolores quam reiciendis. Voluptas quo totam.\",\"created_at\":\"2016-10-03T15:48:29.900Z\"},{\"id\":12,\"title\":\"Corrupti ad voluptates error rerum aliquam aliquid accusamus dolor repudiandae omnis.\",\"category\":\"opportunity\",\"content\":\"Sit quidem est pariatur et officiis. Qui et necessitatibus quae dolores quasi placeat voluptatem. Quo autem sit optio libero molestiae voluptatibus sit. Omnis aut repellendus assumenda nulla saepe. Odio ipsa dicta labore dolor sint sit. Nobis repellat pariatur. Eius non voluptatibus voluptatem laudantium totam ut accusamus. Eos dolore velit consequuntur saepe eaque. Veniam praesentium sed illum. Autem quidem ad maiores facere doloribus. Harum ut similique dignissimos voluptatem. Nostrum qui dolores error sit.\",\"created_at\":\"2016-10-03T15:48:29.904Z\"},{\"id\":23,\"title\":\"Ut sit quia repudiandae voluptatem praesentium autem.\",\"category\":\"observation\",\"content\":\"Explicabo eos perferendis. Molestias non voluptatem earum ea aperiam quia. Voluptas quia veniam et consequatur. Suscipit id aperiam. Molestias consequatur nulla. Et necessitatibus quisquam. Illum repudiandae aut ipsum. Dolor amet in nemo illum vel est mollitia. A perspiciatis officiis fugit aperiam quisquam. In qui qui dolorum est dolorem. Ut assumenda et et facere.\",\"created_at\":\"2016-10-03T15:48:42.223Z\"}],\"media\":[{\"id\":1,\"category\":\"image\"},{\"id\":2,\"category\":\"image\"},{\"id\":3,\"category\":\"image\"}],\"group_assessment\":null}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/documents/45",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"9bc9ae2354da07ae6d2ac03e844f73ac\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "f47325ee-4b16-4716-991b-02756bb5dd84",
    "X-Runtime": "0.099138",
    "Content-Length": "2426"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/documents/:id/add-notes`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
note_ids | false | array



## Duplicate a Document

> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "api/v2/documents/45/duplicate",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2c0b01fe85c6aa2bb1525dc5e9dd027d",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"document\":{\"tags\":[{\"id\":5,\"name\":\"homework\",\"color\":\"aut\"},{\"id\":3,\"name\":\"english\",\"color\":\"dolorum\"},{\"id\":6,\"name\":\"doloremque corporis illo quo. tempora ipsum voluptatem optio aut. laborum rem hic doloremque.\",\"color\":\"#FFFFFF\"}],\"id\":62,\"title\":\"Main document Copy\",\"date\":\"1994-07-05T15:48:29.560Z\",\"is_template\":false,\"student_ids\":[90,91],\"note_ids\":[],\"strand_ids\":[43],\"classroom_id\":68,\"preferences\":{\"note_show\":true}},\"students\":[{\"id\":90,\"first_name\":\"Anika\",\"last_name\":\"Lesch\",\"has_consent\":false},{\"id\":91,\"first_name\":\"Kavon\",\"last_name\":\"Bashirian\",\"has_consent\":false}],\"notes\":[{\"id\":17,\"title\":\"Iure quidem qui impedit possimus hic.\",\"category\":\"reflection\",\"content\":\"Ea quia odio architecto in temporibus. Corporis et omnis dolor. Deserunt qui tempore quos facilis incidunt. Vitae velit laboriosam minus aliquam amet quibusdam. Distinctio aspernatur illum ipsum est. Sit tempore impedit dolor rerum ut. Et assumenda sed tenetur doloribus laborum. Totam placeat itaque. Et dolores quam reiciendis. Voluptas quo totam.\",\"created_at\":\"2016-10-03T15:48:40.873Z\"},{\"id\":18,\"title\":\"Corrupti ad voluptates error rerum aliquam aliquid accusamus dolor repudiandae omnis.\",\"category\":\"opportunity\",\"content\":\"Sit quidem est pariatur et officiis. Qui et necessitatibus quae dolores quasi placeat voluptatem. Quo autem sit optio libero molestiae voluptatibus sit. Omnis aut repellendus assumenda nulla saepe. Odio ipsa dicta labore dolor sint sit. Nobis repellat pariatur. Eius non voluptatibus voluptatem laudantium totam ut accusamus. Eos dolore velit consequuntur saepe eaque. Veniam praesentium sed illum. Autem quidem ad maiores facere doloribus. Harum ut similique dignissimos voluptatem. Nostrum qui dolores error sit.\",\"created_at\":\"2016-10-03T15:48:40.879Z\"}],\"media\":[],\"group_assessment\":null}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/documents/62",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"2e609d2907a25e9167a3e8ea8e524af5\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "42174fe7-69d5-4197-8f4b-7beae2a12349",
    "X-Runtime": "0.189293",
    "Content-Length": "1820"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/documents/:id/duplicate`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
note_ids | false | array



## Save a Document as a Template

> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "api/v2/documents/45/save-as-template",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2c0b01fe85c6aa2bb1525dc5e9dd027d",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"document\":{\"tags\":[{\"id\":5,\"name\":\"homework\",\"color\":\"aut\"},{\"id\":3,\"name\":\"english\",\"color\":\"dolorum\"},{\"id\":6,\"name\":\"doloremque corporis illo quo. tempora ipsum voluptatem optio aut. laborum rem hic doloremque.\",\"color\":\"#FFFFFF\"}],\"id\":64,\"title\":\"Main document Copy\",\"date\":\"1994-07-05T15:48:29.560Z\",\"is_template\":true,\"student_ids\":[90,91],\"note_ids\":[],\"strand_ids\":[43],\"classroom_id\":68,\"preferences\":{\"note_show\":true}},\"students\":[{\"id\":90,\"first_name\":\"Anika\",\"last_name\":\"Lesch\",\"has_consent\":false},{\"id\":91,\"first_name\":\"Kavon\",\"last_name\":\"Bashirian\",\"has_consent\":false}],\"notes\":[{\"id\":21,\"title\":\"Iure quidem qui impedit possimus hic.\",\"category\":\"reflection\",\"content\":\"Ea quia odio architecto in temporibus. Corporis et omnis dolor. Deserunt qui tempore quos facilis incidunt. Vitae velit laboriosam minus aliquam amet quibusdam. Distinctio aspernatur illum ipsum est. Sit tempore impedit dolor rerum ut. Et assumenda sed tenetur doloribus laborum. Totam placeat itaque. Et dolores quam reiciendis. Voluptas quo totam.\",\"created_at\":\"2016-10-03T15:48:41.238Z\"},{\"id\":22,\"title\":\"Corrupti ad voluptates error rerum aliquam aliquid accusamus dolor repudiandae omnis.\",\"category\":\"opportunity\",\"content\":\"Sit quidem est pariatur et officiis. Qui et necessitatibus quae dolores quasi placeat voluptatem. Quo autem sit optio libero molestiae voluptatibus sit. Omnis aut repellendus assumenda nulla saepe. Odio ipsa dicta labore dolor sint sit. Nobis repellat pariatur. Eius non voluptatibus voluptatem laudantium totam ut accusamus. Eos dolore velit consequuntur saepe eaque. Veniam praesentium sed illum. Autem quidem ad maiores facere doloribus. Harum ut similique dignissimos voluptatem. Nostrum qui dolores error sit.\",\"created_at\":\"2016-10-03T15:48:41.246Z\"}],\"media\":[],\"group_assessment\":null}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/documents/64",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"a1f0fafed5cdbde322c8c0420cb27939\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "6b97964f-e97a-4ca3-b535-7c22c88edcf9",
    "X-Runtime": "0.143231",
    "Content-Length": "1819"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/documents/:id/save-as-template`



## Show a List of Documents

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/documents?include[]=note_ids",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=2c0b01fe85c6aa2bb1525dc5e9dd027d",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include[]": "note_ids"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"documents\":[{\"id\":48,\"title\":\"exercitationem consequatur dolore et rerum.\",\"date\":\"2001-04-16T15:48:31.284Z\",\"is_template\":false,\"classroom_id\":68,\"note_ids\":[]},{\"id\":45,\"title\":\"Main document\",\"date\":\"1994-07-05T15:48:29.560Z\",\"is_template\":false,\"classroom_id\":68,\"note_ids\":[12,11]},{\"id\":47,\"title\":\"EOS ILLUM SUNT FACILIS EX ULLAM OCCAECATI VOLUPTATEM AUT.\",\"date\":\"1993-04-10T15:48:31.190Z\",\"is_template\":false,\"classroom_id\":68,\"note_ids\":[]},{\"id\":49,\"title\":\"recusandae consequatur voluptatibus dolores quia aperiam beatae sint amet.\",\"date\":\"1992-05-08T15:48:31.400Z\",\"is_template\":false,\"classroom_id\":68,\"note_ids\":[]},{\"id\":46,\"title\":\"Other document\",\"date\":\"1990-06-20T15:48:31.018Z\",\"is_template\":false,\"classroom_id\":68,\"note_ids\":[]}],\"total_count\":5}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"418a4833d364337894004fc7e030d52d\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "219da84b-5201-4a1f-aa76-eba5b08ff7bc",
    "X-Runtime": "0.179451",
    "Content-Length": "772"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/documents`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
student_id | false | integer
classroom_id | false | integer
tag_ids | false | array
keyword | false | string
include | false | array of options (Options: tags, strands)
order | false | json_object


# Guardians


## Create a Guardian

> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/guardians",
  "request_body": "user[license_id]=56&user[username]=test6438&user[email]=test10112%40pivotallabs.com&user[first_name]=Edd&user[last_name]=O%27Hara&user[type]=Guardian&user[country_code]=CA&user[language_code]=en&user[public_id]=3967864&user[phone_number]=14163334444&user[phone_extension]=55555&user[student_id]=250",
  "request_headers": {
    "Authorization": "Token token=c9e7f7f42ec5ed0e6625fd7397887f5a",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"user\":{\"id\":261,\"type\":\"Guardian\",\"username\":\"test6438\",\"email\":\"test10112@pivotallabs.com\",\"first_name\":\"Edd\",\"last_name\":\"O'Hara\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":56,\"language_code\":\"en\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/guardians/261",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"b8e2d7feb1a968fc85bb54d157dbe183\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "5a138983-16ea-4f45-895e-f1fd8bac6e2f",
    "X-Runtime": "0.204816",
    "Content-Length": "293"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/guardians`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
license_id | false | integer
username | true | string
email | true | string
password | false | string
password_confirmation | false | string
first_name | false | string
last_name | false | string
country_code | false | string
phone_number | false | string
phone_extension | false | string
public_id | false | string
student_id | true | integer



## Show a Guardian

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/guardians/249?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=c9e7f7f42ec5ed0e6625fd7397887f5a",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"user\":{\"id\":249,\"type\":\"Guardian\",\"username\":\"aquitzon\",\"email\":\"test10100@pivotallabs.com\",\"first_name\":\"Amaya\",\"last_name\":\"Quitzon\",\"phone_number\":\"12223334444\",\"phone_extension\":null,\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":56,\"language_code\":\"en\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"d2ca1252064e0b460c90ed0cd6d79470\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "d5db44c6-323c-4c6c-b92b-ac8f64396b44",
    "X-Runtime": "0.055801",
    "Content-Length": "293"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/guardians/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | false | array of options (Options: schools, classrooms, teacher_count, student_count)



## Update a Guardian

> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/guardians/249/",
  "request_body": "user[license_id]=56&user[username]=test6442&user[email]=test10116%40pivotallabs.com&user[first_name]=Max&user[last_name]=Ledner&user[type]=Guardian&user[country_code]=CA&user[language_code]=en&user[public_id]=8824826&user[phone_number]=14163334444&user[phone_extension]=55555&user[student_id]=250",
  "request_headers": {
    "Authorization": "Token token=c9e7f7f42ec5ed0e6625fd7397887f5a",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"user\":{\"id\":249,\"type\":\"Guardian\",\"username\":\"test6442\",\"email\":\"test10116@pivotallabs.com\",\"first_name\":\"Max\",\"last_name\":\"Ledner\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":true,\"license_id\":56,\"language_code\":\"en\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/guardians/249",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "9f98865e-4a1d-49ef-a0d0-eb71c5532678",
    "X-Runtime": "0.173331",
    "Content-Length": "292"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/guardians/:id/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | string
email | true | string
password | false | string
password_confirmation | false | string
first_name | false | string
last_name | false | string
country_code | false | string
phone_number | false | string
phone_extension | false | string
public_id | false | string



## Show a List of Guardians

> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/guardians?include=[]&per_page=10",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=c9e7f7f42ec5ed0e6625fd7397887f5a",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]",
    "per_page": "10"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":259,\"first_name\":\"Xzavier\",\"last_name\":\"Yost\",\"is_archived\":true,\"type\":\"Guardian\",\"username\":\"xyost\",\"email\":\"test10110@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":258,\"first_name\":\"Kellie\",\"last_name\":\"Bergnaum\",\"is_archived\":true,\"type\":\"Guardian\",\"username\":\"kbergnaum\",\"email\":\"test10109@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":257,\"first_name\":\"Fatima\",\"last_name\":\"Herzog\",\"is_archived\":true,\"type\":\"Guardian\",\"username\":\"fherzog\",\"email\":\"test10108@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":256,\"first_name\":\"Darron\",\"last_name\":\"Keeling\",\"is_archived\":true,\"type\":\"Guardian\",\"username\":\"dkeeling\",\"email\":\"test10107@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":255,\"first_name\":\"Eulalia\",\"last_name\":\"Marquardt\",\"is_archived\":false,\"type\":\"Guardian\",\"username\":\"emarquardt\",\"email\":\"test10106@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":254,\"first_name\":\"Anabel\",\"last_name\":\"Kunze\",\"is_archived\":false,\"type\":\"Guardian\",\"username\":\"akunze\",\"email\":\"test10105@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":253,\"first_name\":\"Brennon\",\"last_name\":\"Hyatt\",\"is_archived\":false,\"type\":\"Guardian\",\"username\":\"bhyatt\",\"email\":\"test10104@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":252,\"first_name\":\"Vivienne\",\"last_name\":\"Klocko\",\"is_archived\":false,\"type\":\"Guardian\",\"username\":\"vklocko\",\"email\":\"test10103@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":251,\"first_name\":\"Christelle\",\"last_name\":\"Deckow\",\"is_archived\":false,\"type\":\"Guardian\",\"username\":\"test6437\",\"email\":\"test10102@pivotallabs.com\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\"},{\"id\":249,\"first_name\":\"Amaya\",\"last_name\":\"Quitzon\",\"is_archived\":false,\"type\":\"Guardian\",\"username\":\"aquitzon\",\"email\":\"test10100@pivotallabs.com\",\"phone_number\":\"12223334444\",\"phone_extension\":null,\"country_code\":\"CA\"}],\"total_count\":10}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"6c76218c846777c56408d250b240d1bc\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "46841dc7-8aa9-43fd-9d5d-29779ea2cdb1",
    "X-Runtime": "0.113999",
    "Content-Length": "2180"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/guardians`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
show_archived | false | boolean
include | false | array of options (Options: school_count, classroom_count, status)
exclude_ids | false | array of guardian ids


# Languages

## Show a List of Languages


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/languages",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=72a93132545e7b1e8c8eab27551c708e",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"languages\":[{\"id\":1,\"code\":\"en\",\"name\":\"English\",\"updated_at\":\"2016-10-03T15:48:42.795Z\"},{\"id\":2,\"code\":\"en1-test\",\"name\":\"English\",\"updated_at\":\"2016-10-03T15:48:42.811Z\"}]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"ff3f4a48daea0ec6a2921a523d81f6ae\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "2a1ee10f-0b90-46d4-8339-f397efa01f53",
    "X-Runtime": "0.104817",
    "Content-Length": "177"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/languages`

# License Admins


## Show a License Admin


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/license-admins/275?include=%23%3CRSpec%3A%3AMatchers%3A%3ABuiltIn%3A%3AInclude%3A0x007f0467cb85f0%3E",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=807086879b0cbd2caeb7e12bc51d6a63",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "#<RSpec::Matchers::BuiltIn::Include:0x007f0467cb85f0>"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"user\":{\"id\":275,\"type\":\"LicenseAdmin\",\"username\":\"license_admin8\",\"email\":\"test10131@pivotallabs.com\",\"first_name\":\"Nicolette\",\"last_name\":\"Hagenes\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":58,\"language_code\":\"en\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"0ae69554aadf113feb821842b420a60e\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "70ce09a3-cdad-47a0-a6b9-2ce32f5f21a7",
    "X-Runtime": "0.089017",
    "Content-Length": "298"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/license-admins/:id`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | false | array of options (Options: schools, classrooms, teacher_count, student_count)



## Show a List of License Admins


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/license-admins?include=[]&per_page=10",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=807086879b0cbd2caeb7e12bc51d6a63",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]",
    "per_page": "10"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":283,\"first_name\":\"Tate\",\"last_name\":\"Metz\",\"is_archived\":true,\"type\":\"LicenseAdmin\",\"username\":\"license_admin16\",\"email\":\"test10139@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":282,\"first_name\":\"Lucie\",\"last_name\":\"Koepp\",\"is_archived\":true,\"type\":\"LicenseAdmin\",\"username\":\"license_admin15\",\"email\":\"test10138@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":281,\"first_name\":\"Delta\",\"last_name\":\"Sawayn\",\"is_archived\":true,\"type\":\"LicenseAdmin\",\"username\":\"license_admin14\",\"email\":\"test10137@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":280,\"first_name\":\"Tatyana\",\"last_name\":\"Keebler\",\"is_archived\":true,\"type\":\"LicenseAdmin\",\"username\":\"license_admin13\",\"email\":\"test10136@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":279,\"first_name\":\"Pascale\",\"last_name\":\"Stokes\",\"is_archived\":false,\"type\":\"LicenseAdmin\",\"username\":\"license_admin12\",\"email\":\"test10135@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":278,\"first_name\":\"Heather\",\"last_name\":\"Lesch\",\"is_archived\":false,\"type\":\"LicenseAdmin\",\"username\":\"license_admin11\",\"email\":\"test10134@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":277,\"first_name\":\"Einar\",\"last_name\":\"Okuneva\",\"is_archived\":false,\"type\":\"LicenseAdmin\",\"username\":\"license_admin10\",\"email\":\"test10133@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":276,\"first_name\":\"Jerad\",\"last_name\":\"Kutch\",\"is_archived\":false,\"type\":\"LicenseAdmin\",\"username\":\"license_admin9\",\"email\":\"test10132@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":275,\"first_name\":\"Nicolette\",\"last_name\":\"Hagenes\",\"is_archived\":false,\"type\":\"LicenseAdmin\",\"username\":\"license_admin8\",\"email\":\"test10131@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":274,\"first_name\":\"Vicky\",\"last_name\":\"Boyer\",\"is_archived\":false,\"type\":\"LicenseAdmin\",\"username\":\"license_admin7\",\"email\":\"test10130@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"}],\"total_count\":10}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"ea2e051773b3b6da11a1072f19de59f3\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "250f2699-57bc-4665-8617-be5c115e2d7f",
    "X-Runtime": "0.154365",
    "Content-Length": "2257"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/license-admins/`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
show_archived | false | boolean
exclude_ids | false | array
include | false | array of options (Options: school_count, classroom_count, status)


# Licenses


## Create a License


> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/licenses",
  "request_body": "license[name]=molestias27&license[purchasing_contact_info][first_name]=Caleigh&license[purchasing_contact_info][last_name]=Witting&license[purchasing_contact_info][email]=molestias27%40pivotallabs.fake&license[purchasing_contact_info][phone_number]=14161112222&license[purchasing_contact_info][phone_extension]=1234&license[purchasing_contact_info][address]=69+Yonge+St.&license[purchasing_contact_info][city]=Toronto&license[purchasing_contact_info][postal_code]=M5S+2L9&license[purchasing_contact_info][country]=Canada&license[purchasing_contact_info][country_code]=CA&license[expiry]=2017-10-03+15%3A48%3A44+UTC&license[languages][]=en&license[default_language_code]=en&license[curriculum_ids][]=61&license[curriculum_ids][]=62&license[limits][disk_space]=100000000&license[limits][schools]=100000000&license[limits][classrooms]=100000000&license[limits][students]=100000000&license[limits][teachers]=100000000&license[secret_key]=c5c504011a9f42a2227ce98fdda8360d&license[is_pearson]=true",
  "request_headers": {
    "Authorization": "Token token=1ad7dcd132509130f157cf5adf2df2c4",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"license\":{\"id\":27,\"is_pearson\":true,\"secret_key\":\"b0ef52cdf3d4933ddf020d9e2837039a\",\"name\":\"molestias27\",\"languages\":[\"en\"],\"default_language_code\":\"en\",\"limits\":{\"disk_space\":\"100000000\",\"schools\":\"100000000\",\"classrooms\":\"100000000\",\"students\":\"100000000\",\"teachers\":\"100000000\"},\"usage\":{\"disk_space\":\"0\",\"schools\":\"0\",\"classrooms\":\"0\",\"students\":\"0\",\"teachers\":\"0\"},\"expiry\":\"2017-10-03T15:48:44.000Z\",\"purchasing_contact_info\":{\"first_name\":\"Caleigh\",\"last_name\":\"Witting\",\"email\":\"molestias27@pivotallabs.fake\",\"phone_number\":\"14161112222\",\"phone_extension\":\"1234\",\"address\":\"69 Yonge St.\",\"postal_code\":\"M5S 2L9\",\"city\":\"Toronto\",\"country\":\"Canada\",\"country_code\":\"CA\"},\"curriculum_ids\":[\"61\",\"62\"],\"group_assessment\":false}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/licenses/27",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"1b8b103ad53b79f8403d7bca73424952\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "e5fce222-d288-421f-8dbf-01693d3df8dc",
    "X-Runtime": "0.067711",
    "Content-Length": "734"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/licenses`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
name | true | string
purchasing_contact_info | true | json_object
limits | true | json_object
languages | true | array of strings
curriculum_ids | true | array of integers



## Show a License


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/licenses/22",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=1ad7dcd132509130f157cf5adf2df2c4",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"license\":{\"id\":22,\"is_pearson\":false,\"secret_key\":\"d8adb5177773962174fa0b3a06f89f97\",\"name\":\"veritatis22\",\"languages\":[\"en\"],\"default_language_code\":\"en\",\"limits\":{\"schools\":\"100000000\",\"students\":\"100000000\",\"teachers\":\"100000000\",\"classrooms\":\"100000000\",\"disk_space\":\"100000000\"},\"usage\":{\"schools\":\"0\",\"students\":\"0\",\"teachers\":\"0\",\"classrooms\":\"0\",\"disk_space\":\"0\"},\"expiry\":\"2017-10-03T15:48:44.405Z\",\"purchasing_contact_info\":{\"city\":\"Toronto\",\"email\":\"veritatis22@pivotallabs.fake\",\"address\":\"69 Yonge St.\",\"country\":\"Canada\",\"last_name\":\"Cassin\",\"first_name\":\"Florine\",\"postal_code\":\"M5S 2L9\",\"country_code\":\"CA\",\"phone_number\":\"14161112222\",\"phone_extension\":\"1234\"},\"curriculum_ids\":[61,62],\"group_assessment\":false}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"1784c4b076219fa8b3b52dcf05542841\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "bf4be36b-d194-4003-ab85-677ca98d4302",
    "X-Runtime": "0.068406",
    "Content-Length": "730"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/licenses/:id`


## Show a List of Licenses


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/licenses",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=1ad7dcd132509130f157cf5adf2df2c4",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"licenses\":[{\"id\":18,\"name\":\"asperiores18\",\"limits\":{\"schools\":\"100000000\",\"students\":\"100000000\",\"teachers\":\"100000000\",\"classrooms\":\"100000000\",\"disk_space\":\"100000000\"},\"usage\":{\"schools\":\"0\",\"students\":\"0\",\"teachers\":\"0\",\"classrooms\":\"0\",\"disk_space\":\"0\"},\"expiry\":\"2017-10-03T15:48:44.022Z\",\"purchasing_contact_info\":{\"city\":\"Toronto\",\"email\":\"asperiores18@pivotallabs.fake\",\"address\":\"69 Yonge St.\",\"country\":\"Canada\",\"last_name\":\"Goyette\",\"first_name\":\"Viviane\",\"postal_code\":\"M5S 2L9\",\"country_code\":\"CA\",\"phone_number\":\"14161112222\",\"phone_extension\":\"1234\"}},{\"id\":17,\"name\":\"aut17\",\"limits\":{\"schools\":\"100000000\",\"students\":\"100000000\",\"teachers\":\"100000000\",\"classrooms\":\"100000000\",\"disk_space\":\"100000000\"},\"usage\":{\"schools\":\"0\",\"students\":\"0\",\"teachers\":\"0\",\"classrooms\":\"0\",\"disk_space\":\"0\"},\"expiry\":\"2017-10-03T15:48:44.010Z\",\"purchasing_contact_info\":{\"city\":\"Toronto\",\"email\":\"aut17@pivotallabs.fake\",\"address\":\"69 Yonge St.\",\"country\":\"Canada\",\"last_name\":\"Christiansen\",\"first_name\":\"Stefan\",\"postal_code\":\"M5S 2L9\",\"country_code\":\"CA\",\"phone_number\":\"14161112222\",\"phone_extension\":\"1234\"}},{\"id\":16,\"name\":\"esse16\",\"limits\":{\"schools\":\"100000000\",\"students\":\"100000000\",\"teachers\":\"100000000\",\"classrooms\":\"100000000\",\"disk_space\":\"100000000\"},\"usage\":{\"schools\":\"0\",\"students\":\"0\",\"teachers\":\"0\",\"classrooms\":\"0\",\"disk_space\":\"0\"},\"expiry\":\"2017-10-03T15:48:43.910Z\",\"purchasing_contact_info\":{\"city\":\"Toronto\",\"email\":\"esse16@pivotallabs.fake\",\"address\":\"69 Yonge St.\",\"country\":\"Canada\",\"last_name\":\"Lynch\",\"first_name\":\"Jasper\",\"postal_code\":\"M5S 2L9\",\"country_code\":\"CA\",\"phone_number\":\"14161112222\",\"phone_extension\":\"1234\"}}],\"total_count\":3}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"8a9acbd9d9d8d1befc9af4d098a0db1a\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "1c9ad5f1-2204-4a09-b9eb-c2bb189b8ee3",
    "X-Runtime": "0.107630",
    "Content-Length": "1676"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/licenses/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer



## Get a License's List of Admins


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/licenses/38/purchasing-admins",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=1ad7dcd132509130f157cf5adf2df2c4",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":144,\"first_name\":\"Myrl\",\"last_name\":\"Durgan\",\"is_archived\":false,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin8\",\"email\":\"test9993@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":143,\"first_name\":\"Jeanette\",\"last_name\":\"Christiansen\",\"is_archived\":false,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin7\",\"email\":\"test9992@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"}],\"total_count\":2}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"9fb79a9981c2d7d381afe7853cf46eca\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "e621f296-3ce1-4eeb-aa64-33a57536e64d",
    "X-Runtime": "0.045535",
    "Content-Length": "489"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/licenses/38/purchasing-admins`



## Get an Active Users Own License


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/licenses/current",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=26b390512585aba3c91ab411e0b36e08",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"license\":{\"id\":37,\"is_pearson\":false,\"secret_key\":\"48577733d8a3dfaf6d359de24fdb5053\",\"name\":\"fugit41\",\"languages\":[\"en\"],\"default_language_code\":\"en\",\"limits\":{\"schools\":\"100000000\",\"students\":\"100000000\",\"teachers\":\"100000000\",\"classrooms\":\"100000000\",\"disk_space\":\"100000000\"},\"usage\":{\"schools\":\"0\",\"students\":\"0\",\"teachers\":\"1\",\"classrooms\":\"0\",\"disk_space\":\"0\"},\"expiry\":\"2017-10-03T15:48:45.701Z\",\"purchasing_contact_info\":{\"city\":\"Toronto\",\"email\":\"fugit41@pivotallabs.fake\",\"address\":\"69 Yonge St.\",\"country\":\"Canada\",\"last_name\":\"Leuschke\",\"first_name\":\"Dusty\",\"postal_code\":\"M5S 2L9\",\"country_code\":\"CA\",\"phone_number\":\"14161112222\",\"phone_extension\":\"1234\"},\"curriculum_ids\":[61,62],\"group_assessment\":false}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/licenses/37",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"21580f6fcce203c3b4b6fe6879abe044\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "3064531b-9784-47d2-bdf1-faf326acedec",
    "X-Runtime": "0.032563",
    "Content-Length": "722"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/licenses/current`




# Local Admins


## Create a Local Admin


> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/local-admins",
  "request_body": "user[license_id]=61&user[username]=test6452&user[email]=test10170%40pivotallabs.com&user[first_name]=Wayne&user[last_name]=Batz&user[type]=LocalAdmin&user[country_code]=CA&user[language_code]=en&user[public_id]=3854548&user[phone_number]=14163334444&user[phone_extension]=55555",
  "request_headers": {
    "Authorization": "Token token=791a649088affc0b44cab1fbf8c7b1ba",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"user\":{\"id\":309,\"type\":\"LocalAdmin\",\"username\":\"test6452\",\"email\":\"test10170@pivotallabs.com\",\"first_name\":\"Wayne\",\"last_name\":\"Batz\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":61,\"language_code\":\"en\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/local-admins/309",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"9031c3785d37ceb7a49383a945b953f4\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "0d636ddc-e9f0-463f-89a2-09f53efbfb13",
    "X-Runtime": "0.078431",
    "Content-Length": "295"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/local-admins`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
license_id | false | integer
username | true | string
email | true | string
password | false | string
password_confirmation | false | string
first_name | false | string
last_name | false | string
country_code | false | string
phone_number | false | string
phone_extension | false | string
public_id | false | string



## Show a Local Admin


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/local-admins/299?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=791a649088affc0b44cab1fbf8c7b1ba",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"user\":{\"id\":299,\"type\":\"LocalAdmin\",\"username\":\"local_admin2547\",\"email\":\"test10160@pivotallabs.com\",\"first_name\":\"Zackery\",\"last_name\":\"Stoltenberg\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":61,\"language_code\":\"en\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"ed2bd692f28ff6918721bed2fd2a2932\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "732b7e3c-6415-4ba2-a3aa-ed1b7baa5970",
    "X-Runtime": "0.044298",
    "Content-Length": "299"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/local-admins/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | false | array of options (Options: schools, classrooms, teacher_count, student_count)



## Show a List Local Admins


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/local-admins?include=[]&per_page=9",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=791a649088affc0b44cab1fbf8c7b1ba",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]",
    "per_page": "9"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":307,\"first_name\":\"Lucile\",\"last_name\":\"Gaylord\",\"is_archived\":true,\"type\":\"LocalAdmin\",\"username\":\"local_admin2555\",\"email\":\"test10168@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":306,\"first_name\":\"Candelario\",\"last_name\":\"Doyle\",\"is_archived\":true,\"type\":\"LocalAdmin\",\"username\":\"local_admin2554\",\"email\":\"test10167@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":305,\"first_name\":\"Charley\",\"last_name\":\"Stroman\",\"is_archived\":true,\"type\":\"LocalAdmin\",\"username\":\"local_admin2553\",\"email\":\"test10166@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":304,\"first_name\":\"Cordelia\",\"last_name\":\"Lesch\",\"is_archived\":true,\"type\":\"LocalAdmin\",\"username\":\"local_admin2552\",\"email\":\"test10165@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":303,\"first_name\":\"Davon\",\"last_name\":\"Huel\",\"is_archived\":false,\"type\":\"LocalAdmin\",\"username\":\"local_admin2551\",\"email\":\"test10164@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":302,\"first_name\":\"Bertrand\",\"last_name\":\"Howe\",\"is_archived\":false,\"type\":\"LocalAdmin\",\"username\":\"local_admin2550\",\"email\":\"test10163@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":301,\"first_name\":\"Gianni\",\"last_name\":\"Hagenes\",\"is_archived\":false,\"type\":\"LocalAdmin\",\"username\":\"local_admin2549\",\"email\":\"test10162@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":300,\"first_name\":\"Jett\",\"last_name\":\"Hammes\",\"is_archived\":false,\"type\":\"LocalAdmin\",\"username\":\"local_admin2548\",\"email\":\"test10161@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":299,\"first_name\":\"Zackery\",\"last_name\":\"Stoltenberg\",\"is_archived\":false,\"type\":\"LocalAdmin\",\"username\":\"local_admin2547\",\"email\":\"test10160@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"}],\"total_count\":9}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"ee6ea6b192605aa05b808cae45d54177\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "e0bb5c28-6707-4965-ace8-91c3247ed8ad",
    "X-Runtime": "0.156212",
    "Content-Length": "2030"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/local-admins/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
show_archived | false | boolean
exclude_ids | false | array
include | false | array of options (Options: schools, classrooms, teacher_count, student_count)



# Notes


## Create a Document Note


> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/notes",
  "request_body": "note[category]=other&note[title]=Random+title&note[content]=This+is+a+note&note[document_id]=75",
  "request_headers": {
    "Authorization": "Token token=d184ba3a3c78e1125373421f20dcf5be",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"note\":{\"id\":72,\"title\":\"Random title\",\"category\":\"other\",\"content\":\"This is a note\",\"document_id\":75,\"student_ids\":[],\"created_at\":\"2016-10-03T15:49:01.376Z\",\"creator\":{\"id\":180,\"first_name\":\"Beverly\",\"last_name\":\"Buckridge\"}},\"students\":[]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/notes/72",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"560239a4c12ca6654bf90cb1e8e9388f\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "7bb4c1bd-55e9-4ae8-a2fa-f50761d33224",
    "X-Runtime": "0.092613",
    "Content-Length": "243"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/notes`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
category | true | string
title | true | string
content | true | string
student_id | false | integer
document_id | false | integer



## Delete a Note


> Example request & response:

```json
{
  "request_method": "DELETE",
  "request_path": "/api/v2/notes/79",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=d184ba3a3c78e1125373421f20dcf5be",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 204,
  "response_status_text": "No Content",
  "response_body": null,
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Cache-Control": "no-cache",
    "X-Request-Id": "c241132c-fcb2-4743-9ca7-be7536cbde5d",
    "X-Runtime": "0.042444"
  },
  "response_content_type": null,
  "curl": null
}
```


### HTTP Request

`DELETE /api/v2/notes/:id`


## Show a Note


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/notes/66",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=d184ba3a3c78e1125373421f20dcf5be",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"note\":{\"id\":66,\"title\":\"Sit quo vel debitis consequatur eos aut facere officiis.\",\"category\":\"other\",\"content\":\"Quam autem non magni alias. Consectetur commodi illo aut recusandae quisquam. Itaque sit est qui consequatur. Rerum ea sit est earum ex. Cupiditate vel quia harum. Amet officiis et quia nam repudiandae dicta laborum. Excepturi aut autem enim sint dolor. Omnis nobis dicta nostrum sit. Sit id et. Ut dolorem ratione atque. Ut aperiam voluptatem illum labore.\",\"document_id\":null,\"student_ids\":[],\"created_at\":\"2016-10-03T15:49:00.042Z\",\"creator\":{\"id\":180,\"first_name\":\"Beverly\",\"last_name\":\"Buckridge\"},\"student\":{\"id\":178,\"first_name\":\"Gunner\",\"last_name\":\"Terry\"}},\"students\":[]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"6e57e16e4e3e2fd49f4a5d4ad42997d8\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "48b56f36-6a88-41bd-b54c-a5d098fd0eda",
    "X-Runtime": "0.120908",
    "Content-Length": "695"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/notes/:id`



## Update a Note


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/notes/75",
  "request_body": "note[category]=other&note[title]=New+title&note[content]=This+is+an+updated+note",
  "request_headers": {
    "Authorization": "Token token=d184ba3a3c78e1125373421f20dcf5be",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"note\":{\"id\":75,\"title\":\"New title\",\"category\":\"other\",\"content\":\"This is an updated note\",\"document_id\":null,\"student_ids\":[],\"created_at\":\"2016-10-03T15:49:01.547Z\",\"creator\":{\"id\":180,\"first_name\":\"Beverly\",\"last_name\":\"Buckridge\"}},\"students\":[]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/notes/75",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "16f327e8-7f9d-4d22-85f0-be941365a98b",
    "X-Runtime": "0.092257",
    "Content-Length": "251"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/notes/:id`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
category | true | string
title | true | string
content | true | string
student_id | false | integer
document_id | false | integer



## Show a List of Notes


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/notes?student_id=178",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=d184ba3a3c78e1125373421f20dcf5be",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "student_id": "178"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"notes\":[{\"id\":57,\"title\":\"Aut autem eum est molestiae ut qui inventore.\",\"category\":\"opportunity\",\"content\":\"Esse occaecati nemo officiis autem reiciendis sit. In non veniam reiciendis animi earum. Error odio ut quibusdam. Totam fugiat ducimus. Temporibus sed cumque est dolorum minima est. Aut minima nisi debitis est saepe amet. Autem magni quod soluta et. Cupiditate nam nostrum corporis fugiat aspernatur. Velit iusto fugit consequatur necessitatibus. Unde saepe quibusdam qui nostrum. Aliquid veritatis aut consequatur vel quas. Iure enim alias.\",\"created_at\":\"2016-10-03T15:48:59.292Z\"},{\"id\":56,\"title\":\"Aperiam aut ut maiores dolore et occaecati perferendis.\",\"category\":\"observation\",\"content\":\"Pariatur aperiam et veritatis cupiditate. Adipisci nihil tempora. Magnam illum earum voluptatem voluptatem sit voluptatem eligendi. Est ipsa similique officia. Voluptates iusto occaecati autem non. Ipsum nihil expedita voluptates. Ea dolorem dicta veniam et rem alias animi. Accusamus aut quo quos alias. Fuga reiciendis ea repellat fugit ratione. Doloribus necessitatibus sit dignissimos blanditiis.\",\"created_at\":\"2016-10-03T15:48:59.264Z\"},{\"id\":53,\"title\":\"Facere iure fuga possimus voluptatem magni cum qui error tenetur est.\",\"category\":\"observation\",\"content\":\"Animi id sunt aut aut enim accusamus maiores. Sunt maiores doloremque id id a. Dignissimos enim laudantium est itaque. Laboriosam animi repellat voluptatem. Debitis sed ex eum quas et occaecati. Sed consectetur voluptas. Quod saepe doloremque. Voluptatem enim cum. Voluptas natus quia. Corporis nostrum soluta tempora et. Illum repudiandae repellendus sit et rerum nostrum accusantium. Consequatur occaecati reiciendis aut id.\",\"created_at\":\"2016-10-03T15:48:58.989Z\"},{\"id\":52,\"title\":\"Accusamus voluptatem autem repudiandae velit aliquid nam reprehenderit officiis.\",\"category\":\"reflection\",\"content\":\"Est praesentium dolorem officiis quas ratione. Doloremque commodi ab consequatur itaque. Quis maxime rerum consequatur. Fugit nisi rerum. Ut a aliquid voluptas sapiente consequuntur consequatur. Nihil non illum ut totam accusantium aut ab. Maxime aut atque quaerat similique. Mollitia recusandae tempore. Quibusdam quaerat deserunt. Exercitationem mollitia autem et doloremque reiciendis. Rerum rerum occaecati facilis laudantium. Maiores nemo accusamus aut veritatis consequatur voluptatem.\",\"created_at\":\"2016-10-03T15:48:58.983Z\"},{\"id\":51,\"title\":\"Distinctio inventore aut odio non est sint sit at officiis qui.\",\"category\":\"other\",\"content\":\"Voluptatem suscipit accusamus autem. Sed et rerum consequatur libero ut. Corporis sit placeat excepturi a eos dolor. Possimus voluptas ab molestias nostrum aliquam quis ut. Non omnis aut ut. Voluptas velit dolores et eveniet. Est mollitia aspernatur quidem. Expedita quam minima unde et dolorem facere perspiciatis. Amet dolor corrupti et mollitia. Asperiores sapiente quia voluptas sed in. Sit repellat velit suscipit laboriosam.\",\"created_at\":\"2016-10-03T15:48:58.972Z\"}],\"total_count\":5}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"c666edbc23ba6796362af9c4b21e19f2\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "74761879-4bba-4e55-9ebf-776b9e85b668",
    "X-Runtime": "0.048484",
    "Content-Length": "3015"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/notes`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
student_id | false | integer
order | false | json_object
keyword | false | string




# Purchasing Admins


## Create a Purchasing Admin


> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/purchasing-admins",
  "request_body": "user[license_id]=65&user[username]=test6459&user[email]=test10209%40pivotallabs.com&user[first_name]=Kyle&user[last_name]=Cronin&user[type]=PurchasingAdmin&user[country_code]=CA&user[language_code]=en&user[public_id]=877911&user[phone_number]=14163334444&user[phone_extension]=55555",
  "request_headers": {
    "Authorization": "Token token=8696def39f9e18729c871e7cfd42ed41",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"user\":{\"id\":343,\"type\":\"PurchasingAdmin\",\"username\":\"test6459\",\"email\":\"test10209@pivotallabs.com\",\"first_name\":\"Kyle\",\"last_name\":\"Cronin\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":65,\"language_code\":\"en\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/purchasing-admins/343",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"ba62ddae1b09737c8eeb37a0237fce8b\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "b15cca2c-7fa6-4e12-8a3e-291ce145268b",
    "X-Runtime": "0.086611",
    "Content-Length": "301"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/purchasing-admins`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
license_id | false | integer
username | true | string
email | true | string
password | false | string
password_confirmation | false | string
first_name | false | string
last_name | false | string
country_code | false | string
phone_number | false | string
phone_extension | false | string
public_id | false | string



## Show a Purchasing Admin


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/purchasing-admins/333?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=8696def39f9e18729c871e7cfd42ed41",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"user\":{\"id\":333,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin20\",\"email\":\"test10199@pivotallabs.com\",\"first_name\":\"Dario\",\"last_name\":\"Jacobson\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":65,\"language_code\":\"en\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"08c17bb356fa133db0cc42817ef11fae\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "3a614d8a-2df7-45e1-94da-2c227ad4b4a3",
    "X-Runtime": "0.046942",
    "Content-Length": "302"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/purchasing-admins/:id`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | false | array of options (Options: schools, classrooms, teacher_count, student_count)



## Show a List Purchasing Admins


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/purchasing-admins?include=[]&per_page=9",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=8696def39f9e18729c871e7cfd42ed41",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]",
    "per_page": "9"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":341,\"first_name\":\"Christa\",\"last_name\":\"Heidenreich\",\"is_archived\":true,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin28\",\"email\":\"test10207@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":340,\"first_name\":\"Sherman\",\"last_name\":\"Herzog\",\"is_archived\":true,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin27\",\"email\":\"test10206@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":339,\"first_name\":\"Joan\",\"last_name\":\"Schowalter\",\"is_archived\":true,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin26\",\"email\":\"test10205@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":338,\"first_name\":\"Maybell\",\"last_name\":\"Eichmann\",\"is_archived\":true,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin25\",\"email\":\"test10204@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":337,\"first_name\":\"Rhianna\",\"last_name\":\"Dare\",\"is_archived\":false,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin24\",\"email\":\"test10203@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":336,\"first_name\":\"Herta\",\"last_name\":\"Kilback\",\"is_archived\":false,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin23\",\"email\":\"test10202@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":335,\"first_name\":\"Ayla\",\"last_name\":\"Emard\",\"is_archived\":false,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin22\",\"email\":\"test10201@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":334,\"first_name\":\"Charley\",\"last_name\":\"Wuckert\",\"is_archived\":false,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin21\",\"email\":\"test10200@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":333,\"first_name\":\"Dario\",\"last_name\":\"Jacobson\",\"is_archived\":false,\"type\":\"PurchasingAdmin\",\"username\":\"purchasing_admin20\",\"email\":\"test10199@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"}],\"total_count\":9}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"3ec64cb0163ad53d981450f3d9db8385\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "f057ea22-9b0b-4fa1-a477-c89151774491",
    "X-Runtime": "0.094409",
    "Content-Length": "2104"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/purchasing-admins`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
show_archived | false | boolean
include | false | array of options (Options: school_count, classroom_count, status)
exclude_ids | false | array of purchasing admin ids



# Schools


## Create a School


> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/schools",
  "request_body": "school[curriculum_ids][]=75&school[curriculum_ids][]=76&school[type]=School&school[total_disk_space]=0&school[used_disk_space]=0&school[public_id]=4303237&school[teacher_ids][]=221&school[teacher_ids][]=222&school[student_ids][]=223&school[student_ids][]=224&school[local_admin_ids][]=225&school[name]=Doloremque+Libero+Qui+Quibusdam+Consequatur+Suscipit+Architecto+Temporibus+Quisquam+Omnis+In.",
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"school\":{\"id\":127,\"public_id\":\"4303237\",\"local_admin_ids\":[225],\"teacher_ids\":[221,222],\"student_ids\":[223,224],\"name\":\"Doloremque Libero Qui Quibusdam Consequatur Suscipit Architecto Temporibus Quisquam Omnis In.\",\"curriculum_ids\":[75,76],\"license_id\":49,\"is_archived\":false,\"total_disk_space\":0,\"used_disk_space\":0}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/schools/127",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"bf219c1fb59750ae150ec44b607ac0f4\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "6106996b-bc32-4508-bdca-40858c62037a",
    "X-Runtime": "0.137850",
    "Content-Length": "320"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/schools`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
teacher_ids | false | array of integers
student_ids | false | array of integers
name | true | string
curriculum_ids | true | array of integers
license_id | true | integer
total_disk_space | false | integer



## Delete a School


> Example request & response:

```json
{
  "request_method": "DELETE",
  "request_path": "/api/v2/schools/95",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=ff43e4852dc5979f6739e34427450a27",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 204,
  "response_status_text": "No Content",
  "response_body": null,
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Cache-Control": "no-cache",
    "X-Request-Id": "807092ec-f5b5-4f90-af7f-8f5f3664aac0",
    "X-Runtime": "0.338927"
  },
  "response_content_type": null,
  "curl": null
}
```


### HTTP Request

`DELETE /api/v2/schools/:id`



## Show a School


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/schools/106?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"school\":{\"id\":106,\"public_id\":\"7028133\",\"local_admin_ids\":[210],\"teacher_ids\":[206,207],\"student_ids\":[208,209],\"name\":\"Possimus Eveniet Neque Consequatur Pariatur Rerum.\",\"curriculum_ids\":[75,76],\"license_id\":49,\"is_archived\":false,\"total_disk_space\":0,\"used_disk_space\":0}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"bcc0b0ee6d5934767c8d86a7fd3602fb\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "e2632b79-37e0-4852-9d3c-7177c646183b",
    "X-Runtime": "0.080305",
    "Content-Length": "277"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/schools/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | false | array of options (Options: classrooms, curriculums)



## Update a School


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/schools/129",
  "request_body": "school[curriculum_ids][]=75&school[curriculum_ids][]=76&school[type]=School&school[public_id]=4303237&school[teacher_ids][]=221&school[teacher_ids][]=222&school[student_ids][]=223&school[student_ids][]=224&school[local_admin_ids][]=225&school[name]=Sint+Eaque+Possimus+Totam+Ipsum+Eius+Consequuntur+Quam+Culpa+Quidem+Reprehenderit.",
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"school\":{\"id\":129,\"public_id\":\"4303237\",\"local_admin_ids\":[225],\"teacher_ids\":[221,222],\"student_ids\":[223,224],\"name\":\"Sint Eaque Possimus Totam Ipsum Eius Consequuntur Quam Culpa Quidem Reprehenderit.\",\"curriculum_ids\":[75,76],\"license_id\":49,\"is_archived\":false,\"total_disk_space\":1,\"used_disk_space\":0}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/schools/129",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "3cb7b1f8-2fde-4e65-b95c-de8de5d42ebf",
    "X-Runtime": "0.117380",
    "Content-Length": "309"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/schools/:id`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
teacher_ids | false | array of integers
student_ids | false | array of integers
name | false | string
curriculum_ids | true | array of integers
total_disk_space | false | integer



## Add or Remove Local Admins from a School


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/schools/106/update-local-admins",
  "request_body": "school[add_ids][]=234",
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"school\":{\"id\":106,\"public_id\":\"7028133\",\"local_admin_ids\":[210,234],\"teacher_ids\":[207,206,233],\"student_ids\":[208,209,232],\"name\":\"Possimus Eveniet Neque Consequatur Pariatur Rerum.\",\"curriculum_ids\":[75,76],\"license_id\":49,\"is_archived\":false,\"total_disk_space\":0,\"used_disk_space\":0}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/schools/106",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "6c54c1dd-bde9-41ad-8432-5c7a149f3465",
    "X-Runtime": "0.126832",
    "Content-Length": "289"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/schools/:id/update-local-admins`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
remove_ids | false | array
add_ids | false | array


## Add or Remove Students from a School


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/schools/106/update-students",
  "request_body": "school[add_ids][]=232",
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"school\":{\"id\":106,\"public_id\":\"7028133\",\"local_admin_ids\":[210],\"teacher_ids\":[206,207],\"student_ids\":[208,209,232],\"name\":\"Possimus Eveniet Neque Consequatur Pariatur Rerum.\",\"curriculum_ids\":[75,76],\"license_id\":49,\"is_archived\":false,\"total_disk_space\":0,\"used_disk_space\":0}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/schools/106",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "30a85d9c-8132-4a31-b85c-36bf4ab8ae22",
    "X-Runtime": "0.100553",
    "Content-Length": "281"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/schools/:id/update-students`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
remove_ids | false | array
add_ids | false | array


## Add or Remove Teachers from a School


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/schools/106/update-teachers",
  "request_body": "school[add_ids][]=233",
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"school\":{\"id\":106,\"public_id\":\"7028133\",\"local_admin_ids\":[210],\"teacher_ids\":[207,206,233],\"student_ids\":[208,209,232],\"name\":\"Possimus Eveniet Neque Consequatur Pariatur Rerum.\",\"curriculum_ids\":[75,76],\"license_id\":49,\"is_archived\":false,\"total_disk_space\":0,\"used_disk_space\":0}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/schools/106",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "7993ec76-94e5-42ab-a035-4014cf377397",
    "X-Runtime": "0.120193",
    "Content-Length": "285"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/schools/:id/update-teachers`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
remove_ids | false | array
add_ids | false | array




## Show a List of Schools


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/schools",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"schools\":[{\"id\":115,\"name\":\"Vero Temporibus Voluptas Qui Laborum Tempore.\",\"is_archived\":true,\"classroom_count\":0,\"teacher_count\":0,\"student_count\":0},{\"id\":114,\"name\":\"Iure Quisquam Laborum Amet Porro Harum Non.\",\"is_archived\":true,\"classroom_count\":0,\"teacher_count\":0,\"student_count\":0},{\"id\":113,\"name\":\"Perspiciatis Sed Numquam Repellendus Et Rem.\",\"is_archived\":true,\"classroom_count\":0,\"teacher_count\":0,\"student_count\":0},{\"id\":108,\"name\":\"Veniam Et Neque Facere Sed Necessitatibus Temporibus Fuga Quis.\",\"is_archived\":false,\"classroom_count\":0,\"teacher_count\":2,\"student_count\":2},{\"id\":107,\"name\":\"Exercitationem Expedita Tempora Quidem Amet Culpa Impedit Libero Unde.\",\"is_archived\":false,\"classroom_count\":0,\"teacher_count\":2,\"student_count\":2},{\"id\":106,\"name\":\"Possimus Eveniet Neque Consequatur Pariatur Rerum.\",\"is_archived\":false,\"classroom_count\":2,\"teacher_count\":2,\"student_count\":2}],\"total_count\":6}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"3ef2af86d587e797e8bd04aa5b1e80e5\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "fe6a8c71-97c2-4bce-ba7b-25c79b1fc488",
    "X-Runtime": "0.090635",
    "Content-Length": "923"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/schools`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
exclude_ids | false | array
license_id | false | integer
order | false | json_object



## Show a School's Students


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/schools/106/students?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":209,\"first_name\":\"Haylie\",\"last_name\":\"Tremblay\",\"is_archived\":false,\"has_consent\":false,\"birthday\":\"2001-10-03T15:49:11.162Z\",\"grade_level\":10,\"public_id\":\"3330395\"},{\"id\":208,\"first_name\":\"Rosalyn\",\"last_name\":\"Becker\",\"is_archived\":false,\"has_consent\":false,\"birthday\":\"2001-10-03T15:49:11.125Z\",\"grade_level\":11,\"public_id\":\"3816890\"}],\"total_count\":2}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"8ce259388dfc77aaec9bddfeede32a51\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "253c8458-696d-4c0f-9d5c-51acd6de0747",
    "X-Runtime": "0.055666",
    "Content-Length": "372"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/schools/:id/students`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
exclude_ids | false | array
include | false | array of options (Options: school_count, classroom_count, status)




## Show a School's Teachers


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/schools/106/teachers?include=%23%3CRSpec%3A%3AMatchers%3A%3ABuiltIn%3A%3AInclude%3A0x007f04627bb9f8%3E",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=4ce30cf1bab0176a99a61c39c2f8efb2",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "#<RSpec::Matchers::BuiltIn::Include:0x007f04627bb9f8>"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":207,\"first_name\":\"Myron\",\"last_name\":\"Lakin\",\"is_archived\":false,\"type\":\"Teacher\",\"username\":\"teacher90\",\"email\":\"test10058@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":206,\"first_name\":\"Hailee\",\"last_name\":\"Bosco\",\"is_archived\":false,\"type\":\"Teacher\",\"username\":\"teacher89\",\"email\":\"test10057@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"}],\"total_count\":2}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"6f5cafc47d011d2c40174eebccd25870\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "b4622b3f-30fd-4db6-9908-853dd2ce99d0",
    "X-Runtime": "0.052468",
    "Content-Length": "450"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/schools/:id/teachers`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
exclude_ids | false | array
include | false | array of options (Options: school_count, classroom_count, status)


# Strands


## Show a Strand


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/strands/79",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=5b13774251dad608dfaa96f74b135638",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"strand\":{\"id\":79,\"level_name\":\"Curriculum\",\"description\":\"Province 38\",\"grade_level\":8,\"year\":1963,\"depth\":0,\"assessment_depth\":2,\"children\":[{\"id\":80,\"level_name\":\"Learning Area\",\"description\":\"Et consequatur aut laboriosam cumque aliquid. Optio ratione quas voluptas laboriosam.\",\"color\":\"#FFFFFF\",\"depth\":1,\"children\":[{\"id\":82,\"level_name\":\"Overall Expectation\",\"description\":\"Repudiandae libero cumque.\",\"color\":null,\"depth\":2,\"children\":[{\"id\":84,\"level_name\":\"Specific Expectation\",\"description\":\"Ut sit aut. Non aut dolores architecto reprehenderit consequatur.\",\"color\":null,\"depth\":3,\"children\":[]},{\"id\":85,\"level_name\":\"Specific Expectation\",\"description\":\"Totam et ipsa qui. Non quas quaerat inventore. Qui voluptates nobis.\",\"color\":null,\"depth\":3,\"children\":[]}],\"at_assessment_depth\":true},{\"id\":83,\"level_name\":\"Overall Expectation\",\"description\":\"Est rerum temporibus doloremque. Exercitationem rerum voluptates nesciunt placeat.\",\"color\":null,\"depth\":2,\"children\":[{\"id\":86,\"level_name\":\"Specific Expectation\",\"description\":\"Dicta maiores recusandae repudiandae. Magni omnis in tempore a pariatur. Aperiam perferendis blanditiis.\",\"color\":null,\"depth\":3,\"children\":[]},{\"id\":87,\"level_name\":\"Specific Expectation\",\"description\":\"Magnam delectus distinctio itaque tempore iure. Suscipit fugiat et quia omnis perferendis corrupti omnis.\",\"color\":null,\"depth\":3,\"children\":[]}],\"at_assessment_depth\":true}]},{\"id\":81,\"level_name\":\"Learning Area\",\"description\":\"Vitae quia excepturi. Consectetur velit consequatur.\",\"color\":\"#FFFFFF\",\"depth\":1,\"children\":[{\"id\":88,\"level_name\":\"Overall Expectation\",\"description\":\"Quia eaque beatae rem inventore dicta qui incidunt. Expedita corporis et atque.\",\"color\":null,\"depth\":2,\"children\":[{\"id\":90,\"level_name\":\"Specific Expectation\",\"description\":\"Voluptas molestiae necessitatibus voluptatem tenetur harum ipsum. Modi provident rerum dolores dignissimos amet. Odio vel animi doloribus occaecati.\",\"color\":null,\"depth\":3,\"children\":[]},{\"id\":91,\"level_name\":\"Specific Expectation\",\"description\":\"Aut eligendi deleniti. Ut id nobis libero accusamus dolorum aut hic. Non et est sint et.\",\"color\":null,\"depth\":3,\"children\":[]}],\"at_assessment_depth\":true},{\"id\":89,\"level_name\":\"Overall Expectation\",\"description\":\"Tempora in architecto culpa debitis rerum ducimus et.\",\"color\":null,\"depth\":2,\"children\":[{\"id\":92,\"level_name\":\"Specific Expectation\",\"description\":\"Dolorem eos provident occaecati esse non corporis. Voluptatibus magni iusto et doloribus officia.\",\"color\":null,\"depth\":3,\"children\":[]},{\"id\":93,\"level_name\":\"Specific Expectation\",\"description\":\"Ut deserunt rem occaecati animi. Ut aut sunt.\",\"color\":null,\"depth\":3,\"children\":[]}],\"at_assessment_depth\":true}]}]}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"d78ee389d2b810977a5d06a48cdbe21c\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "79a9e244-e76c-4541-8b79-964beace812b",
    "X-Runtime": "0.117058",
    "Content-Length": "2737"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/strands/:id`



## Show a List of Strands


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/strands?include=[]&grade_level=8&description=Ontario+-+Private&assessment_depth=2",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=5b13774251dad608dfaa96f74b135638",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]",
    "grade_level": "8",
    "description": "Ontario - Private",
    "assessment_depth": "2"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"strands\":[{\"id\":95,\"level_name\":\"Curriculum\",\"description\":\"Ontario - Private\",\"grade_level\":8,\"year\":1963,\"depth\":0,\"assessment_depth\":2,\"max_depth\":3}],\"total_count\":1}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"1049a9c2b90134900fc5e42db1e821eb\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "256b442f-09e6-4950-b9cc-eda0638adef6",
    "X-Runtime": "0.279169",
    "Content-Length": "172"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/strands`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
grade | false | string
description | false | string
level_name | false | string (defaults to \"Curriculum\")
page | false | integer
per_page | false | integer
school_id | false | integer
classroom_id | false | integer
include | false | array of options (Options: marking_scheme)



## Show a Strands Color Scheme


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/strands/79/color-scheme",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=5b13774251dad608dfaa96f74b135638",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"color_scheme\":[{\"strand\":\"Et consequatur aut laboriosam cumque aliquid. Optio ratione quas voluptas laboriosam.\",\"color\":\"#FFFFFF\"},{\"strand\":\"Vitae quia excepturi. Consectetur velit consequatur.\",\"color\":\"#FFFFFF\"}]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"e10062b90878272b5a25d7cdd3ef0b25\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "e51318ab-22cc-4c7c-a696-0781eca9fd35",
    "X-Runtime": "0.073091",
    "Content-Length": "219"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/strands/:id/color-scheme`



## Show a Strands Marking Scheme


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/strands/79/marking-scheme",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=5b13774251dad608dfaa96f74b135638",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"marking_scheme\":[{\"label\":\"BD\",\"details\":\"Beginning to Develop\"},{\"label\":\"D\",\"details\":\"Develop\"},{\"label\":\"WD\",\"details\":\"Well Developed\"}]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"072f50ae6555fc044213f0ec9c0f86af\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "7b20a98f-3e07-44a7-b36f-c9417039be18",
    "X-Runtime": "0.091428",
    "Content-Length": "144"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/strands/:id/marking-scheme`



## Show Assessment Summary for a Classroom


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/strands/79/summary?classroom_id=132",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=5b13774251dad608dfaa96f74b135638",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "classroom_id": "132"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"summary\":[{\"student_id\":238,\"student_name\":\"Nicolas Leffler\",\"grade_level\":7,\"assessment_count\":{\"80\":1}},{\"student_id\":239,\"student_name\":\"Aimee Beier\",\"grade_level\":5,\"assessment_count\":{}}],\"max_assessment_count\":1,\"strands\":[{\"id\":80,\"level_name\":\"Learning Area\",\"description\":\"Et consequatur aut laboriosam cumque aliquid. Optio ratione quas voluptas laboriosam.\",\"color\":\"#FFFFFF\"},{\"id\":81,\"level_name\":\"Learning Area\",\"description\":\"Vitae quia excepturi. Consectetur velit consequatur.\",\"color\":\"#FFFFFF\"}]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"78caa1d225fdad15cda50c7132728569\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "afcea119-d607-43d1-aa93-66de4357c912",
    "X-Runtime": "0.131225",
    "Content-Length": "517"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/strands/:id/summary`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
classroom_id | true | integer
date | false | datetime
student_id | false | integer





# Students

## Create a Student


> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/students",
  "request_body": "user[license_id]=69&user[username]=test6468&user[email]=test10235%40pivotallabs.com&user[first_name]=Mavis&user[last_name]=Ankunding&user[type]=Student&user[country_code]=CA&user[language_code]=en&user[public_id]=34088&user[phone_number]=14163334444&user[phone_extension]=55555&user[birthday]=2003-12-14+15%3A49%3A50+UTC&user[has_consent]&user[comment_or_restriction]=Repudiandae+voluptas+nihil+quis+temporibus+recusandae+mollitia+vel+consequatur+porro+voluptatem.&user[grade_level]=9",
  "request_headers": {
    "Authorization": "Token token=534aa40bdc11bbf455bc269cbb406411",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"user\":{\"id\":364,\"type\":\"Student\",\"username\":\"test6468\",\"email\":\"test10235@pivotallabs.com\",\"first_name\":\"Mavis\",\"last_name\":\"Ankunding\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":68,\"language_code\":\"en\",\"birthday\":\"2003-12-14T15:49:50.000Z\",\"has_consent\":null,\"comment_or_restriction\":\"Repudiandae voluptas nihil quis temporibus recusandae mollitia vel consequatur porro voluptatem.\",\"grade_level\":9,\"primary_guardian_id\":null,\"guardian_ids\":[],\"public_id\":\"34088\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/students/364",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"7cd8b0b24fe4b445cd54b007a2b39dac\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "31febee1-8bdd-4f62-9aaf-25ddaa2f3b32",
    "X-Runtime": "0.185159",
    "Content-Length": "559"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/students`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | integer
password | false | string
password_confirmation | false | string
first_name | false | string
last_name | false | string
country_code | false | string
phone_number | false | string
phone_extension | false | string
birthday | false | datetime
has_consent | false | boolean
comment_or_restriction | false | text
grade_level | false | string
public_id | true | string
guardian_ids | false | array
primary_guardian_id | false | integer
public_id | false | string
student_id | true | integer



## Show a Student


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/students/356?include[]=guardians",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=534aa40bdc11bbf455bc269cbb406411",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include[]": "guardians"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"user\":{\"id\":356,\"type\":\"Student\",\"username\":\"student309\",\"email\":\"test10227@pivotallabs.com\",\"first_name\":\"Lorenzo\",\"last_name\":\"Casper\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":68,\"language_code\":\"en\",\"birthday\":\"2010-10-03T15:49:50.175Z\",\"has_consent\":false,\"comment_or_restriction\":null,\"grade_level\":0,\"primary_guardian_id\":null,\"guardian_ids\":[360],\"public_id\":\"4122430\"},\"guardians\":[{\"id\":360,\"first_name\":\"Lesley\",\"last_name\":\"Feeney\",\"email\":\"test10231@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"}]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"a25b74c92af11d2d0a8b2f95624c1ef5\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "5f1e7b72-8bc7-41eb-94ab-3f6314f63782",
    "X-Runtime": "0.067809",
    "Content-Length": "627"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/students/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | false | array of options (Options: guardians, notes)



## Update a Student


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/students/356/",
  "request_body": "user[license_id]=69&user[username]=test6469&user[email]=test10237%40pivotallabs.com&user[first_name]=Vern&user[last_name]=Schuppe&user[type]=Student&user[country_code]=CA&user[language_code]=en&user[public_id]=62277&user[phone_number]=14163334444&user[phone_extension]=55555&user[birthday]=2002-12-23+15%3A49%3A51+UTC&user[has_consent]=true&user[comment_or_restriction]=Impedit+numquam+ut+voluptatibus+sunt+aut+alias+sit+laborum+eos+quia.&user[grade_level]=9&user[primary_guardian_id]=365&user[guardian_ids][]=360&user[guardian_ids][]=365",
  "request_headers": {
    "Authorization": "Token token=534aa40bdc11bbf455bc269cbb406411",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"user\":{\"id\":356,\"type\":\"Student\",\"username\":\"test6469\",\"email\":\"test10237@pivotallabs.com\",\"first_name\":\"Vern\",\"last_name\":\"Schuppe\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":68,\"language_code\":\"en\",\"birthday\":\"2002-12-23T15:49:51.000Z\",\"has_consent\":true,\"comment_or_restriction\":\"Impedit numquam ut voluptatibus sunt aut alias sit laborum eos quia.\",\"grade_level\":9,\"primary_guardian_id\":365,\"guardian_ids\":[360,365],\"public_id\":\"62277\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/students/356",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "3c9a6eae-dad8-4137-884f-c003b90bcff1",
    "X-Runtime": "0.106952",
    "Content-Length": "534"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/students/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | integer
email | false | string
password | false | string
password_confirmation | false | string
first_name | false | string
last_name | false | string
country_code | false | string
phone_number | false | string
phone_extension | false | string
birthday | false | datetime
has_consent | false | boolean
comment_or_restriction | false | text
grade_level | false | string
public_id | true | string
guardian_ids | false | array
primary_guardian_id | false | integer
public_id | false | string
student_id | true | integer



## Add Notes to a Student


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/students/356/add-notes",
  "request_body": "student[note_ids][]=83",
  "request_headers": {
    "Authorization": "Token token=5991197389b39c10f2aa62e60f28e085",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"user\":{\"id\":356,\"type\":\"Student\",\"username\":\"test6469\",\"email\":\"test10237@pivotallabs.com\",\"first_name\":\"Vern\",\"last_name\":\"Schuppe\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":68,\"language_code\":\"en\",\"birthday\":\"2002-12-23T15:49:51.000Z\",\"has_consent\":true,\"comment_or_restriction\":\"Impedit numquam ut voluptatibus sunt aut alias sit laborum eos quia.\",\"grade_level\":9,\"primary_guardian_id\":365,\"guardian_ids\":[360,365],\"public_id\":\"62277\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/students/356",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "92e9b9cf-7413-4e8f-a141-de5f057da91a",
    "X-Runtime": "0.074827",
    "Content-Length": "534"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/students/:id/add-notes`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
note_ids | false | array




## Add or Remove Student from a Classroom


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/students/356/update-classrooms",
  "request_body": "user[add_ids][]=148",
  "request_headers": {
    "Authorization": "Token token=534aa40bdc11bbf455bc269cbb406411",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": " ",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json",
    "Cache-Control": "no-cache",
    "X-Request-Id": "f937814a-6542-4051-9336-d47f6ee7d2d5",
    "X-Runtime": "0.347834",
    "Content-Length": "1"
  },
  "response_content_type": "application/json",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/students/:id/update-classrooms`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
add_ids | false | array
remove_ids | false | array


## Add or Remove Student from a School


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/students/356/update-schools",
  "request_body": "user[add_ids][]=150",
  "request_headers": {
    "Authorization": "Token token=534aa40bdc11bbf455bc269cbb406411",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": " ",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json",
    "Cache-Control": "no-cache",
    "X-Request-Id": "ae260908-d845-4764-96cc-58165cce3d61",
    "X-Runtime": "0.065793",
    "Content-Length": "1"
  },
  "response_content_type": "application/json",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/students/:id/update-schools`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
add_ids | false | array
remove_ids | false | array



## Show a List of Students


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/students",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=534aa40bdc11bbf455bc269cbb406411",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":356,\"first_name\":\"Lorenzo\",\"last_name\":\"Casper\",\"is_archived\":false,\"has_consent\":false,\"birthday\":\"2001-10-03T15:49:49.543Z\",\"grade_level\":0,\"public_id\":\"4122430\"}],\"total_count\":1}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"5232a78ecbbe4b59fdd2f4b61bd25347\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "361986ad-8524-4dd5-b038-10aa86e9b82f",
    "X-Runtime": "0.071248",
    "Content-Length": "198"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/students`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
show_archived | false | boolean
grade_level | false | string
include | false | array of options (Options: note_ids)


# Tags


## Create a Tag


> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/tags",
  "request_body": "tag[name]=New+Tag",
  "request_headers": {
    "Authorization": "Token token=baea25c8e39a2d1b3449cd6687254dff",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"tag\":{\"id\":22,\"name\":\"new tag\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"266acdf56f42407327d145d0fb151224\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "589a124c-7e27-460a-a6f7-40fe1bec118e",
    "X-Runtime": "0.121794",
    "Content-Length": "34"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/tags`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
name | true | string




## Show a List of Tags


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/tags?classroom_id=134",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=baea25c8e39a2d1b3449cd6687254dff",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "classroom_id": "134"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"tags\":[{\"id\":21,\"name\":\"aut voluptatem quia laudantium vero nulla.\",\"color\":\"#FFFFFF\",\"editable\":false},{\"id\":20,\"name\":\"saepe temporibus nihil non. et consequatur consequuntur.\",\"color\":\"#FFFFFF\",\"editable\":false},{\"id\":12,\"name\":\"english\",\"color\":\"et\",\"editable\":true},{\"id\":14,\"name\":\"french\",\"color\":\"perferendis\",\"editable\":true},{\"id\":13,\"name\":\"homework\",\"color\":\"minus\",\"editable\":true},{\"id\":15,\"name\":\"travail\",\"color\":\"magnam\",\"editable\":true}]}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"29c2dec0e487f44994c5e5671d8f246a\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "ef3cd1c3-315d-4f81-a761-25ad1112568f",
    "X-Runtime": "0.097698",
    "Content-Length": "458"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/tags`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
strand_id | false | array
classroom_id | false | array



# Teachers

## Create a Teacher


> Example request & response:

```json
{
  "request_method": "POST",
  "request_path": "/api/v2/teachers",
  "request_body": "user[license_id]=73&user[username]=test6477&user[email]=test10321%40pivotallabs.com&user[first_name]=Larry&user[last_name]=Luettgen&user[type]=Teacher&user[country_code]=CA&user[language_code]=en&user[public_id]=93187&user[phone_number]=14163334444&user[phone_extension]=55555",
  "request_headers": {
    "Authorization": "Token token=a4766eab6cc2f20ddbb3127f24441e49",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 201,
  "response_status_text": "Created",
  "response_body": "{\"user\":{\"id\":444,\"type\":\"Teacher\",\"username\":\"test6477\",\"email\":\"test10321@pivotallabs.com\",\"first_name\":\"Larry\",\"last_name\":\"Luettgen\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":73,\"language_code\":\"en\",\"public_id\":\"93187\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/teachers/444",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"2b10c536faeaa8170fd93c796da09288\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "79b3163f-916f-4e78-ac78-2559dc4f3e60",
    "X-Runtime": "0.095908",
    "Content-Length": "316"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`POST /api/v2/teachers`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | string
email | true | string
password | false | string
password_confirmation | false | string
first_name | false | string
last_name | false | string
country_code | false | string
phone_number | false | string
phone_extension | false | string
public_id | false | string



## Show a Teacher


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/teachers/433?include=[]",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=a4766eab6cc2f20ddbb3127f24441e49",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"user\":{\"id\":433,\"type\":\"Teacher\",\"username\":\"teacher127\",\"email\":\"test10310@pivotallabs.com\",\"first_name\":\"Hassie\",\"last_name\":\"Hodkiewicz\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":false,\"license_id\":73,\"language_code\":\"en\",\"public_id\":\"4921963\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"1b3eb93489b413c8eba417aa15fb5263\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "a7b58b60-c620-4229-be0d-513564be77d7",
    "X-Runtime": "0.046037",
    "Content-Length": "311"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/teachers/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | false | array of options (Options: schools, classrooms, teacher_count, student_count)




## Update a Teacher


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/teachers/433/",
  "request_body": "user[license_id]=73&user[username]=test6481&user[email]=test10325%40pivotallabs.com&user[first_name]=Julio&user[last_name]=Prohaska&user[type]=Teacher&user[country_code]=CA&user[language_code]=en&user[public_id]=89800&user[phone_number]=14163334444&user[phone_extension]=55555",
  "request_headers": {
    "Authorization": "Token token=a4766eab6cc2f20ddbb3127f24441e49",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": "{\"user\":{\"id\":433,\"type\":\"Teacher\",\"username\":\"test6481\",\"email\":\"test10325@pivotallabs.com\",\"first_name\":\"Julio\",\"last_name\":\"Prohaska\",\"phone_number\":\"14163334444\",\"phone_extension\":\"55555\",\"country_code\":\"CA\",\"has_accepted_eula\":false,\"is_archived\":true,\"license_id\":73,\"language_code\":\"en\",\"public_id\":\"89800\"}}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Location": "/api/v2/teachers/433",
    "Content-Type": "application/json; charset=utf-8",
    "Cache-Control": "no-cache",
    "X-Request-Id": "621156cb-fbbb-46dd-87a5-eb3b0533c03f",
    "X-Runtime": "0.081017",
    "Content-Length": "315"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/teachers/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | string
email | true | string
password | false | string
password_confirmation | false | string
first_name | false | string
last_name | false | string
country_code | false | string
phone_number | false | string
phone_extension | false | string
public_id | false | string



## Add or Remove a Teacher's Classrooms


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/teachers/433/update-classrooms",
  "request_body": "user[add_ids][]=156",
  "request_headers": {
    "Authorization": "Token token=a4766eab6cc2f20ddbb3127f24441e49",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": " ",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json",
    "Cache-Control": "no-cache",
    "X-Request-Id": "f62f484f-8617-4ccc-b35a-11f8f63f9e51",
    "X-Runtime": "0.048759",
    "Content-Length": "1"
  },
  "response_content_type": "application/json",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/teachers/:id/update-classrooms`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
add_ids | false | array
remove_ids | false | array



## Add or Remove a Teacher's Schools


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/teachers/433/update-schools",
  "request_body": "user[add_ids][]=158",
  "request_headers": {
    "Authorization": "Token token=a4766eab6cc2f20ddbb3127f24441e49",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 202,
  "response_status_text": "Accepted",
  "response_body": " ",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json",
    "Cache-Control": "no-cache",
    "X-Request-Id": "5f32f64c-c966-4121-82d2-b72a30077df7",
    "X-Runtime": "0.030857",
    "Content-Length": "1"
  },
  "response_content_type": "application/json",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/teachers/:id/update-schools`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
add_ids | false | array
remove_ids | false | array



## Show a List of Teachers


> Example request & response:

```json
{
  "request_method": "GET",
  "request_path": "/api/v2/teachers?include=[]&per_page=9",
  "request_body": null,
  "request_headers": {
    "Authorization": "Token token=a4766eab6cc2f20ddbb3127f24441e49",
    "Host": "example.org",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
    "include": "[]",
    "per_page": "9"
  },
  "request_content_type": null,
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": "{\"users\":[{\"id\":442,\"first_name\":\"Dayne\",\"last_name\":\"Dicki\",\"is_archived\":true,\"type\":\"Teacher\",\"username\":\"teacher135\",\"email\":\"test10319@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":441,\"first_name\":\"Carson\",\"last_name\":\"Jakubowski\",\"is_archived\":true,\"type\":\"Teacher\",\"username\":\"teacher134\",\"email\":\"test10318@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":440,\"first_name\":\"Neha\",\"last_name\":\"Douglas\",\"is_archived\":true,\"type\":\"Teacher\",\"username\":\"teacher133\",\"email\":\"test10317@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":439,\"first_name\":\"Gordon\",\"last_name\":\"Bergnaum\",\"is_archived\":true,\"type\":\"Teacher\",\"username\":\"teacher132\",\"email\":\"test10316@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":438,\"first_name\":\"Laurie\",\"last_name\":\"Walsh\",\"is_archived\":false,\"type\":\"Teacher\",\"username\":\"teacher131\",\"email\":\"test10315@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":437,\"first_name\":\"Johnson\",\"last_name\":\"MacGyver\",\"is_archived\":false,\"type\":\"Teacher\",\"username\":\"teacher130\",\"email\":\"test10314@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":436,\"first_name\":\"Sim\",\"last_name\":\"Sporer\",\"is_archived\":false,\"type\":\"Teacher\",\"username\":\"teacher129\",\"email\":\"test10313@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":435,\"first_name\":\"Abigale\",\"last_name\":\"Morissette\",\"is_archived\":false,\"type\":\"Teacher\",\"username\":\"teacher128\",\"email\":\"test10312@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"},{\"id\":433,\"first_name\":\"Hassie\",\"last_name\":\"Hodkiewicz\",\"is_archived\":false,\"type\":\"Teacher\",\"username\":\"teacher127\",\"email\":\"test10310@pivotallabs.com\",\"phone_number\":null,\"phone_extension\":null,\"country_code\":\"CA\"}],\"total_count\":9}",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json; charset=utf-8",
    "ETag": "\"4aad19c3110cfe7440dc0689aa20b019\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "162d8443-8be3-4b2b-9b2c-66f63e20c273",
    "X-Runtime": "0.367322",
    "Content-Length": "1960"
  },
  "response_content_type": "application/json; charset=utf-8",
  "curl": null
}
```


### HTTP Request

`GET /api/v2/teachers`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | integer
per_page | false | integer
show_archived | false | boolean
include | false | array of options (Options: school_count, classroom_count, status)
exclude_ids | false | integer




# Users

## Reset Password


> Example request & response:

```json
{
  "request_method": "PATCH",
  "request_path": "/api/v2/users/update-password",
  "request_body": "user[current_password]=Password1&user[password]=Password2&user[password_confirmation]=Password2",
  "request_headers": {
    "Authorization": "Token token=91bc080b93f387bb9e00b4e3ce918f4b",
    "Host": "example.org",
    "Content-Type": "application/x-www-form-urlencoded",
    "Cookie": "",
    "Origin": null
  },
  "request_query_parameters": {
  },
  "request_content_type": "application/x-www-form-urlencoded",
  "response_status": 200,
  "response_status_text": "OK",
  "response_body": " ",
  "response_headers": {
    "X-Frame-Options": "SAMEORIGIN",
    "X-XSS-Protection": "1; mode=block",
    "X-Content-Type-Options": "nosniff",
    "Content-Type": "application/json",
    "ETag": "\"7215ee9c7d9dc229d2921a40e899ec5f\"",
    "Cache-Control": "max-age=0, private, must-revalidate",
    "X-Request-Id": "42d2e678-af43-4b4f-ba73-fed2c9a3265a",
    "X-Runtime": "0.041312",
    "Content-Length": "1"
  },
  "response_content_type": "application/json",
  "curl": null
}
```


### HTTP Request

`PATCH /api/v2/users/update-password`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
current_password | true | string
password | true | string
password_confirmation | true | string


