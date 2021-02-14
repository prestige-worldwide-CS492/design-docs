# design-docs
Design docs for CS-492

## Claims
All endpoints relating the creation, modification, retrieval, and
removal of claims.


<h3>
  <img src="assets/GET.png" height="26.4" align="left">
  <code>api.placeholder.com/claims/:claim_id</code>
</h3>

This endpoint returns a JSON representation of a claim.  `claim_id` is a UUID corresponding to some
claim which has been filed by a user.  Note that this endpoint will return `403 - Forbidden` if the
supplied bearer token is not authorized to access the claim specified by `claim_id`.  If no bearer token is supplied, this endpoint returns `401 - Unauthorized`.  If the UUID does not correspond to
any filed claim, this endpoint returns `404 - Not Found`.

#### Required Parameters
|  Parameter |                            Description                           |
|:----------:|:----------------------------------------------------------------:|
| `claim_id` | A UUID representing a claim which has been filed with the server |

#### Required Headers
|      Header     |              Description              |
|:---------------:|:-------------------------------------:|
| `authorization` | A JWT in the form of `Bearer {token}` |

#### Response Codes
<img align="left" src="assets/200.png" height="21">

```json
{
  "status": 200,
  "policy_number": "0123456789",
  "location": "357 Brittany Farms Ave.",
  "claim_type": "collision coverage",
  "Description": "I got hit."
}
```

<img align="left" src="assets/401.png" height="21">

```json
{
  "status": 401,
  "error": "Unauthorized"
}
```

<img align="left" src="assets/403.png" height="21">

```json
{
  "status": 403,
  "error": "Forbidden"
}
```

<img align="left" src="assets/404.png" height="21">

```json
{
  "status": 404,
  "error": "Not Found"
}
```


<h3>
  <img src="assets/GET.png" height="26.4" align="left">
  <code>api.placeholder.com/user/:user_id</code>
</h3>

This endpoint returns a JSON encoded list of claims associated with a
user.  Additionally, this endpoint returns basic user data. `user_id`
is a UUID representing a user.

#### Required Parameters
|  Parameter |                               Description                            |
|:----------:|:--------------------------------------------------------------------:|
| `user_id`  | A UUID representing a user which has been registered with the server |

#### Required Headers
|      Header     |              Description              |
|:---------------:|:-------------------------------------:|
| `authorization` | A JWT in the form of `Bearer {token}` |

#### Response Codes
<img align="left" src="assets/200.png" height="21">

```json
{
  "status": 200,
  "last_name": "Schmitt",
  "first_name": "Christopher",
  "policy_number": "0123456789",
  "claims": [
    "8b012965-187c-43db-9c32-7d4992af1c93",
    "38dd4362-2c4c-4645-8884-67bf950a8317",
    "2a1e3444-2354-4a22-b16d-ac56b6538bd7"
  ]
}
```

<img align="left" src="assets/401.png" height="21">

```json
{
  "status": 401,
  "error": "Unauthorized"
}
```

<img align="left" src="assets/403.png" height="21">

```json
{
  "status": 403,
  "error": "Forbidden"
}
```

<img align="left" src="assets/404.png" height="21">

```json
{
  "status": 404,
  "error": "Not Found"
}
```


## Authentication
