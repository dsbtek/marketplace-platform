# Database Schema

## Tables

### 1. Users

Stores user information including buyers and service providers.

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    full_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    phone_number VARCHAR(20) UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    location GEOMETRY(Point, 4326),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 2. Products

Stores product listings from users.

```sql
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id) ON DELETE CASCADE,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10,2) NOT NULL,
    category VARCHAR(100),
    location GEOMETRY(Point, 4326),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 3. Services

Stores services offered by users.

```sql
CREATE TABLE services (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(255) NOT NULL,
    description TEXT,
    category VARCHAR(100),
    price_range VARCHAR(50),
    location GEOMETRY(Point, 4326),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 4. Messages

Handles user interactions via chat.

```sql
CREATE TABLE messages (
    id SERIAL PRIMARY KEY,
    sender_id INT REFERENCES users(id) ON DELETE CASCADE,
    receiver_id INT REFERENCES users(id) ON DELETE CASCADE,
    message TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 5. Transactions

Tracks purchases and service requests.

```sql
CREATE TABLE transactions (
    id SERIAL PRIMARY KEY,
    buyer_id INT REFERENCES users(id) ON DELETE CASCADE,
    seller_id INT REFERENCES users(id) ON DELETE CASCADE,
    product_id INT REFERENCES products(id),
    service_id INT REFERENCES services(id),
    amount DECIMAL(10,2) NOT NULL,
    status VARCHAR(50) DEFAULT 'pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Indexing & Performance

-   **Indexing location data** for fast geolocation queries.
-   **Partitioning messages** for scalability.
-   **Using Redis** for caching frequent queries.
