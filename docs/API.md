# API Specifications

## Authentication Service

### User Registration

**Endpoint:** `POST /auth/register`
**Description:** Registers a new user.
**Request Body:**

```json
{
    "username": "string",
    "email": "string",
    "password": "string"
}
```

**Response:**

```json
{
    "user_id": "string",
    "message": "User registered successfully."
}
```

### User Login

**Endpoint:** `POST /auth/login`
**Description:** Authenticates a user.
**Request Body:**

```json
{
    "email": "string",
    "password": "string"
}
```

**Response:**

```json
{
    "access_token": "string",
    "refresh_token": "string"
}
```

## Product Service

### Create Product

**Endpoint:** `POST /products`
**Description:** Allows users to upload a product listing.
**Request Body:**

```json
{
    "name": "string",
    "description": "string",
    "price": "number",
    "location": "string"
}
```

**Response:**

```json
{
    "product_id": "string",
    "message": "Product created successfully."
}
```

### Search Products by Location

**Endpoint:** `GET /products/search?query={query}&location={location}`
**Description:** Fetches products near the given location.
**Response:**

```json
[
    {
        "product_id": "string",
        "name": "string",
        "price": "number",
        "location": "string"
    }
]
```

## Messaging Service

### Send Message

**Endpoint:** `POST /messages`
**Description:** Sends a message to another user.
**Request Body:**

```json
{
    "sender_id": "string",
    "receiver_id": "string",
    "message": "string"
}
```

**Response:**

```json
{
    "message_id": "string",
    "status": "sent"
}
```

## Search & Recommendation Service

### Get Nearby Services

**Endpoint:** `GET /services/nearby?category={category}&location={location}`
**Description:** Fetches nearby service providers based on category.
**Response:**

```json
[
    {
        "service_id": "string",
        "provider_name": "string",
        "category": "string",
        "location": "string"
    }
]
```

More endpoints will be added as the system expands.
