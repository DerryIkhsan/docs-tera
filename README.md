# 📘 Catatan Teknis Open API Cloud (V2 & V3)

---

## 📋 Daftar Isi
1. [Open API Cloud](#open-api-cloud)
2. [Arsitektur Open API Cloud](#arsitektur-cloud)
3. [Collection Open API Cloud](#collection-api)
4. [Path Project Open API Cloud](#path-project)

---

## <a name="open-api-cloud"></a>🌐 Open API Cloud
Open API Cloud merupakan jembatan (**API Gateway**) yang disediakan Teramedik untuk memenuhi kebutuhan klien dalam pengembangan aplikasi pihak ketiga rumah sakit. Ini mencakup pengembangan aplikasi web maupun mobile yang dikembangkan secara mandiri oleh vendor dari masing-masing rumah sakit.

---

## <a name="arsitektur-cloud"></a>🏢 Arsitektur Open API Cloud

### 1. Arsitektur Open API Cloud V2
Arsitektur ini berfungsi sebagai jembatan yang memungkinkan aplikasi pihak ketiga berinteraksi dengan **Teramedik HIS** tanpa mengakses database utama secara langsung.

* **Data Sync**: Data dari HIS disinkronkan oleh *Backend Sync* ke *Cloud Database*.
* **Transaksi**: Interaksi antara API Cloud dan HIS dijembatani oleh **Webservice internal HIS** untuk memastikan validitas data di kedua sisi.

#### 📥 Alur Request Client Apps (Hit API)
Ketika Client Apps melakukan permintaan ke API Cloud, proses berikut terjadi:
1. **Authentication**: API Cloud memvalidasi *API Key/Token* dari client.
2. **Request Routing**: Sistem menentukan apakah mengambil data dari *Cloud Database* (untuk data hasil sinkronisasi) atau meneruskan ke *Webservice HIS* (untuk transaksi real-time).
3. **Data Processing**: 
   - **Read**: Mengambil data cepat dari *Cloud Database*.
   - **Write**: Mengirim data ke *Webservice HIS* untuk validasi sistem inti.
4. **Response**: API Cloud mengembalikan data dalam format JSON ke client.

<img width="1920" height="1080" alt="Open API Cloud V2" src="https://github.com/user-attachments/assets/dc87a3a9-64ab-4ff2-a43a-e1105c6e6bd0" />

---

### 2. Arsitektur Open API Cloud V3
Secara fungsionalitas mirip dengan V2, namun memiliki perbedaan pada mekanisme transaksi. Pada **V3**, transaksi antara API Cloud dan sistem rumah sakit (**Teramedik HIS**) dilakukan secara **sinkron langsung** tanpa melalui *Webservice* internal HIS sebagai perantara tambahan.

<img width="1920" height="1080" alt="Open API Cloud V3" src="https://github.com/user-attachments/assets/80cef3b6-c9e5-4486-9545-e5ae608fadba" />

---

## <a name="collection-api"></a>📖 Collection Open API Cloud
Dokumen koleksi API dapat diunduh pada tautan berikut:

1. [**Collection Open API Cloud V2**](./collection/Open_API_V2.postman_collection.json)
2. [**Collection Open API Cloud V3**](./collection/Open_API_V3.postman_collection.json)

---

## <a name="path-project"></a>🌐 Path Project Open API Cloud

### 1. Open API Cloud V2 (Server ALI CLOUD)
* **Production**
  * Path Backend Sync: `/var/www/production/api-v2.1`
  * Path Open API: `/var/www/cloud-webservice/production`
* **Devel/Staging**
  * Path Backend Sync: `/var/www/devel/group/api`
  * Path Open API: `/var/www/cloud-webservice/devel`

### 2. Open API Cloud V3 (Server GCP Mobile Production)
* **Production**
  * Path Backend Sync: `/var/www/production/backendsync`
  * Path Open API: `/var/www/production/cloud-webservice`
* **Devel/Staging**
  * Path Backend Sync: `/var/www/staging/backendsync`
  * Path Open API: `/var/www/staging/cloud-webservice`
