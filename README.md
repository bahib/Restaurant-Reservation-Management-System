# Restaurant Reservation Management System

This project is a **Restaurant Reservation Management System** built with a full-stack architecture using **Node.js**, **Express**, **MySQL**, and **React**. The application allows customers to book reservations, manage bookings, and for admins to oversee and manage restaurant tables and reservations.

---

## **Features**

### **Customer Features**
- Register and log in to the system.
- Browse available time slots for reservations.
- Make, modify, or cancel reservations.
- Receive email notifications for confirmation or updates.

### **Admin Features**
- Add, update, or remove restaurant tables.
- View all reservations in real-time.
- Access statistics on reservations (daily, weekly, and monthly).
- Manage users (view and update customer information).

---

## **Technologies Used**

### **Frontend**
- **React**: For building the user interface.
- **Redux/Context API**: For state management.
- **Axios**: For making API calls.
- **React Router**: For handling navigation.

### **Backend**
- **Node.js**: JavaScript runtime environment.
- **Express.js**: Web framework for building RESTful APIs.
- **JWT (JSON Web Tokens)**: For secure authentication.
- **Nodemailer**: For sending email notifications.

### **Database**
- **MySQL**: Relational database for managing application data.
- **Sequelize**: ORM for interacting with the MySQL database.

---

## **Frontend Directory**

/src
  - **components**
    - `Navbar.js` - Header navigation component
    - `Footer.js` - Footer of the application
    - `BookingForm.js` - Form for customers to book a reservation
    - `AdminDashboard.js` - Dashboard for admin functionality
  - **pages**
    - `Home.js` - Landing page of the application
    - `Login.js` - Login page for users
    - `Register.js` - Registration page for new users
    - `Reservations.js` - Page to view and manage user reservations
  - **redux** (if using Redux)
    - `store.js` - Redux store configuration
    - `userSlice.js` - Redux slice for user state management
  - `App.js` - Root component of the application
  - `index.js` - Entry point of the React application

## **Backend Directory**

/src
  - **routes**
    - `authRoutes.js` - Routes for authentication-related endpoints
    - `reservationRoutes.js` - Routes for reservation-related endpoints
    - `adminRoutes.js` - Routes for admin-specific functionalities
  - **controllers**
    - `authController.js` - Logic for handling authentication
    - `reservationController.js` - Logic for reservation management
    - `adminController.js` - Logic for admin-related functionalities
  - **models**
    - `User.js` - Schema for user data
    - `Reservation.js` - Schema for reservation data
    - `Table.js` - Schema for table data
  - **middleware**
    - `authMiddleware.js` - Middleware for authentication and authorization
  - `server.js` - Main server file to start the application

---

## **Database Schema**

### **Users Table**
| Column    | Type                    | Description                 |
|-----------|-------------------------|-----------------------------|
| id        | INT (PK)                | Unique identifier           |
| name      | VARCHAR(100)            | User's name                 |
| email     | VARCHAR(100)            | User's email                |
| password  | VARCHAR(255)            | Hashed password             |
| role      | ENUM('user', 'admin')   | User role                   |

### **Tables Table**
| Column    | Type                    | Description                 |
|-----------|-------------------------|-----------------------------|
| id        | INT (PK)                | Unique identifier           |
| capacity  | INT                     | Number of seats at the table|
| status    | ENUM('available', 'booked') | Availability status    |

### **Reservations Table**
| Column    | Type                    | Description                 |
|-----------|-------------------------|-----------------------------|
| id        | INT (PK)                | Unique identifier           |
| user_id   | INT (FK)                | Linked to Users table       |
| table_id  | INT (FK)                | Linked to Tables table      |
| date      | DATE                    | Reservation date            |
| time      | TIME                    | Reservation time            |
| status    | ENUM('pending', 'confirmed', 'cancelled') | Reservation status |

---

## **API Endpoints**

### **Authentication**
- `POST /api/auth/register`  
  Register a new user.
- `POST /api/auth/login`  
  Log in a user.

### **Reservations**
- `GET /api/reservations`  
  Fetch all reservations (admin only).
- `POST /api/reservations`  
  Create a new reservation.
- `PUT /api/reservations/:id`  
  Modify an existing reservation.
- `DELETE /api/reservations/:id`  
  Cancel a reservation.

### **Admin**
- `GET /api/admin/tables`  
  View all tables.
- `POST /api/admin/tables`  
  Add a new table.
- `PUT /api/admin/tables/:id`  
  Update a table's details.
- `DELETE /api/admin/tables/:id`  
  Remove a table.

---

## **Setup Instructions**

### **1. Clone the Repository**
```bash
git clone https://github.com/bahib/Restaurant-Reservation-Management-System.git
cd restaurant-reservation-system
