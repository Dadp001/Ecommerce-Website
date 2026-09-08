# E-Commerce Website

A responsive **frontend e-commerce website** built using **HTML, CSS, and JavaScript**.

The project simulates an online fashion store with product listings, product details, shopping-cart functionality, and client-side state management. The shopping cart is implemented using JavaScript and persisted in the browser using `LocalStorage`.

> This project is a frontend demonstration and does not include a backend, database, real payment processing, or user authentication.

---

## Features

* Responsive e-commerce website interface
* Home page with promotional sections
* Product listing pages
* Individual product detail page
* Product image gallery
* Shopping cart functionality
* Add products to cart
* Increase product quantity when the same product is added again
* Remove/decrease product quantity
* Dynamic cart display
* Dynamic subtotal calculation
* Cart persistence using `LocalStorage`
* Shopping-cart item count
* Blog page
* Responsive navigation and layout
* Simulated checkout interaction

---

## Tech Stack

* **HTML5** — Page structure and content
* **CSS3** — Styling, layout and responsive design
* **JavaScript** — User interactions, cart logic and client-side state management
* **LocalStorage** — Persistent cart data in the browser
* **Font Awesome** — Icons used throughout the interface

---

## Project Structure

```text
E-Commerce-Website/
│
├── index.html
├── shop.html
├── shop2.html
├── shop3.html
├── sproduct.html
├── blog.html
│
├── script.js
├── style.css
│
└── img/
    ├── products/
    ├── shop/
    ├── features/
    └── pay/
```

---

## Application Pages

### Home Page

The home page provides the main landing experience for the website, including:

* Navigation bar
* Promotional hero section
* Product-related sections
* Feature highlights
* Newsletter section
* Footer

---

### Shop Pages

The shop pages display products in a structured product grid.

Each product contains information such as:

* Product image
* Product name
* Description
* Price
* Product ID
* Add-to-cart functionality

Products are identified using a unique `data-id` attribute, which is used by the JavaScript cart logic.

---

### Product Details

The individual product page provides a detailed view of a product along with multiple product images.

The interface includes a main product image and smaller product images that can be used to display different views of the product.

---

### Blog

The website also contains a blog section as part of the overall e-commerce interface.

---

# Shopping Cart

The main interactive functionality of the project is the shopping cart.

The cart is implemented using JavaScript classes:

```text
CartItem
LocalCart
```

### CartItem

The `CartItem` class represents an individual product added to the cart.

It stores:

```text
Product Name
Description
Image
Price
Quantity
```

A newly created cart item starts with a quantity of `1`.

---

## Add to Cart Flow

When a user clicks **Add to Cart**, the application:

```text
User clicks Add to Cart
          |
          v
Retrieve Product ID
          |
          v
Read Product Information
          |
          v
Create CartItem
          |
          v
Check Existing Cart
          |
          v
Add Item / Increase Quantity
          |
          v
Save Cart to LocalStorage
          |
          v
Update Cart UI
```

The JavaScript retrieves the product ID, image, name, description and price from the product element and creates a `CartItem`.

---

## Handling Duplicate Products

The application uses the product ID to determine whether a product is already present in the cart.

If the product already exists:

```text
quantity = quantity + 1
```

Otherwise, a new cart item is created.

This prevents the same product from appearing as multiple separate entries in the cart.

---

## Removing Items

When a user removes an item from the cart:

```text
If quantity > 1
        |
        v
Decrease quantity by 1

Otherwise
        |
        v
Remove product from cart
```

The updated cart is then saved back to `LocalStorage` and the interface is refreshed.

---

# LocalStorage

Since the project is a frontend-only application, `LocalStorage` is used to persist the shopping-cart state in the browser.

The cart uses:

```text
cartItems
```

as its storage key.

The data is stored as JSON.

### Saving Data

```text
JavaScript Object
       |
       v
JSON.stringify()
       |
       v
LocalStorage
```

### Reading Data

```text
LocalStorage
       |
       v
JSON.parse()
       |
       v
JavaScript Object
```

This allows the cart information to remain available after refreshing the page.

---

# Cart State Management

The project uses JavaScript to maintain the current cart state.

Whenever the cart changes, the application:

```text
Cart State Changes
        |
        v
Update LocalStorage
        |
        v
updateCartUI()
        |
        v
Regenerate Cart Display
        |
        v
Update Quantity / Subtotal
```

The `updateCartUI()` function reads the current cart, dynamically creates the cart elements and calculates the total price.

The cart is also initialized when the page loads so that previously stored items can be displayed.

---

# Subtotal Calculation

For each product in the cart, the subtotal is calculated as:

```text
Subtotal = Product Price × Quantity
```

For example:

```text
Product A
$50 × 2 = $100

Product B
$30 × 1 = $30

Total Subtotal = $130
```

The JavaScript calculates these values dynamically whenever the cart UI is updated.

---

# Responsive Design

The website uses CSS to create a responsive layout that adapts to different screen sizes.

The styling includes layouts for:

* Navigation
* Hero sections
* Product grids
* Product details
* Shopping cart
* Footer
* Other website sections

The HTML pages also include the responsive viewport configuration:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

---

# User Interaction Flow

A typical shopping flow is:

```text
Open Website
     |
     v
Browse Products
     |
     v
Open Product
     |
     v
Add to Cart
     |
     v
Shopping Cart Updated
     |
     v
Modify Quantity / Remove Item
     |
     v
Subtotal Recalculated
     |
     v
Simulated Checkout
```

The shopping bag is displayed through an interactive cart interface, with the cart contents generated dynamically by JavaScript.

---

# Getting Started

## 1. Clone the Repository

```bash
git clone <repository-url>
```

## 2. Open the Project

Open the project folder in a code editor such as **Visual Studio Code**.

## 3. Run the Website

Open:

```text
index.html
```

in a web browser.

For the best development experience, you can use a local development server such as the **Live Server** extension in Visual Studio Code.

---

# How the Cart Works

The overall cart architecture can be summarized as:

```text
                 PRODUCT
                    |
                    v
             Add to Cart
                    |
                    v
              Product ID
                    |
                    v
              CartItem
                    |
                    v
              LocalCart
                    |
             +------+------+
             |             |
             v             v
        New Product    Existing Product
             |             |
             |             v
             |        Increase Quantity
             |             |
             +------+------+
                    |
                    v
              LocalStorage
                    |
                    v
             updateCartUI()
                    |
             +------+------+
             |             |
             v             v
        Cart Display    Subtotal
```

---

# Limitations

This project is a frontend demonstration and has several limitations:

* No backend server
* No database
* No user authentication
* No real order management
* No real payment gateway
* Product information is handled on the frontend
* Cart state is stored locally in the browser
* Cart data is not synchronized between different devices or browsers
* The checkout interaction is simulated rather than processing a real transaction

---

# Future Improvements

The project could be extended into a full-stack e-commerce application by adding:

### Backend

* REST APIs
* User authentication
* Product management
* Order management
* Inventory management

### Database

A database could be introduced to store:

```text
Users
Products
Orders
Cart Data
Payments
Inventory
```

### Additional Features

* User registration and login
* Product search
* Product filtering
* Product categories
* Wishlist
* Real checkout process
* Payment gateway integration
* Order history
* Order tracking
* Admin dashboard
* Backend-based cart synchronization

A production architecture could look like:

```text
             Frontend
        HTML / CSS / JS
                |
                v
           REST API
                |
                v
             Backend
                |
        +-------+-------+
        |               |
        v               v
     Database       Payment API
```

---

# Key Learning Outcomes

Through this project, I gained practical experience with:

* HTML page structuring
* CSS-based responsive design
* JavaScript DOM manipulation
* Event handling
* Object-oriented JavaScript
* Client-side state management
* Browser `LocalStorage`
* JSON serialization and parsing
* Dynamic UI generation
* Shopping-cart logic
* Basic e-commerce user flows

