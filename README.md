````md id="tp11localisation"
# TP 11 — Localisation Smartphone et Envoi vers Serveur PHP

![Android](https://img.shields.io/badge/Platform-Android-green)
![Java](https://img.shields.io/badge/Language-Java-orange)
![PHP](https://img.shields.io/badge/Backend-PHP-blue)
![MySQL](https://img.shields.io/badge/Database-MySQL-red)

## 📌 Description

Ce TP montre comment :

- récupérer la position GPS d’un smartphone Android ;
- envoyer latitude et longitude vers un serveur PHP ;
- enregistrer les coordonnées dans MySQL.

---

# 🎯 Objectifs

- utiliser la géolocalisation Android ;
- gérer les permissions ;
- communiquer avec un backend PHP ;
- stocker des données dans MySQL.

---

# 🛠 Technologies Utilisées

- Android Studio
- Java
- PHP
- MySQL
- GPS Android

---

# 🗄 Partie Serveur — Base MySQL

Créer la base :

```sql id="a4v8mk"
CREATE DATABASE localisation_db;
````
<img width="991" height="631" alt="image" src="https://github.com/user-attachments/assets/88e9a9e5-8a0d-4c77-9d4e-02cab83c471c" />


Créer la table :

```sql id="x7q2lp"
CREATE TABLE positions (

    id INT AUTO_INCREMENT PRIMARY KEY,
    latitude VARCHAR(50),
    longitude VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
<img width="1581" height="784" alt="image" src="https://github.com/user-attachments/assets/172d8575-ecc7-4c58-8f41-70dbd6938750" />


---

# 🌐 Partie Serveur — PHP

Créer `save_location.php`

```php id="n9t3ws"
<?php

$conn = mysqli_connect("localhost","root","","localisation_db");

$lat = $_POST['latitude'];
$lon = $_POST['longitude'];

$sql = "INSERT INTO positions(latitude, longitude)
VALUES('$lat','$lon')";

mysqli_query($conn,$sql);

echo "Success";

?>
```

---

# 📱 Partie Mobile — Permissions

Dans `AndroidManifest.xml`

```xml id="k2m6rd"
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
<uses-permission android:name="android.permission.INTERNET"/>
```

---

# 📍 Récupération GPS

Exemple Java :

```java id="j5x1vn"
LocationManager locationManager;

locationManager = (LocationManager)
getSystemService(LOCATION_SERVICE);
```
<img width="137" height="293" alt="image" src="https://github.com/user-attachments/assets/785e5ca7-8538-4cb5-a169-84eed695e417" />

---

# 🚀 Envoi des Coordonnées

Exemple :

```java id="u8p4yt"
String url = "http://YOUR_SERVER/save_location.php";
```

Envoyer :

* latitude
* longitude

vers le serveur PHP.

---
<img width="143" height="315" alt="image" src="https://github.com/user-attachments/assets/5fac6432-be47-455f-bb47-4fbd07226170" />

# 🔥 Résultat Attendu

* récupération GPS réussie
* données envoyées au serveur
* coordonnées enregistrées dans MySQL

---

# 📚 Architecture

```text id="f1z7qa"
Android App
   ↓
PHP API
   ↓
MySQL Database
```

---

# ⚠️ Bonnes Pratiques

* demander permissions runtime
* utiliser HTTPS
* valider les données serveur
* éviter les coordonnées en clair

---

# ✅ Concepts Appris

* Android GPS
* Permissions Android
* HTTP Request
* PHP Backend
* Base de données MySQL

---

# 👨‍💻 Auteur

Ayoub Laafar — EMSI Marrakech

```
```
