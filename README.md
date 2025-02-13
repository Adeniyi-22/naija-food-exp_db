# Naija Food Express Database

This repository contains the MySQL database for Naija Food Express, an online store for ordering and delivering Nigerian foodstuffs in Lagos State.

# Database Details
  - Database Name: `naija_food_express`
  - Tables Included:
  - `users` (Customer information)
  - `vendors` (List of vendors selling foodstuffs)
  - `products` (Available Nigerian foodstuffs)
  - `orders` (Customer orders)
  - `payments` (Payment records)
  - `deliveries` (Delivery tracking)
  
      - Exported File: `nfd_db.sql`

---

# How to Import the Database
Follow these steps to import the database into MySQL:

# Using MySQL Workbench 8.0 CE
1. Download the file `nfd_db.sql` from this repository.
2. Open MySQL Workbench and connect to your MySQL server.
3. Create a new database:
   ```sql
   CREATE DATABASE naija_food_express;

- Click Server → Data Import.
- Select "Import from Self-Contained File" and choose nfd_db.sql.
- Click Start Import and wait for the process to complete.
Done! Your database is now ready.

# How to Use This Database
- Developers can integrate this database with a web or mobile app for food ordering.
- Admins can manage users, products, orders, and deliveries using SQL queries.
- Customers can place orders and leave reviews.

# Contact:
For any inquiries, please contact Email: adeniyinifemi330@gmail.com
 GitHub: https://github.com/Adeniyi-22
