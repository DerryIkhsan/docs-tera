# 📘 Catatan Teknis Open API Cloud (V2 & V3)

---

## 📋 Daftar Isi
1. [Open API Cloud](#-open-api-cloud)
2. [Arsitektur Open API Cloud](#-arsitektur-open-api-cloud)
3. [Collection Open API Cloud](#-collection-open-api-cloud)
4. [Path Project Open API Cloud](#-path-project-open-api-cloud)

---

## 🌐 Open API Cloud
Open API Cloud merupakan jembatan (API Gateway) yang disediakan teramedik untuk memenuhi kebutuhan klien teramedik dalam pengembangan aplikasi pihak ketiga rumah sakit, seperti untuk pengembangan aplikasi web maupun mobile apps yang dikembangkan mandiri oleh vendor dari masing-masing rumah sakit.

---


## 🏢 Arsitektur Open API Cloud

**1. Arsitektur Open API Cloud V2**

Pada gambar dibawah dapat dijelaskan bahwa arsitektur open api cloud v2 berfungsi sebagai jembatan (API Gateway) yang memungkinkan aplikasi pihak ketiga berinteraksi dengan sistem rumah sakit (Teramedik HIS) tanpa mengakses database utama HIS secara langsung. Data dari HIS disinkronkan oleh Backend Sync ke Cloud Database agar bisa diakses oleh API Cloud. Sementara untuk transaksi antara API Cloud dan HIS dijembatani oleh Webservice internal HIS untuk memastikan data tetap sinkron dan valid di kedua sisi.

<img width="1920" height="1080" alt="Open API Cloud V2 (2)" src="https://github.com/user-attachments/assets/dc87a3a9-64ab-4ff2-a43a-e1105c6e6bd0" />


**2. Arsitektur Open API Cloud V3**

Arsitektur open api cloud v3 hampir mirip dengan open api cloud v2 yang hanya berbeda dari cara transaksi antara API Cloud dengan HIS, dimana pada open api cloud v3 transaksi antara API Cloud dan sistem rumah sakit (Teramedik HIS) sinkron langsung tanpa melalui Webservice internal HIS.

<img width="1920" height="1080" alt="Open API Cloud V3 (1)" src="https://github.com/user-attachments/assets/80cef3b6-c9e5-4486-9545-e5ae608fadba" />

 

---

## 📖 Collection Open API Cloud

Collection open api cloud v2 dan open api cloud v3 dapat di download pada link berikut :

1. [**Collection Open API Cloud V2**](./collection/Open_API_V2.postman_collection.json)
2. [**Collection Open API Cloud V3**](./collection/Open_API_V3.postman_collection.json)

---

## 🌐 Path Project Open API Cloud

**Open API Cloud V2 (Server ALI CLOUD)**
Production :
- path backendsync : /var/www/production/api-v2.1
- path open api : /var/www/cloud-webservice/production

Devel/Staging :
- path backendsync : /var/www/devel/group/api
- path open api : /var/www/cloud-webservice/devel

**Open API Cloud V3 (Server GCP Mobile Production)**
Production :
- path backendsync : /var/www/production/backendsync
- path open api : /var/www/production/cloud-webservice

Devel/Staging :
- path backendsync : /var/www/staging/backendsync
- path open api : /var/www/staging/cloud-webservice

