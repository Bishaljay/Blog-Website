# **📝 Blog Website**  
A simple **blogging platform** built with **HTML, CSS, Node.js (Express.js), and MongoDB** that allows users to **read, write, edit, and delete blog posts**.

---

## **📌 Overview**  
This project provides a **user-friendly interface** for managing blog posts. Users can **create, read, update, and delete (CRUD)** blog posts, with data stored securely in **MongoDB**.

### **✨ Features**  
✔️ **Create, Read, Update, Delete (CRUD) blog posts**  
✔️ **User Authentication (Login & Signup)**  
✔️ **Responsive UI for easy reading & writing**  
✔️ **Markdown Support for formatting posts**  
✔️ **Stored securely in MongoDB**  
✔️ **Search and Filter posts**  

---

## **🛠 Tech Stack**  
- 🌐 **Frontend:** HTML, CSS, JavaScript  
- 🖥 **Backend:** Node.js, Express.js  
- 🛢 **Database:** MongoDB (Mongoose ORM)  
- 🔐 **Authentication:** Passport.js, JWT  
- 📦 **Additional Libraries:** EJS for templating  

---

## **🚀 Installation & Setup**  

### **1️⃣ Clone the Repository**  
```bash
git clone https://github.com/your-username/blog-website.git
cd blog-website
```

### **2️⃣ Install Dependencies**  
```bash
npm install
```

### **3️⃣ Set Up MongoDB**  
Ensure **MongoDB is installed** or use **MongoDB Atlas**.  
Create a **`.env` file** and add your MongoDB connection string:  
```
MONGO_URI=mongodb://localhost:27017/blogDB
PORT=3000
SECRET_KEY=your_secret_key
```

### **4️⃣ Start the Server**  
```bash
node server.js
```
- Open **`http://localhost:3000`** in your browser.

---

## **📂 File Structure**  
```
/blog-website
  ├── /public       # Frontend assets (CSS, JS)
  ├── /views        # EJS Templates
  ├── /routes       # Express Routes
  ├── /models       # Mongoose Models
  ├── /controllers  # Business Logic
  ├── server.js     # Main Server File
  ├── .env          # Environment Variables
  ├── package.json  # Project Dependencies
```

---

## **🔗 API Endpoints**  

| Method | Endpoint       | Description            |
|--------|--------------|------------------------|
| POST   | `/register`  | Register a new user    |
| POST   | `/login`     | User login             |
| GET    | `/posts`     | Fetch all blog posts   |
| POST   | `/post`      | Create a new post      |
| GET    | `/post/:id`  | View a specific post   |
| PUT    | `/post/:id`  | Edit a blog post       |
| DELETE | `/post/:id`  | Delete a blog post     |

---

## **💻 Code Snippets**  

### **Blog Post Model (`models/Post.js`)**
```javascript
const mongoose = require("mongoose");

const postSchema = new mongoose.Schema({
  title: { type: String, required: true },
  content: { type: String, required: true },
  author: { type: String, required: true },
  date: { type: Date, default: Date.now }
});

module.exports = mongoose.model("Post", postSchema);
```

### **Server Setup (`server.js`)**
```javascript
const express = require("express");
const mongoose = require("mongoose");
const dotenv = require("dotenv");
const Post = require("./models/Post");

dotenv.config();
const app = express();
app.use(express.json());

mongoose.connect(process.env.MONGO_URI, { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log("MongoDB Connected"));

app.post("/post", async (req, res) => {
  try {
    const post = new Post(req.body);
    await post.save();
    res.status(201).send("Post Created");
  } catch (error) {
    res.status(400).send(error.message);
  }
});

app.listen(process.env.PORT, () => console.log(`Server running on port ${process.env.PORT}`));
```

---

## **📈 Future Enhancements 🚀**  
🔹 **Commenting system**  
🔹 **Like & Share functionality**  
🔹 **User Profiles & Avatars**  
🔹 **Rich text editor for post formatting**    

---

## **👤 Contributors**  
**Your Name** - [GitHub Profile](https://github.com/Bishaljay)  
