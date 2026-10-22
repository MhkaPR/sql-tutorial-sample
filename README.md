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
