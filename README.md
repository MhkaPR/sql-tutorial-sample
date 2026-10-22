```sql
-- جدول مشتریان
CREATE TABLE customers (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    city TEXT,
    age INTEGER,
    email TEXT UNIQUE
);

-- جدول محصولات
CREATE TABLE products (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    price REAL,
    stock INTEGER,
    category_id INTEGER
);

-- جدول دسته‌بندی‌ها
CREATE TABLE categories (
    id INTEGER PRIMARY KEY,
    title TEXT NOT NULL
);

-- جدول سفارشات
CREATE TABLE orders (
    id INTEGER PRIMARY KEY,
    customer_id INTEGER,
    order_date TEXT,
    total REAL,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

-- جدول آیتم‌های سفارش (رابطه چند به چند)
CREATE TABLE order_items (
    id INTEGER PRIMARY KEY,
    order_id INTEGER,
    product_id INTEGER,
    quantity INTEGER,
    price REAL,
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);

---
```
```sql
-- ==================== دسته‌بندی‌ها ====================

INSERT INTO categories (id, title) VALUES
(1, 'لپ‌تاپ'),
(2, 'موبایل'),
(3, 'لوازم جانبی'),
(4, 'تبلت'),
(5, 'کنسول بازی');

-- ==================== مشتریان ====================

INSERT INTO customers (id, name, city, age, email) VALUES
(1,  'مهدی رضایی',    'تهران',   28, 'mehdi@example.com'),
(2,  'زهرا محمدی',    'تهران',   35, 'zahra@example.com'),
(3,  'علی کریمی',     'مشهد',    42, 'ali@example.com'),
(4,  'مریم حسینی',    'اصفهان',  31, 'maryam@example.com'),
(5,  'رضا نوری',      'تهران',   19, NULL),
(6,  'سارا احمدی',    'شیراز',   27, 'sara@example.com'),
(7,  'حسن موسوی',     'تهران',   55, 'hasan@example.com'),
(8,  'نگار قاسمی',    'مشهد',    23, 'negar@example.com'),
(9,  'امیر عباسی',    'تبریز',   38, 'amir@example.com'),
(10, 'فاطمه صادقی',   'تهران',   16, NULL),
(11, 'کاوه رستمی',    'اصفهان',  45, 'kaveh@example.com'),
(12, 'لیلا شریفی',    'شیراز',   29, 'leila@example.com');

-- ==================== محصولات ====================

INSERT INTO products (id, name, price, stock, category_id) VALUES
(1,  'لپ‌تاپ ایسوس VivoBook',   25000000, 15, 1),
(2,  'لپ‌تاپ لنوو ThinkPad',    38000000, 8,  1),
(3,  'لپ‌تاپ اپل MacBook Air',  55000000, 5,  1),
(4,  'گوشی سامسونگ S23',        32000000, 20, 2),
(5,  'گوشی شیائومی Redmi',      9000000,  50, 2),
(6,  'گوشی اپل iPhone 15',      62000000, 12, 2),
(7,  'هدفون سونی WH-1000',      12000000, 30, 3),
(8,  'ماوس لاجیتک MX',          2500000,  100,3),
(9,  'کیبورد مکانیکی رزر',      4500000,  40, 3),
(10, 'تبلت آیپد ایر',           28000000, 10, 4),
(11, 'تبلت سامسونگ Tab S9',     22000000, 14, 4),
(12, 'پلی‌استیشن 5',            45000000, 6,  5),
(13, 'ایکس‌باکس Series X',      43000000, 4,  5),
(14, 'پاوربانک انکر',           1200000,  200,3),
(15, 'شارژر سریع سامسونگ',      800000,   150,3);

-- ==================== سفارشات ====================

INSERT INTO orders (id, customer_id, order_date, total) VALUES
(1,  1,  '1403-01-15', 25000000),
(2,  1,  '1403-02-20', 14500000),
(3,  2,  '1403-01-18', 62000000),
(4,  3,  '1403-02-05', 38000000),
(5,  4,  '1403-03-01', 28000000),
(6,  4,  '1403-03-12', 9000000),
(7,  6,  '1403-02-25', 12000000),
(8,  7,  '1403-03-10', 55000000),
(9,  8,  '1403-03-15', 4500000),
(10, 9,  '1403-03-18', 45000000),
(11, 2,  '1403-03-20', 22000000),
(12, 11, '1403-03-22', 32000000),
(13, 12, '1403-03-25', 2500000),
(14, 1,  '1403-04-01', 1200000),
(15, 6,  '1403-04-05', 4500000);

-- ==================== آیتم‌های سفارش ====================

INSERT INTO order_items (id, order_id, product_id, quantity, price) VALUES
(1,  1,  1,  1, 25000000),
(2,  2,  7,  1, 12000000),
(3,  2,  8,  1, 2500000),
(4,  3,  6,  1, 62000000),
(5,  4,  2,  1, 38000000),
(6,  5,  10, 1, 28000000),
(7,  6,  5,  1, 9000000),
(8,  7,  7,  1, 12000000),
(9,  8,  3,  1, 55000000),
(10, 9,  9,  1, 4500000),
(11, 10, 12, 1, 45000000),
(12, 11, 11, 1, 22000000),
(13, 12, 4,  1, 32000000),
(14, 13, 8,  1, 2500000),
(15, 14, 14, 1, 1200000),
(16, 15, 9,  1, 4500000),
(17, 1,  8,  2, 2500000),
(18, 3,  7,  1, 12000000),
(19, 4,  9,  1, 4500000),
(20, 10, 13, 1, 43000000);

```
