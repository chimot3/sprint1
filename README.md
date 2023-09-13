<p align="center"><a href="https://www.dot.co.id/" target="_blank"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEikw-f56L6-Ce0DtBECOLgxtdqhky0s-j9GFr71yow-8f-Q_rZDy1K26ibwcwo4OoZ2b58NZcODu1a469z8JQH_iyDNtWKoKRLe9RPw7D-h2R9YOCwfzkoUA_ungtwnqaWuWfmXKJ9haUTcueFakqH_AgE96va6MQg1VU9SIfTKhZf8JJLG3vasDyUJ/w680/icon-dot.png" width="200" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## DOT Sprint 1

- Integrasi dengan API province & city Rajaongkir (paket starter) [https://rajaongkir.com/dokumentasi/starter](https://rajaongkir.com/dokumentasi/starter).
- Membuat artisan command​ yg melakukan fetching API data provinsi & kota dan data disimpan ke dalam database.
- Membuat REST API untuk pencarian provinsi & kota dengan endpoint berikut:
-     [GET] /search/provinces?id={province_id}.
-     [GET] /search/cities?id={city_id}
- Live demo : [https://poppyfebria.ddns.net:9001](https://poppyfebria.ddns.net:9001)


## Installation

Clone the repo locally:

```sh
git clone https://github.com/chimot3/sprint1.git dot-sprint-1 && cd dot-sprint-1
```

Install PHP dependencies:

```sh
composer install
```

Setup configuration:

```sh
cp .env.example .env
```

Generate application key:

```sh
php artisan key:generate
```

Create an SQLite database. You can also use another database (MySQL, Postgres), simply update your configuration accordingly.

```sh
touch database/database.sqlite
```

Run database migrations:

```sh
php artisan migrate
```

Fetch province and city data from Rajaongkir:

```sh
php artisan province-city:fetch
```

Run the dev server (the output will give the address, ex: https://127.0.0.1:8000):

```sh
php artisan serve
```


## Get data Province

### Request
<section id="province-request">
                <div class="tab-content">
                    <div class="tab-pane fade active in" id="province-request-url">
                        <table class="table table-bordered table-striped">
                            <thead>
                                <tr>
                                    <td>Method</td>
                                    <td>URL</td>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>GET</td>
                                    <td>https://127.0.0.1:8000/search/provinces</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="tab-pane fade" id="province-request-parameter">
                        <table class="table table-bordered table-striped">
                            <thead>
                                <tr>
                                    <td>Method</td>
                                    <td>Parameter</td>
                                    <td>Required</td>
                                    <td>Type</td>
                                    <td>Description</td>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>GET</td>
                                    <td>id</td>
                                    <td>Yes</td>
                                    <td>String</td>
                                    <td>Provincy ID</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
            </section>

### Response

#### Success Response
```sh
{
    "success": true,
    "result": [
        {
            "id": 1,
            "province": "Bali",
            "created_at": "2023-09-08T09:02:51.000000Z",
            "updated_at": "2023-09-08T09:02:51.000000Z"
        }
    ]
}
```

#### Response detail
<table class="table table-bordered table-striped">
                            <thead>
                                <tr>
                                    <td>Component</td>
                                    <td>Type</td>
                                    <td>Description</td>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>id</td>
                                    <td>Integer</td>
                                    <td>Provincy ID</td>
                                </tr>
                                <tr>
                                    <td>province</td>
                                    <td>String</td>
                                    <td>Provincy Name</td>
                                </tr>
                                <tr>
                                    <td>created_at</td>
                                    <td>Timestamp</td>
                                    <td>Time Created</td>
                                </tr>
                                <tr>
                                    <td>updated_at</td>
                                    <td>Timestamp</td>
                                    <td>Time Updated</td>
                                </tr>
                            </tbody>
                        </table>


#### Fail Response
```sh
{
    "success": false,
    "message": "ID not provided"
}
```


## Get data City

### Request
<section id="province-request">
                <div class="tab-content">
                    <div class="tab-pane fade active in" id="province-request-url">
                        <table class="table table-bordered table-striped">
                            <thead>
                                <tr>
                                    <td>Method</td>
                                    <td>URL</td>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>GET</td>
                                    <td>https://127.0.0.1:8000/search/cities</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="tab-pane fade" id="province-request-parameter">
                        <table class="table table-bordered table-striped">
                            <thead>
                                <tr>
                                    <td>Method</td>
                                    <td>Parameter</td>
                                    <td>Required</td>
                                    <td>Type</td>
                                    <td>Description</td>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>GET</td>
                                    <td>id</td>
                                    <td>Yes</td>
                                    <td>String</td>
                                    <td>City ID</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
            </section>

### Response

#### Success Response
```sh
{
    "success": true,
    "result": [
        {
            "id": 1,
            "province_id": 21,
            "type": "Kabupaten",
            "city_name": "Aceh Barat",
            "postal_code": "23681",
            "created_at": "2023-09-07T15:50:34.000000Z",
            "updated_at": "2023-09-07T15:50:34.000000Z"
        }
    ]
}
```

#### Response detail
<table class="table table-bordered table-striped">
                            <thead>
                                <tr>
                                    <td>Component</td>
                                    <td>Type</td>
                                    <td>Description</td>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>id</td>
                                    <td>Integer</td>
                                    <td>City ID</td>
                                </tr>
                                <tr>
                                    <td>province_id</td>
                                    <td>Integer</td>
                                    <td>Provincy ID</td>
                                </tr>
                                <tr>
                                    <td>type</td>
                                    <td>String</td>
                                    <td>City type</td>
                                </tr>
                                <tr>
                                    <td>city_name</td>
                                    <td>String</td>
                                    <td>City Name</td>
                                </tr>
                                <tr>
                                    <td>postal_code</td>
                                    <td>String</td>
                                    <td>City Postalcode</td>
                                </tr>
                                <tr>
                                    <td>created_at</td>
                                    <td>Timestamp</td>
                                    <td>Time Created</td>
                                </tr>
                                <tr>
                                    <td>updated_at</td>
                                    <td>Timestamp</td>
                                    <td>Time Updated</td>
                                </tr>
                            </tbody>
                        </table>


#### Fail Response
```sh
{
    "success": false,
    "message": "ID not provided"
}
```

