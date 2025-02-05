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

## **Game Winnings**

### **Handle User Winnings**
- **Endpoint**: `POST /api/game/winnings`
- **Description**: Calculates the user's winnings based on a percentage (1-150%) of their current balance.
- **Request Body**:
  ```json
  {
    "userId": "string",    // User ID
    "percentage": number   // Winning percentage (1-150)
  }
  ```
- **Response**:
  ```json
  {
    "userId": "string",
    "username": "string",
    "oldBalance": number,
    "winnings": number,
    "newBalance": number
  }
  ```

---

## **Admin Commission**

### **Handle Admin Commission**
- **Endpoint**: `POST /api/admin/commission`
- **Description**: Deducts a commission (0-100%) from the user's winnings and adds it to the admin's balance.
- **Request Body**:
  ```json
  {
    "userId": "string",    // User ID
    "commissionPercentage": number  // Commission percentage (0-100)
  }
  ```
- **Response**:
  ```json
  {
    "userId": "string",
    "username": "string",
    "winnings": number,
    "commissionDeducted": number,
    "newBalance": number,
    "adminBalance": number  // Updated admin balance
  }
  ```

---

## **Notes**
1. **Authentication**: All endpoints (except user creation) require authentication.
2. **Admin Access**: Balance updates and commission handling are restricted to admin users.
3. **Validation**:
   - Ensure unique usernames, strong passwords, and valid balance values.
   - Validate percentages (1-150% for winnings, 0-100% for commission).
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

3. **Handle Winnings**:
   ```json
   POST /api/game/winnings
   {
     "userId": "12345",
     "percentage": 50
   }
   ```

4. **Handle Commission**:
   ```json
   POST /api/admin/commission
   {
     "userId": "12345",
     "commissionPercentage": 10
   }
   ```

5. **Delete User**:
   ```json
   DELETE /api/users/12345
   ```

---


