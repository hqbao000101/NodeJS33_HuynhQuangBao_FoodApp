# DROP TABLE & COLUMN

DROP TABLE user;
DROP TABLE restaurant;
DROP TABLE rate_res;
DROP TABLE like_res;
DROP TABLE food;
DROP TABLE food_type;
DROP TABLE food_order;
DROP TABLE sub_food;

ALTER TABLE restaurant
ADD description VARCHAR(200);

# CREATE TABLE

CREATE TABLE user (
user_id INT PRIMARY KEY AUTO_INCREMENT,
full_name VARCHAR(50),
email VARCHAR(100),
password VARCHAR(100)
);

CREATE TABLE restaurant (
res_id INT PRIMARY KEY AUTO_INCREMENT,
res_name VARCHAR(100),
image VARCHAR(200),
description VARCHAR(200)
);

CREATE TABLE rate_res (
user_id INT,
res_id INT,
amount INT,
date_rate DATETIME,

PRIMARY KEY (user_id, res_id),
FOREIGN KEY (user_id) REFERENCES user(user_id),
FOREIGN KEY (res_id) REFERENCES restaurant(res_id)
);

CREATE TABLE like_res (
user_id INT,
res_id INT,
date_like DATETIME,

PRIMARY KEY (user_id, res_id),
FOREIGN KEY (user_id) REFERENCES user(user_id),
FOREIGN KEY (res_id) REFERENCES restaurant(res_id)
);

CREATE TABLE food_type (
type_id INT PRIMARY KEY AUTO_INCREMENT,
type_name VARCHAR(200)
);

CREATE TABLE food (
food_id INT PRIMARY KEY AUTO_INCREMENT,
food_name VARCHAR(200),
image VARCHAR(200),
price FLOAT,
description VARCHAR(200),
type_id INT,

FOREIGN KEY (type_id) REFERENCES food_type(type_id)
);

CREATE TABLE sub_food (
sub_id INT PRIMARY KEY AUTO_INCREMENT,
sub_name VARCHAR(100),
sub_price FLOAT,
food_id INT,

FOREIGN KEY (food_id) REFERENCES food(food_id)
);

CREATE TABLE food_order (
user_id INT,
food_id INT,
amount INT,
code VARCHAR(100),
arr_sub_id VARCHAR(200),

PRIMARY KEY (user_id, food_id),
FOREIGN KEY (user_id) REFERENCES user(user_id),
FOREIGN KEY (food_id) REFERENCES food(food_id)
);

# INSERT DATA

INSERT INTO user (full_name, email, password) VALUES
('John Doe', 'johndoe@example.com', 'password1'),
('Jane Doe', 'janedoe@example.com', 'password2'),
('Mary Smith', 'marysmith@example.com', 'password3'),
('Peter Jones', 'peterjones@example.com', 'password4'),
('Susan Brown', 'susanbrown@example.com', 'password5'),
('David Green', 'davidgreen@example.com', 'password6'),
('Emily White', 'emilywhite@example.com', 'password7'),
('Michael Black', 'michaelblack@example.com', 'password8'),
('Sarah Blue', 'sarahblue@example.com', 'password9'),
('William Red', 'williamred@example.com', 'password10');

INSERT INTO restaurant (res*name, image, description) VALUES
('La Scala', 'https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/La_Scala_Milan_Italy.jpg/1200px-La_Scala_Milan_Italy.jpg', 'La Scala is an opera house in Milan, Italy. It is one of the most famous opera houses in the world.'),
('The Fat Duck', 'https://upload.wikimedia.org/wikipedia/commons/thumb/7/70/The_Fat_Duck*%28restaurant%29*in_Bray.jpg/1200px-The_Fat_Duck*%28restaurant%29_in_Bray.jpg', 'The Fat Duck is a three-Michelin-starred restaurant in Bray, England. It is known for its innovative and experimental cuisine.'),
('Noma', 'https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Noma_restaurant_in_Copenhagen.jpg/1200px-Noma_restaurant_in_Copenhagen.jpg', 'Noma is a two-Michelin-starred restaurant in Copenhagen, Denmark. It is known for its Nordic cuisine.'),
('Eleven Madison Park', 'https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Eleven_Madison_Park_restaurant_in_Manhattan.jpg/1200px-Eleven_Madison_Park_restaurant_in_Manhattan.jpg', 'Eleven Madison Park is a three-Michelin-starred restaurant in Manhattan, New York City. It is known for its tasting menu.'),
('Per Se', 'https://upload.wikimedia.org/wikipedia/commons/thumb/c/c7/The_Modern_and_Per_Se.jpg/1200px-The_Modern_and_Per_Se.jpg', 'Per Se is a three-Michelin-starred restaurant in Manhattan, New York City. It is known for its American cuisine.'),
('The French Laundry', 'https://upload.wikimedia.org/wikipedia/commons/thumb/a/a3/The_French_Laundry_in_Yountville.jpg/1200px-The_French_Laundry_in_Yountville.jpg', 'The French Laundry is a three-Michelin-starred restaurant in Yountville, California. It is known for its traditional French cuisine.'),
('Mugaritz', 'https://upload.wikimedia.org/wikipedia/commons/thumb/0/05/Mugaritz_restaurant_in_Errenteria.jpg/1200px-Mugaritz_restaurant_in_Errenteria.jpg', 'Mugaritz is a three-Michelin-starred restaurant in Errenteria, Spain. It is known for its experimental cuisine.'),
('Dinner by Heston Blumenthal', 'https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Dinner_by_Heston_Blumenthal_restaurant_in_London.jpg/1200px-Dinner_by_Heston_Blumenthal_restaurant_in_London.jpg', 'Dinner by Heston Blumenthal is a two-Michelin-starred restaurant in London, England. It is known for its historical British cuisine.'),
('Central', 'https://upload.wikimedia.org/wikipedia/commons/thumb/f/f2/Central_restaurant_in_Lima.jpg/1200px-Central_restaurant_in_Lima.jpg', 'Central is a two-Michelin-starred restaurant in Lima, Peru. It is known for its Nikkei cuisine.');

INSERT INTO rate_res (user_id, res_id, amount, date_rate) VALUES
(1, 2, 5, '2023-07-31 22:00:00'),
(2, 6, 4, '2023-07-31 22:01:00'),
(3, 7, 3, '2023-07-31 22:02:00'),
(4, 1, 2, '2023-07-31 22:03:00'),
(5, 9, 1, '2023-07-31 22:04:00'),
(6, 3, 5, '2023-07-31 22:05:00'),
(7, 5, 4, '2023-07-31 22:06:00'),
(8, 2, 3, '2023-07-31 22:07:00'),
(9, 8, 2, '2023-07-31 22:08:00'),
(1, 4, 1, '2023-07-31 22:09:00');

INSERT INTO like_res (user_id, res_id, date_like) VALUES
(1, 5, '2023-07-31 22:10:00'),
(2, 6, '2023-07-31 22:11:00'),
(3, 2, '2023-07-31 22:12:00'),
(4, 9, '2023-07-31 22:13:00'),
(5, 9, '2023-07-31 22:14:00'),
(6, 4, '2023-07-31 22:15:00'),
(7, 3, '2023-07-31 22:16:00'),
(8, 1, '2023-07-31 22:17:00'),
(9, 7, '2023-07-31 22:18:00'),
(3, 3, '2023-07-31 22:19:00');

INSERT INTO food_type (type_name) VALUES
('Pizza'),
('Burger'),
('Sushi'),
('Ramen'),
('Fried Chicken'),
('Salad'),
('Ice Cream'),
('Steak'),
('Tacos'),
('Pasta');

INSERT INTO food (food_name, image, price, description, type_id) VALUES
('Margherita Pizza', 'https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/Pizza_margherita.jpg/1200px-Pizza_margherita.jpg', 10, 'A classic pizza with tomato sauce, mozzarella cheese, and basil.', 1),
('Cheeseburger', 'https://upload.wikimedia.org/wikipedia/commons/thumb/thumb/9/9b/Cheeseburger.jpg/1200px-Cheeseburger.jpg', 15, 'A classic burger with a beef patty, cheese, lettuce, tomato, and onion.', 2),
('Sushi Roll', 'https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/California_roll.jpg/1200px-California_roll.jpg', 12, 'A sushi roll with cucumber, avocado, and crab.', 3),
('Tonkotsu Ramen', 'https://upload.wikimedia.org/wikipedia/commons/thumb/a/a3/Tonkotsu_ramen_in_a_bowl.jpg/1200px-Tonkotsu_ramen_in_a_bowl.jpg', 13, 'A Japanese noodle soup made with pork bone broth, noodles, and toppings such as pork belly, scallions, and nori.', 4),
('Fried Chicken Sandwich', 'https://upload.wikimedia.org/wikipedia/commons/thumb/thumb/c/c2/Fried_chicken_sandwich.jpg/1200px-Fried_chicken_sandwich.jpg', 15, 'A sandwich with a fried chicken patty, lettuce, tomato, and mayonnaise.', 5),
('Caesar Salad', 'https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/Caesar_salad.jpg/1200px-Caesar_salad.jpg', 10, 'A salad with romaine lettuce, croutons, parmesan cheese, and a Caesar dressing.', 6),
('Ice Cream Sundae', 'https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/Ice_cream_sundae.jpg/1200px-Ice_cream_sundae.jpg', 12, 'A dessert with ice cream, whipped cream, chocolate sauce, and a cherry.', 7),
('Steak', 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/Steak_with_mushroom_sauce.jpg/1200px-Steak_with_mushroom_sauce.jpg', 25, 'A grilled piece of beef.', 8),
('Tacos', 'https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Tacos_al_pastor.jpg/1200px-Tacos_al_pastor.jpg', 10, 'A Mexican dish made with corn tortillas, grilled meat, and toppings such as cilantro, onions, and salsa.', 9),
('Pasta Carbonara', 'https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/Pasta_carbonara.jpg/1200px-Pasta_carbonara.jpg', 12, 'An Italian pasta dish made with spaghetti, bacon, eggs, and Parmesan cheese.', 10);

INSERT INTO sub_food (sub_name, sub_price, food_id) VALUES
('Margherita Pizza with Pepperoni', 12, 1),
('Cheeseburger with Bacon', 17, 2),
('Sushi Roll with Salmon', 14, 3),
('Tonkotsu Ramen with Extra Toppings', 16, 9),
('Fried Chicken Sandwich with Waffle Fries', 18, 5),
('Caesar Salad with Grilled Chicken', 13, 6),
('Ice Cream Sundae with Whipped Cream and Sprinkles', 14, 7),
('Steak with Mushroom Sauce and Mashed Potatoes', 30, 8),
('Tacos with Chicken and Cilantro Lime Slaw', 12, 9),
('Pasta Carbonara with Shrimp', 15, 9),
('Veggie Pizza with Spinach and Mushrooms', 11, 1),
('Chicken Burger with Lettuce and Tomato', 15, 2),
('California Roll with Avocado and Tuna', 13, 3),
('Vegetable Ramen with Tofu and Edamame', 15, 3),
('Chicken Sandwich with Sweet Potato Fries', 16, 7),
('Greek Salad with Feta Cheese and Olives', 12, 6),
('Chocolate Sundae with Caramel Sauce and Cherries', 15, 7),
('Steak with Blue Cheese Butter and Asparagus', 32, 8),
('Tacos with Fish and Pico de Gallo', 13, 9),
('Pasta alla Norma with Eggplant and Tomato Sauce', 16, 10);

INSERT INTO food_order (user_id, food_id, amount, code, arr_sub_id) VALUES
(1, 1, 1, 'ABC123', '1'),
(2, 2, 2, 'DEF456', '2'),
(3, 3, 3, 'GHI789', '3'),
(4, 4, 4, 'JKL012', '4'),
(5, 5, 5, 'MNO345', '5,8,9'),
(6, 6, 6, 'PQR678', '6'),
(7, 7, 3, 'STU901', '7,1,11,17'),
(8, 8, 3, 'VWX234', '8'),
(9, 9, 9, 'YZ1567', '9'),
(4, 10, 3, 'AA0789', '10'),
(1, 9, 1, 'BB1234', '1,2'),
(2, 8, 2, 'CC5678', '3,4'),
(3, 8, 3, 'DD9012', '5,6'),
(4, 8, 4, 'EE3456', '7,8'),
(5, 6, 12, 'FF7890', '9,10'),
(6, 3, 6, 'GG1234', '11,12,7'),
(9, 4, 7, 'HH5678', '13,14,10'),
(8, 1, 8, 'II9012', '15,16'),
(9, 1, 9, 'JJ3456', '17,18'),
(4, 2, 7, 'KK7890', '19,20');

# MySQL Queries
