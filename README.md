# GameFortuneSuperChance


Here’s a concise version of your API requirements in a `README.md` format:

---

# Gaming App API Documentation

## **User Management**

### **1. Create User**
- **Endpoint**: `POST /api/users`
- **Request Body**:
  ```json
  {
    "username": "string",  // Unique
    "fullName": "string",
    "password": "string"
  }
  ```
- **Response**:
  ```json
  {
    "userId": "string",
    "username": "string",
    "fullName": "string",
    "balance": 0
  }
  ```

### **2. Update User**
- **Endpoint**: `PUT /api/users/{userId}`
- **Request Body**:
  ```json
  {
    "username": "string",  // Optional
    "fullName": "string",  // Optional
    "password": "string"   // Optional
  }
  ```
- **Response**:
  ```json
  {
    "userId": "string",
    "username": "string",
    "fullName": "string"
  }
  ```

### **3. Delete User**
- **Endpoint**: `DELETE /api/users/{userId}`
- **Response**: `204 No Content`

---

## **Balance Management**

### **Update User Balance**
- **Endpoint**: `PUT /api/users/{userId}/balance`
- **Request Body**:
  ```json
  {
    "balance": number  // Can be more or less than current balance
  }
  ```
- **Response**:
  ```json
  {
    "userId": "string",
    "username": "string",
    "balance": number
  }
  ```

---

## **Notes**
1. **Authentication**: All endpoints (except user creation) require authentication.
2. **Admin Access**: Balance updates are restricted to admin users.
3. **Validation**: Ensure unique usernames, strong passwords, and valid balance values.
4. **Security**: Use HTTPS and hash passwords.

---

## **Example Workflow**

1. **Create User**:
   ```json
   POST /api/users
   {
     "username": "john_doe",
     "fullName": "John Doe",
     "password": "SecurePassword123!"
   }
   ```

2. **Update Balance**:
   ```json
   PUT /api/users/12345/balance
   {
     "balance": 100
   }
   ```

3. **Delete User**:
   ```json
   DELETE /api/users/12345
   ```

---

