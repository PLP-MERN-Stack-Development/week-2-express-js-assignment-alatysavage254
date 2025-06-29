[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19867652&assignment_repo_type=AssignmentRepo)

# Express.js RESTful API Assignment

A complete RESTful API built with Express.js that implements CRUD operations for products, custom middleware, error handling, and advanced features.

## 🚀 Features

- **RESTful API** with full CRUD operations for products
- **Custom Middleware** for logging, authentication, and validation
- **Error Handling** with appropriate HTTP status codes
- **Advanced Features** including filtering, pagination, search, and statistics
- **Authentication** using API key headers

## 📋 Prerequisites

- Node.js (v18 or higher)
- npm or yarn
- Postman, Insomnia, or curl for API testing

## 🛠️ Setup Instructions

1. **Clone the repository:**

   ```bash
   git clone <your-repo-url>
   cd week-2-express-js-assignment-alatysavage254
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Set up environment variables:**

   ```bash
   cp .env.example .env
   ```

   Edit `.env` file with your configuration.

4. **Start the server:**
   ```bash
   npm start
   ```
   The server will run on `http://localhost:3000`

## 🔐 Authentication

All API endpoints require authentication using an API key in the request headers:

```
x-api-key: mysecretkey
```

## 📚 API Documentation

### Base URL

```
http://localhost:3000
```

### Endpoints

#### 1. Get All Products

```http
GET /api/products
```

**Query Parameters:**

- `category` (optional): Filter by category
- `page` (optional): Page number for pagination (default: 1)
- `limit` (optional): Items per page (default: all)

**Example:**

```bash
curl -H "x-api-key: mysecretkey" http://localhost:3000/api/products
curl -H "x-api-key: mysecretkey" "http://localhost:3000/api/products?category=electronics&page=1&limit=2"
```

**Response:**

```json
{
  "total": 3,
  "page": 1,
  "limit": 2,
  "products": [
    {
      "id": "1",
      "name": "Laptop",
      "description": "High-performance laptop with 16GB RAM",
      "price": 1200,
      "category": "electronics",
      "inStock": true
    }
  ]
}
```

#### 2. Get Product by ID

```http
GET /api/products/:id
```

**Example:**

```bash
curl -H "x-api-key: mysecretkey" http://localhost:3000/api/products/1
```

**Response:**

```json
{
  "id": "1",
  "name": "Laptop",
  "description": "High-performance laptop with 16GB RAM",
  "price": 1200,
  "category": "electronics",
  "inStock": true
}
```

#### 3. Create New Product

```http
POST /api/products
```

**Request Body:**

```json
{
  "name": "New Product",
  "description": "Product description",
  "price": 99.99,
  "category": "electronics",
  "inStock": true
}
```

**Example:**

```bash
curl -X POST -H "Content-Type: application/json" -H "x-api-key: mysecretkey" \
  -d '{"name":"New Product","description":"Product description","price":99.99,"category":"electronics","inStock":true}' \
  http://localhost:3000/api/products
```

#### 4. Update Product

```http
PUT /api/products/:id
```

**Request Body:** (same as POST)

**Example:**

```bash
curl -X PUT -H "Content-Type: application/json" -H "x-api-key: mysecretkey" \
  -d '{"name":"Updated Product","description":"Updated description","price":149.99,"category":"electronics","inStock":false}' \
  http://localhost:3000/api/products/1
```

#### 5. Delete Product

```http
DELETE /api/products/:id
```

**Example:**

```bash
curl -X DELETE -H "x-api-key: mysecretkey" http://localhost:3000/api/products/1
```

#### 6. Search Products

```http
GET /api/products/search?name=search_term
```

**Example:**

```bash
curl -H "x-api-key: mysecretkey" "http://localhost:3000/api/products/search?name=laptop"
```

#### 7. Get Product Statistics

```http
GET /api/products/stats
```

**Example:**

```bash
curl -H "x-api-key: mysecretkey" http://localhost:3000/api/products/stats
```

**Response:**

```json
{
  "countByCategory": {
    "electronics": 2,
    "kitchen": 1
  }
}
```

## 🧪 Testing

### Using Postman/Insomnia

1. Set the `x-api-key` header to `mysecretkey`
2. Use the endpoints above with appropriate HTTP methods
3. For POST/PUT requests, set Content-Type to `application/json`

### Using curl

Examples are provided above for each endpoint.

## 📁 Project Structure

```
week-2-express-js-assignment-alatysavage254/
├── server.js              # Main Express server file
├── package.json           # Project dependencies and scripts
├── .env.example          # Example environment variables
├── README.md             # This documentation file
└── Week2-Assignment.md   # Assignment requirements
```

## 🔧 Middleware

- **Logger Middleware**: Logs all requests with timestamp
- **Authentication Middleware**: Validates API key
- **Validation Middleware**: Validates product data for POST/PUT requests
- **Error Handling Middleware**: Global error handler

## 📊 Error Responses

All errors return JSON with an `error` field:

```json
{
  "error": "Error message"
}
```

**Common Status Codes:**

- `200` - Success
- `201` - Created
- `400` - Bad Request (validation error)
- `401` - Unauthorized (invalid API key)
- `404` - Not Found
- `500` - Internal Server Error

## 🚀 Advanced Features

- **Filtering**: Filter products by category
- **Pagination**: Support for page and limit parameters
- **Search**: Search products by name (case-insensitive)
- **Statistics**: Get product count by category

## 📝 Assignment Completion

This implementation includes all required features:

- ✅ Express.js setup with proper dependencies
- ✅ RESTful API routes for products (CRUD operations)
- ✅ Custom middleware (logging, authentication, validation)
- ✅ Error handling with appropriate HTTP status codes
- ✅ Advanced features (filtering, pagination, search, statistics)
- ✅ Comprehensive documentation
