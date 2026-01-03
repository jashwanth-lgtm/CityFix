# MongoDB Setup Guide

## Problem
The application can't connect to MongoDB, which is why login isn't working.

Error: `MongoDB Connection Error: connect ECONNREFUSED ::1:27017`

## Solution Options

### Option 1: MongoDB Atlas (Cloud - Easiest) ✅ RECOMMENDED

1. **Sign up for MongoDB Atlas** (Free)
   - Go to: https://www.mongodb.com/cloud/atlas/register
   - Create a free account

2. **Create a Free Cluster**
   - Click "Build a Database"
   - Choose "M0 Free" tier
   - Select a cloud provider and region close to you
   - Click "Create"

3. **Set up Database Access**
   - Go to "Database Access" in the left sidebar
   - Click "Add New Database User"
   - Create a username and password (remember these!)
   - Set privileges to "Read and write to any database"
   - Click "Add User"

4. **Set up Network Access**
   - Go to "Network Access" in the left sidebar
   - Click "Add IP Address"
   - Click "Allow Access from Anywhere" (for development)
   - Click "Confirm"

5. **Get Connection String**
   - Go to "Database" in the left sidebar
   - Click "Connect" on your cluster
   - Choose "Connect your application"
   - Copy the connection string (looks like: `mongodb+srv://username:<password>@cluster0.xxxxx.mongodb.net/`)
   - Replace `<password>` with your actual password

6. **Update your .env file**
   ```
   MONGO_URI=mongodb+srv://username:yourpassword@cluster0.xxxxx.mongodb.net/smartcity?retryWrites=true&w=majority
   ```

7. **Restart the server**
   - The server should automatically restart and connect to MongoDB Atlas

---

### Option 2: Local MongoDB Installation

1. **Download MongoDB Community Server**
   - Go to: https://www.mongodb.com/try/download/community
   - Download for Windows
   - Install with default settings

2. **Start MongoDB**
   - MongoDB should start automatically as a Windows service
   - Or open Command Prompt and run: `mongod`

3. **Your .env is already configured for local MongoDB**
   ```
   MONGO_URI=mongodb://localhost:27017/smartcity
   ```

4. **Restart the server**

---

## After MongoDB is Connected

1. **Run the seed script** to create test users:
   ```bash
   cd server
   node seed.js
   ```

2. **Use these credentials to login**:
   - **Citizen**: citizen@test.com / password123
   - **Admin**: admin@test.com / password123

---

## Verify Connection

Watch the server logs. You should see:
```
MongoDB Connected
Server running on port 5000
```

Instead of:
```
MongoDB Connection Error: connect ECONNREFUSED
```
