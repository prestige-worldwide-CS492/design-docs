# design-docs
Design docs for CS-492

## Claims
All endpoints relating the creation, modification, retrieval, and
removal of claims.

### <p style="font-size: 85%; background: SeaGreen; color: White; padding: 0.2em 0.5em; border-radius: 3px; font-family: Consolas, monaco, monospace;">GET</p> `api.placeholder.com/claims/:claim_id`
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
<span style="font-size: 85%; background: SeaGreen; color: White; padding: 0.2em 0.5em; border-radius: 3px; font-family: Consolas, monaco, monospace;">200</span>
```json
{
  "status": 200,
  "policy_number": "0123456789",
  "location": "357 Brittany Farms Ave.",
  "claim_type": "collision coverage",
  "Description": "I got hit."
}
```

<span style="font-size: 85%; background: Tomato; color: White; padding: 0.2em 0.5em; border-radius: 3px; font-family: Consolas, monaco, monospace;">401</span>
```json
{
  "status": 401,
  "error": "Unauthorized"
}
```

<span style="font-size: 85%; background: Tomato; color: White; padding: 0.2em 0.5em; border-radius: 3px; font-family: Consolas, monaco, monospace;">403</span>
```json
{
  "status": 403,
  "error": "Forbidden"
}
```

<span style="font-size: 85%; background: Tomato; color: White; padding: 0.2em 0.5em; border-radius: 3px; font-family: Consolas, monaco, monospace;">404</span>
```json
{
  "status": 404,
  "error": "Not Found"
}
```

## Authentication
