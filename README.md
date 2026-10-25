# SiPeMa — Sistem Informasi Pemesanan Makanan

SOFTWARE | DESKTOP APPLICATION | JAVA ‧ MySQL ‧ JDBC

SiPeMa is a simple desktop-based food ordering application developed using Java Swing and MySQL. It allows users to browse food, beverages, and snacks, add products to a shopping cart, manage quantities, calculate the total order price, and proceed to checkout using a QR code payment flow.

## 01. Project Overview

### Project Description

SiPeMa (Sistem Informasi Pemesanan Makanan) is a desktop application developed as a Project-Based Learning (PBO) project. It provides a graphical interface for browsing menu items and managing food orders through a simple ordering workflow.

The application organizes products into three main categories:

- **Makanan (Food):** Displays available food items.
- **Minuman (Beverages):** Displays available drinks.
- **Jajan/Ngemil (Snacks):** Displays snacks and light meals.

Product information, including names, descriptions, prices, and image paths, is retrieved from a MySQL database.

### Objectives

- Develop a desktop-based food ordering application using Java.
- Apply Object-Oriented Programming (OOP) concepts in application development.
- Integrate a Java application with a MySQL database.
- Implement shopping cart functionality and automatic price calculation.
- Provide a simple checkout flow using QR code payment and WhatsApp communication.

### Problem Statement

A simple food ordering process can become inconvenient when menu information, order selection, quantity management, and total price calculation are handled separately.

SiPeMa addresses this by combining menu browsing, cart management, and checkout into a single desktop application.

### Solution and Key Features

**1. Menu Browsing**

Users can browse three product categories: food, beverages, and snacks. Each menu item displays its name, description, price, and image retrieved from the database. Users can navigate through the menu horizontally.

**2. Shopping Cart Management**

Users can add products to the cart and increase or decrease the quantity of each item. The application updates item prices and the overall order total as quantities change. Removing an item when its quantity reaches zero is part of the documented cart behavior.

**3. Automatic Price Calculation**

The total price is calculated based on the selected items and their quantities.

For example:

`Item subtotal = Unit price × Quantity`

`Total order price = Sum of all item subtotals`

**4. Checkout and Payment Flow**

The checkout page displays a QR code for payment. After completing the payment, users can select the payment button to open a WhatsApp link for communicating the payment proof and delivery address to the administrator.

**5. Graphical User Interface**

The application uses Java Swing to create desktop windows, menu cards, navigation buttons, a shopping cart interface, and a checkout page. Custom fonts, background images, icons, and rounded interface elements provide a consistent visual design.

## 02. Tech Stack

| Category | Technology |
|---|---|
| Programming Language | Java |
| GUI Framework | Java Swing |
| Layout and Graphics | Java AWT, Graphics2D |
| Database | MySQL |
| Database Connectivity | JDBC |
| JDBC Driver | MySQL Connector/J 9.1.0 |
| Development Environment | Visual Studio Code |
| Database Management | MySQL-compatible local database environment |

### Database Structure

The application uses a MySQL database named `menu`. Based on the provided Java code, the database includes the following menu tables:

| Table | Purpose |
|---|---|
| `makanan` | Stores food menu information |
| `minuman` | Stores beverage menu information |
| `jajan` | Stores snack menu information |

Each menu table is queried for product names, descriptions, prices, and image paths.

The `DatabaseConnection` class provides a reusable JDBC connection to the local MySQL database.

### Project Structure

```text
SiPeMa/
├── .vscode/
├── Database/
│   └── menu.sql
├── Driver/
│   └── mysql-connector-j-9.1.0.jar
├── Images/
│   ├── fonts/
│   │   ├── Abel-Regular.ttf
│   │   └── IrishGrover.ttf
│   ├── icon/
│   ├── jajan/
│   ├── makanan/
│   ├── minuman/
│   ├── Backgorund.jpeg
│   └── QRcode.jpg
├── DatabaseConnection.java
├── HalamanCheckout.java
├── HalamanJajan.java
├── HalamanKeranjang.java
├── HalamanMakanan.java
├── HalamanMinuman.java
├── HalamanUtama.java
├── JajanTable.java
├── Keranjang.java
├── MakananTable.java
├── MinumanTable.java
├── README.md
└── PENJELASAN.pdf
```

The structure above represents the main files shown in the provided project structure. Additional Java classes may exist in the complete project.

## 03. Screenshots / Results

### Application Workflow

**1. Main Page**

The main page displays the SiPeMa branding, a shopping cart icon, and three central navigation buttons for Food, Beverages, and Snacks.

**2. Food Menu**

The food page displays product cards containing images, names, descriptions, prices, and an add-to-cart button. Menu data is retrieved from the `makanan` table.

**3. Beverage Menu**

The beverage page presents available drinks using the same product-card layout. Menu information is retrieved from the `minuman` table.

**4. Snack Menu**

The snack page displays available snacks and light meals. Product information is retrieved from the `jajan` table.

**5. Shopping Cart**

The shopping cart combines selected products from all three categories. Users can adjust quantities, remove items, and review the updated total order price.

**6. Checkout Page**

The checkout page displays a QR code and a payment button. The button opens the configured WhatsApp link so users can send payment proof and delivery details to the administrator.

### Insights

- **Centralized ordering:** Food, beverages, and snacks are accessible through one application.
- **Database-driven menus:** Product information is retrieved from MySQL instead of being defined entirely in the GUI code.
- **Dynamic cart calculations:** Quantity changes affect item subtotals and the overall order total.
- **Integrated checkout flow:** The application connects order review, QR code payment, and WhatsApp communication.

### Usefulness

SiPeMa demonstrates how a desktop application can simplify a basic food ordering workflow. By bringing product browsing, cart management, and checkout together, it provides a clearer way to select multiple items and review the total cost before payment.

### Practical Application

The project can serve as a prototype for a small food business that needs a simple desktop-based menu and ordering interface. Its database-driven menu structure can also be extended to support product management, order records, and more complete transaction processing.

*The application is a prototype. The documented payment flow uses a QR code and WhatsApp redirection; this should not be interpreted as automatic payment verification or a fully integrated payment gateway.*

## 04. Installation & Usage

### Prerequisites

- Java Development Kit (JDK) compatible with the source code.
- MySQL Server.
- MySQL Connector/J 9.1.0.
- Visual Studio Code or another Java IDE.
- The project assets, including menu images, icons, fonts, and QR code.

### Database Configuration

1. Start the MySQL Server.
2. Create or import the `menu` database using `Database/menu.sql`.
3. Confirm that the `makanan`, `minuman`, and `jajan` tables contain the expected menu data.
4. Open `DatabaseConnection.java` and verify the connection configuration:

   ```java
   private static final String DB_URL =
       "jdbc:mysql://localhost:3306/menu";
   private static final String USER = "root";
   private static final String PASSWORD = "";
   ```

5. Update the username and password to match your local MySQL configuration.

**Security note:** The example uses local development credentials. Avoid committing real database passwords to a public repository.

### Configure the JDBC Driver

Ensure that `Driver/mysql-connector-j-9.1.0.jar` is included in the project's classpath.

### Run the Application

1. Open the project directory in Visual Studio Code.
2. Start MySQL and verify that the `menu` database is accessible.
3. Ensure that the Java source files and image assets are in their expected locations.
4. Configure the JDBC driver in the Java project.
5. Run `HalamanUtama.java`, which contains the application's `main()` method.
6. Select a menu category and add products to the cart.
7. Adjust product quantities and review the total order price.
8. Proceed to checkout, scan the displayed QR code using a compatible payment application, and follow the configured WhatsApp flow.

### Important Notes

- The application expects the database to be available at `localhost:3306/menu` unless the connection settings are changed.
- Image and font paths must match the project's directory structure.
- The checkout page opens a configured WhatsApp link; payment verification and order fulfillment are handled outside the application.
- Database schema details and exact menu records depend on the provided `menu.sql` file.
