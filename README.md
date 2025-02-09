# API Explorer: Mastering RESTful Connections

## API Overview
The MoviesDatabase API is a powerful tool designed to provide detailed information about movies, TV shows, and related entertainment data. It allows users to search for titles, retrieve details about cast and crew, and explore genres, release dates, and ratings. Additionally, it supports advanced features like filtering and sorting data to meet specific criteria.

## Version
The current version of the API is **v1**.

## Available Endpoints
- **GET /movies**: Retrieve a list of movies based on search criteria.
- **GET /movies/{id}**: Fetch detailed information about a specific movie by its ID.
- **GET /genres**: Get a list of all available genres.
- **GET /actors/{id}**: Retrieve detailed information about an actor.
- **POST /movies**: Add a new movie (requires authentication).
- **PUT /movies/{id}**: Update details of an existing movie (requires authentication).
- **DELETE /movies/{id}**: Remove a movie from the database (requires authentication).

## Request and Response Format
### Request Example
**GET /movies**
```http
GET https://api.moviesdatabase.com/v1/movies?genre=action&year=2023
Headers:
  Authorization: Bearer <API_KEY>
```

### Response Example
```json
{
  "status": "success",
  "data": [
    {
      "id": 123,
      "title": "Action Movie",
      "release_date": "2023-07-15",
      "genre": "Action",
      "rating": 8.5
    }
  ]
}
```

### Error Response Example
```json
{
  "status": "error",
  "message": "Invalid API key",
  "code": 401
}
```

## Authentication
The MoviesDatabase API requires an API key for authentication. Include your API key in the headers of every request:
```http
Authorization: Bearer <API_KEY>
```
To obtain an API key, register on the MoviesDatabase website and generate your key from the API settings.

## Error Handling
Common error responses include:
- **401 Unauthorized**: Invalid or missing API key. Ensure your API key is correct and included in the header.
- **404 Not Found**: The requested resource does not exist. Verify the endpoint and parameters.
- **429 Too Many Requests**: Rate limit exceeded. Reduce the frequency of your requests and implement exponential backoff.
- **500 Internal Server Error**: An issue occurred on the server. Retry the request later.

## Usage Limits and Best Practices
- **Rate Limits**: The API allows up to 100 requests per minute per user. Exceeding this limit will result in a 429 error.
- **Best Practices**:
  - Use caching to minimize repeated requests for the same data.
  - Paginate results for large datasets to improve performance.
  - Validate API responses to handle unexpected structures or data types.
  - Log errors for debugging and future reference.

---

