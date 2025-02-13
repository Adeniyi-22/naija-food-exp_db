CREATE DATABASE  IF NOT EXISTS `naija_food_express` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */;
USE `naija_food_express`;
-- MySQL dump 10.13  Distrib 8.0.40, for Win64 (x86_64)
--
-- Host: localhost    Database: naija_food_express
-- ------------------------------------------------------
-- Server version	8.0.40

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!50503 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `deliveries`
--

DROP TABLE IF EXISTS `deliveries`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `deliveries` (
  `delivery_id` int NOT NULL AUTO_INCREMENT,
  `order_id` int DEFAULT NULL,
  `delivery_address` text NOT NULL,
  `delivery_status` enum('pending','out for delivery','delivered') DEFAULT 'pending',
  `delivery_date` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`delivery_id`),
  KEY `order_id` (`order_id`),
  CONSTRAINT `deliveries_ibfk_1` FOREIGN KEY (`order_id`) REFERENCES `orders` (`order_id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `deliveries`
--

LOCK TABLES `deliveries` WRITE;
/*!40000 ALTER TABLE `deliveries` DISABLE KEYS */;
INSERT INTO `deliveries` VALUES (1,1,'12, opebi Street, Ikeja','pending','2025-02-12 20:43:16'),(2,2,'45, Victoria Island, Lagos','out for delivery','2025-02-12 20:43:16'),(3,3,'5, Surulere, Lagos','delivered','2025-02-12 20:43:16'),(4,4,'22, Yaba, Lagos','pending','2025-02-12 20:43:16'),(5,5,'18, Lekki Phase 1, Lagos','out for delivery','2025-02-12 20:43:16'),(6,6,'10, Ikorodu Road, Lagos','delivered','2025-02-12 20:43:16');
/*!40000 ALTER TABLE `deliveries` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `order_items`
--

DROP TABLE IF EXISTS `order_items`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `order_items` (
  `order_item_id` int NOT NULL AUTO_INCREMENT,
  `order_id` int DEFAULT NULL,
  `product_id` int DEFAULT NULL,
  `quantity` int NOT NULL,
  `price` decimal(10,2) NOT NULL,
  PRIMARY KEY (`order_item_id`),
  KEY `order_id` (`order_id`),
  KEY `product_id` (`product_id`),
  CONSTRAINT `order_items_ibfk_1` FOREIGN KEY (`order_id`) REFERENCES `orders` (`order_id`) ON DELETE CASCADE,
  CONSTRAINT `order_items_ibfk_2` FOREIGN KEY (`product_id`) REFERENCES `products` (`product_id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=9 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `order_items`
--

LOCK TABLES `order_items` WRITE;
/*!40000 ALTER TABLE `order_items` DISABLE KEYS */;
INSERT INTO `order_items` VALUES (1,1,1,2,24000.00),(2,1,5,3,4500.00),(3,2,3,1,7000.00),(4,3,14,1,15000.00),(5,4,18,2,8000.00),(6,5,10,4,12000.00),(7,6,15,3,22500.00),(8,6,12,2,14000.00);
/*!40000 ALTER TABLE `order_items` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `orders`
--

DROP TABLE IF EXISTS `orders`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `orders` (
  `order_id` int NOT NULL AUTO_INCREMENT,
  `user_id` int DEFAULT NULL,
  `total_price` decimal(10,2) NOT NULL,
  `status` enum('pending','processing','shipped','delivered') DEFAULT 'pending',
  PRIMARY KEY (`order_id`),
  KEY `user_id` (`user_id`),
  CONSTRAINT `orders_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `users` (`user_id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `orders`
--

LOCK TABLES `orders` WRITE;
/*!40000 ALTER TABLE `orders` DISABLE KEYS */;
INSERT INTO `orders` VALUES (1,1,18500.00,'processing'),(2,2,7000.00,'pending'),(3,3,15000.00,'shipped'),(4,4,4000.00,'delivered'),(5,5,12000.00,'processing'),(6,6,25000.00,'shipped');
/*!40000 ALTER TABLE `orders` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `payments`
--

DROP TABLE IF EXISTS `payments`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `payments` (
  `payment_id` int NOT NULL AUTO_INCREMENT,
  `order_id` int DEFAULT NULL,
  `user_id` int DEFAULT NULL,
  `amount` decimal(10,2) NOT NULL,
  `payment_method` enum('card','transfer','cash_on_delivery') NOT NULL,
  `payment_status` enum('pending','successful','failed') DEFAULT 'pending',
  `payment_date` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`payment_id`),
  KEY `order_id` (`order_id`),
  KEY `user_id` (`user_id`),
  CONSTRAINT `payments_ibfk_1` FOREIGN KEY (`order_id`) REFERENCES `orders` (`order_id`) ON DELETE CASCADE,
  CONSTRAINT `payments_ibfk_2` FOREIGN KEY (`user_id`) REFERENCES `users` (`user_id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `payments`
--

LOCK TABLES `payments` WRITE;
/*!40000 ALTER TABLE `payments` DISABLE KEYS */;
INSERT INTO `payments` VALUES (1,1,1,18500.00,'card','successful','2025-02-12 21:26:43'),(2,2,2,7000.00,'transfer','successful','2025-02-12 21:26:43'),(3,3,3,15000.00,'cash_on_delivery','pending','2025-02-12 21:26:43'),(4,4,4,4000.00,'card','successful','2025-02-12 21:26:43'),(5,5,5,12000.00,'transfer','failed','2025-02-12 21:26:43'),(6,6,6,25000.00,'cash_on_delivery','successful','2025-02-12 21:26:43');
/*!40000 ALTER TABLE `payments` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `products`
--

DROP TABLE IF EXISTS `products`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `products` (
  `product_id` int NOT NULL AUTO_INCREMENT,
  `vendor_id` int DEFAULT NULL,
  `name` varchar(255) NOT NULL,
  `description` text,
  `price` decimal(10,2) NOT NULL,
  `stock_quantity` int NOT NULL,
  `category` varchar(255) DEFAULT NULL,
  `image_url` text,
  PRIMARY KEY (`product_id`),
  KEY `vendor_id` (`vendor_id`),
  CONSTRAINT `products_ibfk_1` FOREIGN KEY (`vendor_id`) REFERENCES `vendors` (`vendor_id`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=21 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `products`
--

LOCK TABLES `products` WRITE;
/*!40000 ALTER TABLE `products` DISABLE KEYS */;
INSERT INTO `products` VALUES (1,1,'Rice','Premium long grain rice',12000.00,100,'Grains','image_url'),(2,2,'Beans','Oloyin honey beans',8500.00,80,'Legumes','image_url'),(3,3,'Garri','Ijebu garri, yellow',7000.00,60,'Grains','image_url'),(4,4,'Yam','Fresh tubers of yam',2000.00,50,'Root Crops','image_url'),(5,5,'Plantain','Ripe plantains',1500.00,70,'Fruits','image_url'),(6,1,'Palm Oil','Fresh palm oil',5000.00,90,'Oils','image_url'),(7,2,'Groundnut Oil','Pure groundnut oil',6000.00,75,'Oils','image_url'),(8,3,'Pepper','Dried chili pepper',1200.00,100,'Spices','image_url'),(9,4,'Tomato Paste','Canned tomato paste',800.00,120,'Canned Goods','image_url'),(10,5,'Egusi','Melon seeds for soup',3000.00,50,'Spices','image_url'),(11,1,'Ogbono','Wild mango seeds for soup',3500.00,40,'Spices','image_url'),(12,2,'Stock Fish','Dried stock fish',7000.00,30,'Seafood','image_url'),(13,3,'Crayfish','Ground crayfish',2500.00,90,'Seafood','image_url'),(14,4,'Goat Meat','Fresh goat meat',15000.00,25,'Meat','image_url'),(15,5,'Chicken','Whole fresh chicken',7500.00,40,'Meat','image_url'),(16,1,'Ponmo','Dried cow skin',5000.00,60,'Meat','image_url'),(17,2,'Snail','Live snails',10000.00,20,'Meat','image_url'),(18,3,'Periwinkle','Fresh periwinkle',4000.00,50,'Seafood','image_url'),(19,4,'Bitter Leaf','Dried bitter leaf',2000.00,70,'Vegetables','image_url'),(20,5,'Okro','Fresh okro',1000.00,100,'Vegetables','image_url');
/*!40000 ALTER TABLE `products` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `users`
--

DROP TABLE IF EXISTS `users`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `users` (
  `user_id` int NOT NULL AUTO_INCREMENT,
  `full_name` varchar(255) NOT NULL,
  `email` varchar(255) NOT NULL,
  `phone` varchar(20) NOT NULL,
  `password_hash` varchar(255) NOT NULL,
  `address` text NOT NULL,
  PRIMARY KEY (`user_id`),
  UNIQUE KEY `email` (`email`),
  UNIQUE KEY `phone` (`phone`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `users`
--

LOCK TABLES `users` WRITE;
/*!40000 ALTER TABLE `users` DISABLE KEYS */;
INSERT INTO `users` VALUES (1,'Johnson Ade','johnsonade22@gmail.com','08123456789','hashed_password','12, opebi Street, Ikeja'),(2,'Chima Smith','csmith@yahoo.com','08098765432','hashed_password','45, Victoria Island, Lagos'),(3,'Emeka Okonkwo','emekaokonkwo@gmail.com','08134567890','hashed_password','5, Surulere, Lagos'),(4,'Amina Bello','aminabello@gmail.com','08023456789','hashed_password','22, Yaba, Lagos'),(5,'Bolu Adesanya','boluadesanya@gmail.com','09012345678','hashed_password','18, Lekki Phase 1, Lagos'),(6,'Fatima Ibrahim','fatimaibrahim@gmail.com','08076543210','hashed_password','10, Ikorodu Road, Lagos');
/*!40000 ALTER TABLE `users` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `vendors`
--

DROP TABLE IF EXISTS `vendors`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `vendors` (
  `vendor_id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  `email` varchar(255) NOT NULL,
  `phone` varchar(20) NOT NULL,
  `address` text NOT NULL,
  PRIMARY KEY (`vendor_id`),
  UNIQUE KEY `email` (`email`),
  UNIQUE KEY `phone` (`phone`)
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `vendors`
--

LOCK TABLES `vendors` WRITE;
/*!40000 ALTER TABLE `vendors` DISABLE KEYS */;
INSERT INTO `vendors` VALUES (1,'Mama Ope Foods','mamaope@gmail.com','08011223344','12, Balogun Market, Lagos'),(2,'Fresh Farm Market','freshfarm@gmail.com','08122334455','24, Oyingbo Market, Lagos'),(3,'Bisi Agro Store','bisiagro@gmail.com','08033445566','15, Ketu Market, Lagos'),(4,'Lagos Food Hub','lagosfoodhub@gmail.com','09055667788','30, Mushin Market, Lagos'),(5,'Eko Fresh Foods','ekofresh@gmail.com','08166778899','7, Oshodi Market, Lagos');
/*!40000 ALTER TABLE `vendors` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2025-02-13  3:14:48
