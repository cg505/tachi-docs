# Search Endpoints

*****

## Search Everything.

`GET /api/v1/search`

### Parameters

| Property | Type | Description |
| :: | :: | :: |
| `search` | String | What to search for. |

### Response

| Property | Type | Description |
| :: | :: | :: |
| `users` | Array&lt;[UserDocument](../../tachi-server/documents/user)&gt; | The array of users whose usernames look like the search criterion. |
| `songs` | ([SongDocument](../../tachi-server/documents/song) With [__textScore](../../tachi-server/implementation-details/search.md) and `game`.)[] | An array of songs from all games, with `__textScore` and `game` properties attached. |

### Example

#### Request
```
GET /api/v1/search?search=freedom
```

#### Response

```js
{
	users: [{
		username: "FreedomDiver",
		// ...
	}],
	songs: [{
		title: "FREEDOM",
		__textScore: 2,
		game: "iidx",
		// ...
	}, {
		title: "FREEDOM DiVE",
		__textScore: 1,
		game: "bms",
		// ...
	}]
}
```

!!! info
	For more details on how searching works, see [Search Implementation](../../tachi-server/implementation-details/search.md).
