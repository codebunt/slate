---
title: KAPSARC Data Versioning API
language_tabs:
  - ruby: Ruby
  - python: Python
toc_footers: []
includes: []
search: false
highlight_theme: darkula
headingLevel: 2

---

<h1 id="kapsarc-data-versioning-api">KAPSARC Data Versioning API v0.1.1</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

API for KAPSARC Data Versioning API

Email: <a href="mailto:pavithra.shetty@kapsarc.org">Support</a> 
License: <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a>

# Authentication

* API Key (ApiKeyAuth)
    - Parameter Name: **h-token**, in: header. 

<h1 id="kapsarc-data-versioning-api-default">Default</h1>

## Imports a excel or csv file. The header has to be at the first line and has to match the name of column in the dataset.

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'multipart/form-data',
  'h-token' => 'API_KEY'
}

result = RestClient.post '/update/{repoid}/{branch}/{tableid}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'multipart/form-data',
  'h-token': 'API_KEY'
}

r = requests.post('/update/{repoid}/{branch}/{tableid}', params={

}, headers = headers)

print r.json()

```

`POST /update/{repoid}/{branch}/{tableid}`

> Body parameter

```yaml
xlfile: string

```

<h3 id="imports-a-excel-or-csv-file.-the-header-has-to-be-at-the-first-line-and-has-to-match-the-name-of-column-in-the-dataset.-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|repoid|path|string|true|Repository Id|
|branch|path|string|true|Branch Id|
|tableid|path|string|true|Table Id|
|body|body|object|false|none|
|» xlfile|body|string(binary)|false|File to import. This has to be either a excel or a csv.|

<h3 id="imports-a-excel-or-csv-file.-the-header-has-to-be-at-the-first-line-and-has-to-match-the-name-of-column-in-the-dataset.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

<h1 id="kapsarc-data-versioning-api-users">users</h1>

Operations available to regular users

## List of all Data Repository

<a id="opIddataRepository"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'h-token' => 'API_KEY'
}

result = RestClient.get '/datarepos',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'h-token': 'API_KEY'
}

r = requests.get('/datarepos', params={

}, headers = headers)

print r.json()

```

`GET /datarepos`

By passing in the appropriate options, you can List all repositories

<h3 id="list-of-all-data-repository-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|q|query|string|false|Query String|

> Example responses

> 200 Response

```json
[
  {
    "name": "string",
    "tables": [
      {
        "name": "string",
        "columns": [
          {
            "type": "string",
            "name": "string",
            "saved": true
          }
        ],
        "uniqueColumns": [
          {
            "type": "string",
            "name": "string",
            "saved": true
          }
        ]
      }
    ],
    "id": "string",
    "branches": [
      {
        "id": "string",
        "name": "string",
        "commitId": 0,
        "timestamp": "string",
        "repo": "string"
      }
    ],
    "currentBranch": {
      "id": "string",
      "name": "string",
      "commitId": 0,
      "timestamp": "string",
      "repo": "string"
    }
  }
]
```

<h3 id="list-of-all-data-repository-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of all repositories|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<h3 id="list-of-all-data-repository-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[DataRepoItem](#schemadatarepoitem)]|false|none|none|
|» name|string|true|none|none|
|» tables|[object]|true|none|none|
|»» name|string|false|none|none|
|»» columns|[object]|false|none|none|
|»»» type|string|false|none|none|
|»»» name|string|false|none|none|
|»»» saved|boolean|false|none|none|
|»» uniqueColumns|[object]|false|none|none|
|»»» type|string|false|none|none|
|»»» name|string|false|none|none|
|»»» saved|boolean|false|none|none|
|»» id|string|true|none|none|
|»» branches|[object]|true|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» commitId|number|false|none|none|
|»»» timestamp|string|false|none|none|
|»»» repo|string|false|none|none|
|»» currentBranch|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» commitId|number|true|none|none|
|»»» timestamp|string|true|none|none|
|»»» repo|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

## Creates a data repository

<a id="opIdcreateRepo"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'h-token' => 'API_KEY'
}

result = RestClient.post '/datarepos',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'h-token': 'API_KEY'
}

r = requests.post('/datarepos', params={

}, headers = headers)

print r.json()

```

`POST /datarepos`

Creates a data repository

> Body parameter

```json
{
  "attr1": "string",
  "attr2": "string",
  "attr3": "string",
  "description": "string",
  "name": "string"
}
```

<h3 id="creates-a-data-repository-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CreateDataRepoItem](#schemacreatedatarepoitem)|false|Data Repo to add|

> Example responses

> 200 Response

```json
{}
```

<h3 id="creates-a-data-repository-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Created Data Repository|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|invalid input, object invalid|None|

<h3 id="creates-a-data-repository-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» name|string|true|none|none|
|» tables|[object]|true|none|none|
|»» name|string|false|none|none|
|»» columns|[object]|false|none|none|
|»»» type|string|false|none|none|
|»»» name|string|false|none|none|
|»»» saved|boolean|false|none|none|
|»» uniqueColumns|[object]|false|none|none|
|»»» type|string|false|none|none|
|»»» name|string|false|none|none|
|»»» saved|boolean|false|none|none|
|»» id|string|true|none|none|
|»» branches|[object]|true|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» commitId|number|false|none|none|
|»»» timestamp|string|false|none|none|
|»»» repo|string|false|none|none|
|»» currentBranch|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» commitId|number|true|none|none|
|»»» timestamp|string|true|none|none|
|»»» repo|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

## Get a data repository

<a id="opIdgetDataRepository"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'h-token' => 'API_KEY'
}

result = RestClient.get '/datarepo/{repoId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'h-token': 'API_KEY'
}

r = requests.get('/datarepo/{repoId}', params={

}, headers = headers)

print r.json()

```

`GET /datarepo/{repoId}`

By passing in the repoid , you can get the details of the repository

<h3 id="get-a-data-repository-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|repoId|path|string|true|Repository Id|

> Example responses

> 200 Response

```json
{
  "name": "string",
  "tables": [
    {
      "name": "string",
      "columns": [
        {
          "type": "string",
          "name": "string",
          "saved": true
        }
      ],
      "uniqueColumns": [
        {
          "type": "string",
          "name": "string",
          "saved": true
        }
      ]
    }
  ],
  "id": "string",
  "branches": [
    {
      "id": "string",
      "name": "string",
      "commitId": 0,
      "timestamp": "string",
      "repo": "string"
    }
  ],
  "currentBranch": {
    "id": "string",
    "name": "string",
    "commitId": 0,
    "timestamp": "string",
    "repo": "string"
  }
}
```

<h3 id="get-a-data-repository-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|the repositories|[DataRepoItem](#schemadatarepoitem)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

## Updates a data repository

<a id="opIdupdateRepo"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'h-token' => 'API_KEY'
}

result = RestClient.put '/datarepo/{repoId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'h-token': 'API_KEY'
}

r = requests.put('/datarepo/{repoId}', params={

}, headers = headers)

print r.json()

```

`PUT /datarepo/{repoId}`

Updates a data repository

> Body parameter

```json
{
  "attr1": "string",
  "attr2": "string",
  "attr3": "string",
  "description": "string",
  "name": "string"
}
```

<h3 id="updates-a-data-repository-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|repoId|path|string|true|Repository Id|
|body|body|[CreateDataRepoItem](#schemacreatedatarepoitem)|false|Data Repo to add|

> Example responses

> 200 Response

```json
{}
```

<h3 id="updates-a-data-repository-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Updated Data Repository|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|invalid input, object invalid|None|

<h3 id="updates-a-data-repository-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» name|string|true|none|none|
|» tables|[object]|true|none|none|
|»» name|string|false|none|none|
|»» columns|[object]|false|none|none|
|»»» type|string|false|none|none|
|»»» name|string|false|none|none|
|»»» saved|boolean|false|none|none|
|»» uniqueColumns|[object]|false|none|none|
|»»» type|string|false|none|none|
|»»» name|string|false|none|none|
|»»» saved|boolean|false|none|none|
|»» id|string|true|none|none|
|»» branches|[object]|true|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» commitId|number|false|none|none|
|»»» timestamp|string|false|none|none|
|»»» repo|string|false|none|none|
|»» currentBranch|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» commitId|number|true|none|none|
|»»» timestamp|string|true|none|none|
|»»» repo|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

## Delete a record

<a id="opIddelete record"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'h-token' => 'API_KEY'
}

result = RestClient.delete '/dataset/{repoid}/{branch}/{tableid}/{rid}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'h-token': 'API_KEY'
}

r = requests.delete('/dataset/{repoid}/{branch}/{tableid}/{rid}', params={

}, headers = headers)

print r.json()

```

`DELETE /dataset/{repoid}/{branch}/{tableid}/{rid}`

By passing in the repoid, branch , table and record, you can delete the record in the repository

<h3 id="delete-a-record-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|repoid|path|string|true|Repository Id|
|branch|path|string|true|Branch Id|
|tableid|path|string|true|Table Id|
|rid|path|string|true|Record Id|

<h3 id="delete-a-record-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|the dataset|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

## List of all commits for a branch

<a id="opIdgetCommits"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'h-token' => 'API_KEY'
}

result = RestClient.get '/commits/{repoId}/{branch}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'h-token': 'API_KEY'
}

r = requests.get('/commits/{repoId}/{branch}', params={

}, headers = headers)

print r.json()

```

`GET /commits/{repoId}/{branch}`

By passing repository id and Branch name you can get all the commits.

<h3 id="list-of-all-commits-for-a-branch-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|repoId|path|string|true|Repository Id|
|branch|path|string|true|Branch Name|
|offset|query|string(int)|false|Starting index of the page (Default 0)|
|psize|query|string(int)|false|Page Size (Default 10)|
|since|query|integer(int)|false|From the date in milliseconds|
|to|query|integer(int)|false|To date in milliseconds|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "comment": "string",
    "branch": "string",
    "ts": "string",
    "user": "string"
  }
]
```

<h3 id="list-of-all-commits-for-a-branch-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of all commits for the branch|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<h3 id="list-of-all-commits-for-a-branch-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CommitItem](#schemacommititem)]|false|none|none|
|» id|number|true|none|none|
|» comment|string|true|none|none|
|» branch|string|true|none|none|
|» ts|string|true|none|none|
|» user|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

## Commit tree for a data repository

<a id="opIdgetCommitTree"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'h-token' => 'API_KEY'
}

result = RestClient.get '/tree/{repoId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'h-token': 'API_KEY'
}

r = requests.get('/tree/{repoId}', params={

}, headers = headers)

print r.json()

```

`GET /tree/{repoId}`

Constructs a commit tree for a repository

<h3 id="commit-tree-for-a-data-repository-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|repoId|path|string|true|Repository Id|

> Example responses

> 200 Response

```json
[
  {
    "children": [
      "string"
    ],
    "parent": 0,
    "level": 0,
    "displayLabel": "string",
    "branchId": "string",
    "name": "string",
    "id": 0
  }
]
```

<h3 id="commit-tree-for-a-data-repository-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Commit Tree for a branch|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<h3 id="commit-tree-for-a-data-repository-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[BranchTree](#schemabranchtree)]|false|none|none|
|» children|[string]|false|none|none|
|» parent|number|false|none|none|
|» level|number|true|none|none|
|» displayLabel|string|true|none|none|
|» branchId|string|true|none|none|
|» name|string|true|none|none|
|» id|number|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

<h1 id="kapsarc-data-versioning-api-dataset">dataset</h1>

## Get a dataset

<a id="opIdgetDataSet"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'h-token' => 'fe61480620fe517cdb89a1712a8f5d7d9876c359c5b94145',
  'h-token' => 'API_KEY'
}

result = RestClient.get '/dataset/{repoid}/{branch}/{tableid}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'h-token': 'fe61480620fe517cdb89a1712a8f5d7d9876c359c5b94145',
  'h-token': 'API_KEY'
}

r = requests.get('/dataset/{repoid}/{branch}/{tableid}', params={

}, headers = headers)

print r.json()

```

`GET /dataset/{repoid}/{branch}/{tableid}`

By passing in the repoid , you can get the details of the repository

<h3 id="get-a-dataset-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|h-token|header|string|true|none|
|repoid|path|string|true|Repository Id|
|branch|path|string|true|Branch Id|
|tableid|path|string|true|Table Id|
|_offset|query|number|false|start of page|
|_limit|query|number|false|Pagesize|

> Example responses

> 200 Response

```json
{
  "name": "string",
  "tables": [
    {
      "name": "string",
      "columns": [
        {
          "type": "string",
          "name": "string",
          "saved": true
        }
      ],
      "uniqueColumns": [
        {
          "type": "string",
          "name": "string",
          "saved": true
        }
      ]
    }
  ],
  "id": "string",
  "branches": [
    {
      "id": "string",
      "name": "string",
      "commitId": 0,
      "timestamp": "string",
      "repo": "string"
    }
  ],
  "currentBranch": {
    "id": "string",
    "name": "string",
    "commitId": 0,
    "timestamp": "string",
    "repo": "string"
  }
}
```

<h3 id="get-a-dataset-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|the dataset|[DataRepoItem](#schemadatarepoitem)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

# Schemas

<h2 id="tocSbranchtree">BranchTree</h2>

<a id="schemabranchtree"></a>

```json
{
  "children": [
    "string"
  ],
  "parent": 0,
  "level": 0,
  "displayLabel": "string",
  "branchId": "string",
  "name": "string",
  "id": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|children|[string]|false|none|none|
|parent|number|false|none|none|
|level|number|true|none|none|
|displayLabel|string|true|none|none|
|branchId|string|true|none|none|
|name|string|true|none|none|
|id|number|true|none|none|

<h2 id="tocScreatedatarepoitem">CreateDataRepoItem</h2>

<a id="schemacreatedatarepoitem"></a>

```json
{
  "attr1": "string",
  "attr2": "string",
  "attr3": "string",
  "description": "string",
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|attr1|string|true|none|Application URL if any|
|attr2|string|true|none|Source Code URL (github , bitbucket) if any|
|attr3|string|true|none|Data URL if any|
|description|string|true|none|Brief description of the repository|
|name|string|true|none|none|

<h2 id="tocScommititem">CommitItem</h2>

<a id="schemacommititem"></a>

```json
{
  "id": 0,
  "comment": "string",
  "branch": "string",
  "ts": "string",
  "user": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|true|none|none|
|comment|string|true|none|none|
|branch|string|true|none|none|
|ts|string|true|none|none|
|user|string|true|none|none|

<h2 id="tocSdatarepoitem">DataRepoItem</h2>

<a id="schemadatarepoitem"></a>

```json
{
  "name": "string",
  "tables": [
    {
      "name": "string",
      "columns": [
        {
          "type": "string",
          "name": "string",
          "saved": true
        }
      ],
      "uniqueColumns": [
        {
          "type": "string",
          "name": "string",
          "saved": true
        }
      ]
    }
  ],
  "id": "string",
  "branches": [
    {
      "id": "string",
      "name": "string",
      "commitId": 0,
      "timestamp": "string",
      "repo": "string"
    }
  ],
  "currentBranch": {
    "id": "string",
    "name": "string",
    "commitId": 0,
    "timestamp": "string",
    "repo": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|tables|[object]|true|none|none|
|» name|string|false|none|none|
|» columns|[object]|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|»» saved|boolean|false|none|none|
|» uniqueColumns|[object]|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|»» saved|boolean|false|none|none|
|» id|string|true|none|none|
|» branches|[object]|true|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» commitId|number|false|none|none|
|»» timestamp|string|false|none|none|
|»» repo|string|false|none|none|
|» currentBranch|object|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» commitId|number|true|none|none|
|»» timestamp|string|true|none|none|
|»» repo|string|true|none|none|

