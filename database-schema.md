# Database Schema Plan with Relationships

## Customers Table

| Column      | Data Type         | Constraints           | Description                           |
|-------------|-------------------|-----------------------|---------------------------------------|
| customer_id | INT, PRIMARY KEY  | NOT NULL, UNIQUE      | Unique identifier for customer        |
| first_name  | VARCHAR           | NOT NULL              | Customer's first name                 |
| last_name   | VARCHAR           | NOT NULL              | Customer's last name                  |
| email       | VARCHAR           | NOT NULL, UNIQUE      | Contact email                         |
| phone       | VARCHAR           |                       | Contact phone number                  |
| address     | VARCHAR           |                       | Customer address                      |

## Products Table

| Column      | Data Type         | Constraints           | Description                           |
|-------------|-------------------|-----------------------|---------------------------------------|
| product_id  | INT, PRIMARY KEY  | NOT NULL, UNIQUE      | Unique identifier for product         |
| product_name| VARCHAR           | NOT NULL              | Product name                          |
| description | TEXT              |                       | Product description                   |
| price       | DECIMAL           | NOT NULL              | Price per unit                        |
| stock       | INT               | NOT NULL              | Stock quantity                        |

## Orders Table

| Column      | Data Type         | Constraints                       | Description                           |
|-------------|-------------------|-----------------------------------|---------------------------------------|
| order_id    | INT, PRIMARY KEY  | NOT NULL, UNIQUE                  | Unique identifier for order           |
| customer_id | INT, FOREIGN KEY  | NOT NULL, references Customers(customer_id) | Links to Customers table              |
| order_date  | DATE              | NOT NULL                          | Date of order placement               |
| status      | VARCHAR           |                                   | Order status                          |

## Order_Items Table

| Column       | Data Type        | Constraints                               | Description                           |
|--------------|------------------|-------------------------------------------|---------------------------------------|
| order_item_id| INT, PRIMARY KEY | NOT NULL, UNIQUE                          | Unique ID for each line item          |
| order_id     | INT, FOREIGN KEY | NOT NULL, references Orders(order_id)     | Links to Orders table                 |
| product_id   | INT, FOREIGN KEY | NOT NULL, references Products(product_id) | Links to Products table               |
| quantity     | INT              | NOT NULL                                  | Quantity of product                   |
| total_price  | DECIMAL          |                                           | Total for this line item              |

## Sales Table

| Column       | Data Type        | Constraints                       | Description                           |
|--------------|------------------|-----------------------------------|---------------------------------------|
| sale_id      | INT, PRIMARY KEY | NOT NULL, UNIQUE                  | Unique identifier for sale            |
| order_id     | INT, FOREIGN KEY | NOT NULL, references Orders(order_id) | Links to Orders table                 |
| sale_date    | DATE             | NOT NULL                          | Date the sale was completed           |
| total_amount | DECIMAL          | NOT NULL                          | Total sale amount                     |
