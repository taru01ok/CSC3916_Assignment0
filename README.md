# CSC3916 Assignment 0 - REST API Testing with Postman

## Student: Taruni Sabhavat

## Overview
This assignment demonstrates REST API testing using Postman and the JSONPlaceholder mock API. Due to rate limiting on the Google Books API, this implementation uses JSONPlaceholder as an alternative while demonstrating the same REST API concepts including:
- GET requests with query parameters
- Request chaining using environment variables
- Automated testing with assertions
- HTTP header analysis

## Postman Collection

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://taruni-sabhavat-7457486.postman.co/collection/52086578-6685c11c-b9b8-47a7-a18a-05a0d779e5db?source=rip_markdown&active-environment=52086578-e3bea103-4ba5-4551-bd4f-05da64354cde)

## API Endpoints Used
1. **Get Posts**: `https://jsonplaceholder.typicode.com/posts?userId={{user_id}}`
   - Returns all posts for a given user ID
   - Saves the first post ID to environment variable for chaining

2. **Get Post by ID**: `https://jsonplaceholder.typicode.com/posts/{{post_id}}`
   - Uses the post_id from the first request
   - Returns a single post object

## Environment Variables
- `user_id`: Set to 1 (used in first request)
- `post_id`: Dynamically set from first request for chaining

## Tests Implemented
### Request 1: Get Posts
- Validates status code is 200
- Checks that posts array is not empty
- Saves first post ID for request chaining

### Request 2: Get Post by ID
- Validates status code is 200
- Verifies response contains the correct post ID
- Checks that post has title and body fields

## Files Modified/Created
- `utils/googlebooks.js` - Modified return object to include response metadata (data, status, statusText, headers, requestHeader)
- `headers.txt` - HTTP header analysis and documentation for request/response headers

## Assignment Notes
Originally intended to use Google Books API, but due to rate limiting (429 errors), switched to JSONPlaceholder API which demonstrates the same REST API concepts without quota restrictions.