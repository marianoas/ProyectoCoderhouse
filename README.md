# ProyectoCoderhouse

-- Creacion de base de datos Banco--
CREATE DATABASE Banco;
USE Banco;
-- Tabla cliente--
CREATE TABLE Cliente(
id_cliente INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
nombre VARCHAR(20) NOT NULL,
apellido VARCHAR(20) NOT NULL,
DNI INT NOT NULL UNIQUE,
fecha_nacimiento DATE NOT NULL,
ciudad INT NOT NULL,
direccion VARCHAR(50) NOT NULL,
telefono INT NOT NULL,
correo_electronico VARCHAR(20) NOT NULL);

-- Tabla cuenta--
CREATE TABLE Cuenta(
numero_cuenta INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
id_cliente INT NOT NULL,
tipo_cuenta VARCHAR(20) NOT NULL,
saldo INT NOT NULL,
moneda VARCHAR(20) NOT NULL,
fecha_apertura DATE NOT NULL,
id_sucursal INT NOT NULL,
estado VARCHAR(20) NOT NULL) AUTO_INCREMENT = 10000;

ALTER TABLE Cuenta
ADD CONSTRAINT FK_id_cliente
FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente);

ALTER TABLE Cuenta
ADD CONSTRAINT FK_id_sucursal_cuenta
FOREIGN KEY (id_sucursal) REFERENCES Sucursal(id_sucursal);

-- Tabla sucursal--
CREATE TABLE Sucursal(
id_sucursal INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
Nombre_sucursal VARCHAR(20) NOT NULL);

-- Tabla empleados--
CREATE TABLE Empleados(
id_empleados INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
nombre VARCHAR(20) NOT NULL,
apellido VARCHAR(20) NOT NULL,
cargo VARCHAR(20) NOT NULL,
id_sucursal INT NOT NULL);
-- foreign key 
ALTER TABLE Empleados
ADD CONSTRAINT FK_id_sucursal_empledos
FOREIGN KEY (id_sucursal) REFERENCES Sucursal(id_sucursal);

-- tabla de transacciones --
CREATE TABLE Transacciones(
id_transaccion INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
cuenta_origen INT NOT NULL,
cuenta_destino INT NOT NULL,
tipo_transaccion VARCHAR(20) NOT NULL,
monto INT NOT NULL,
fecha_hora DATE NOT NULL,
medio VARCHAR(20) NOT NULL);

ALTER TABLE transacciones
ADD CONSTRAINT FK_id_cuenta_transaccion
FOREIGN KEY (cuenta_origen) REFERENCES Cuenta(numero_cuenta);
