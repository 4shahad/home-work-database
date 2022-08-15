
#DDL
create table countries(
    code int primary key ,
    name varchar(20) unique ,
    continent_name varchar(20)not null
);
create table users(
    id int primary key ,
    full_name varchar(20),
    email varchar(20) unique ,
    gender char(1) check ( gender='m'or gender='f' ),
    date_of_birth varchar(15),
    created_at datetime,
    country_code int ,
    foreign key (country_code)references countries(code)
);
create table orders(
    id int primary key ,
    user_id int ,
    status varchar(6)check ( status='start'or status='finish' ),
    created_at datetime ,
    foreign key (user_id)references users(id)
);
create table orders_products(
    order_id int  ,
    product_id int  ,
    quantity int default 0,
    primary key (order_id,product_id),
    foreign key (order_id)references orders(id),
    foreign key (product_id)references products(id)
);
create table products(
    id int primary key ,
    name varchar(10) not null ,
    price int default 0,
    status varchar(10) check ( status='valid'or status='expired' ),
    created_at datetime

);
alter table products alter column created_at set default now();
alter table orders alter column created_at set default now();
alter table users alter column created_at set default now();

#DML

INSERT into users values (1001,'shahad rashed','aishfjs@gdkjg.com','f','1997','2022/08/15 22:34',99922);
INSERT into countries values (2030,'KSA','Asia');
INSERT into countries values (2077,'Egept','Asia');
INSERT into orders values (234,1001,'start','2022/08/15 22:34');
INSERT into products values (5674,'clothes',50,'valid','2022/08/15 22:34');
INSERT into products values (5644,'food',67,'valid','2022/08/15 22:34');
INSERT into orders_products values (234,5674,30);
update countries set continent_name='Afriga'where code=2077;
delete from products where id=5644;



