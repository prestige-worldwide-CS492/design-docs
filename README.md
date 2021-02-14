# design-docs
Design docs for CS-492

## Claims
All endpoints relating the creation, modification, retrieval, and
removal of claims.


<h3>
  <img align="left" src="assets/GET.png" height="31">
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

## Authentication
