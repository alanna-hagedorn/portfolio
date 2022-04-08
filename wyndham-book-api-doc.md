# Books API

# Overview
The Books API is a service that provides information on books stored in the Wyndham Book Club database. The different endpoints provide information such as getting all the books, getting books by genre, or adding a new book record to the database. The API structures its requests and responses using a [Book Object](#the-book-object) which can be found below.

---

## Authorization
API requests made to the Books API need to use an API key for authorization. To generate a new API key, navigate to the settings page in the Wyndham developer portal.

To authenticate an API request, provide your API key in the `Authorization` header.

---

## The Book Object
| Attributes | Type |
| --- | --- |
| `title` | `String` |
| `genre` | `String` |
| `author` | `String` |
| `num_pages` | `Int` |

```json
{
  "title": "The Four Winds",
  "genre": "fiction",
  "author": "Kristin Hannah",
  "num_pages": 400 
}
```

---

## Get all books
`GET /v1/books` - Retrieves all the books stored in the Wyndham Book Club database.

### Query Parameters
None.

### Request Body
None.

### Returns
Returns an array of [Book Object](#the-book-object) that represent all the books in the Wyndham Book Club database.

#### Example Response
```json
{
  "books": [
    {
      "title": "The Four Winds",
      "genre": "historical fiction",
      "author": "Kristin Hannah",
      "num_pages": 400 
    },
    {
      "title": "Night",
      "genre": "non-fiction",
      "author": "Elie Wiesel",
      "num_pages": 200
    },
    {
      "title": "The Silent Patient",
      "genre": "mystery",
      "author": "Alex Michaelides",
      "num_pages": 300 
    }
  ]
}
```

### Status Codes
| Code | Description |
| --- | --- |
| `200` | Success - returns an array of [Book Object](#the-book-object) |
| `400` | Bad Request |
| `403` | Forbidden - your API key is not authorized or you did not pass your API key in the `Authorization` header|
| `404` | Not Found |
| `500` | Internal Server Error |
| `503` | Service Unavailable |

---

## Get books by author
`GET /v1/books?author={name}` - Retrieves all the books by the selected author listed in the Wyndham book club database.

### Query Parameters
| Parameter | Description |
| --- | --- |
| `name` | `String` - author name |

### Request Body
None.

### Returns
Returns an array of [Book Object](#the-book-object) that represents all the books by the selected author in the Wyndham book club.

#### Example Response
```json
{
  "books": [
    {
      "title": "The Four Winds",
      "genre": "historical fiction",
      "author": "Kristin Hannah",
      "num_pages": 400 
    },
    {
      "title": "The Great Alone",
      "genre": "adventure",
      "author": "Kristin Hannah",
      "num_pages": 435
    },
    {
      "title": "Firefly Lane",
      "genre": "romance",
      "author": "Kristin Hannah",
      "num_pages": 415
    }
  ]
}
```

### Status Codes
| Code | Description |
| --- | --- |
| `200` | Success - returns an array of [Book Object](#the-book-object) from the selected author |
| `400` | Bad Request |
| `403` | Forbidden - your API key is not authorized or you did not pass your API key in the `Authorization` header|
| `404` | Not Found |
| `500` | Internal Server Error |
| `503` | Service Unavailable |

---

## Get books by genre
`GET /v1/books?genre={type}` - Retrieves all the books by selected genre listed in the Wyndham book club database.

### Query Parameters
| Parameter | Description |
| --- | --- |
| `type` | `String` - genre type |

### Request Body
None.

### Returns
Returns an array of [Book Object](#the-book-object) that represent all the books by the selected genre in the Wyndham book club.

#### Example Response
```json
{
  "books": [
    {
      "title": "The Silent Patient",
      "genre": "mystery",
      "author": "Alex Michaelides",
      "num_pages": 300 
    },
    {
      "title": "And Then There Were None",
      "genre": "mystery",
      "author": "Agatha Christie",
      "num_pages": 220
    },
    {
      "title": "Watching You",
      "genre": "mystery",
      "author": "Lisa Jewel",
      "num_pages": 312
    }
  ]
}
```

### Status Codes
| Code | Description |
| --- | --- |
| `200` | Success - returns an array of [Book Object](#the-book-object) from the given genre |
| `400` | Bad Request |
| `403` | Forbidden - your API key is not authorized or you did not pass your API key in the `Authorization` header|
| `404` | Not Found |
| `500` | Internal Server Error |
| `503` | Service Unavailable |

---

## Add a new book
`POST /v1/books` - Add a book to the Wyndham book club database.

### Query Parameters
None.

### Request Body Parameters
| Parameter | Description |
| --- | --- |
| `title` | `String` - title of the book |
| `genre` | `String` - genre of the book |
| `author` | `String` - author of the book |
| `num_pages` | `Int` - number of pages of the book |

#### Example Request Body
```json
{
  "title": "And Then There Were None",
  "genre": "mystery",
  "author": "Agatha Christie",
  "num_pages": 220
}
```

### Returns
Returns an empty JSON object.

#### Example Response
```json
{}
```

### Status Codes
| Code | Description |
| --- | --- |
| `201` | Success - successfully added new book to the database |
| `400` | Bad Request |
| `403` | Forbidden - your API key is not authorized or you did not pass your API key in the `Authorization` header|
| `404` | Not Found |
| `500` | Internal Server Error |
| `503` | Service Unavailable |

---

## Delete a book
`DELETE /v1/books` - Add a book to the Wyndham book club database.

### Query Parameters
None.

### Request Body Parameters
| Parameter | Description |
| --- | --- |
| `title` | `String` - title of the book to delete |
| `author` | `String` - author of the book to delete |

#### Example Request Body
```json
{
  "title": "And Then There Were None",
  "author": "Agatha Christie"
}
```

### Returns
Returns an empty JSON object.

#### Example Response
```json
{}
```

### Status Codes
| Code | Description |
| --- | --- |
| `200` | Success - successfully added new book to the database |
| `400` | Bad Request |
| `403` | Forbidden - your API key is not authorized or you did not pass your API key in the `Authorization` header|
| `404` | Not Found |
| `500` | Internal Server Error |
| `503` | Service Unavailable |
