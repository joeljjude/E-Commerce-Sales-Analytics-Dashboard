# Database Schema Plan

## Customers Table

| Column      | Data Type         | Description                           |
|-------------|-------------------|---------------------------------------|
| customer_id | INT, PRIMARY KEY  | Unique identifier for customer        |
| first_name  | VARCHAR           | Customer's first name                 |
| last_name   | VARCHAR           | Customer's last name                  |
| email       | VARCHAR           | Contact email                         |
| phone       | VARCHAR           | Contact phone number                  |
| address     | VARCHAR           | Customer address                      |

## Products Table

| Column      | Data Type         | Description                           |
|-------------|-------------------|---------------------------------------|
| product_id  | INT, PRIMARY KEY  | Unique identifier for product         |
| product_name| VARCHAR           | Product name                          |
| description | TEXT              | Product description                   |
| price       | DECIMAL           | Price per unit                        |
| stock       | INT               | Stock quantity                        |

## Orders Table

| Column      | Data Type         | Description                           |
|-------------|-------------------|---------------------------------------|
| order_id    | INT, PRIMARY KEY  | Unique identifier for order           |
| customer_id | INT, FOREIGN KEY  | Link to Customers table               |
| order_date  | DATE              | Date of order placement               |
| status      | VARCHAR           | Order status                          |

## Order_Items Table

| Column       | Data Type        | Description                           |
|--------------|------------------|---------------------------------------|
| order_item_id| INT, PRIMARY KEY | Unique ID for each line item          |
| order_id     | INT, FOREIGN KEY | Links to Orders table                 |
| product_id   | INT, FOREIGN KEY | Links to Products table               |
| quantity     | INT              | Quantity of product                   |
| total_price  | DECIMAL          | Total for this line item              |

## Sales Table

| Column       | Data Type        | Description                           |
|--------------|------------------|---------------------------------------|
| sale_id      | INT, PRIMARY KEY | Unique identifier for sale            |
| order_id     | INT, FOREIGN KEY | Links to Orders table                 |
| sale_date    | DATE             | Date the sale was completed           |
| total_amount | DECIMAL          | Total sale amount                     |