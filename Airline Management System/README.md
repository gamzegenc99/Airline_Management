
# **Airline Management System**

## **Project Description**

This project is an **Airline Management System** API built using Django and Django REST Framework (DRF). The API allows users to view airplanes, flights, and make reservations. It includes validation for flight data and reservation information, including checking capacity availability and ensuring valid email addresses for passengers.

## **Features**

- **Airplane Management**: Add, update, and delete airplane records, along with querying specific details and flights assigned to an airplane.
- **Flight Management**: Create, update, delete, and view flight information, including reservations linked to a flight.
- **Reservation Management**: Add, modify, cancel, and view reservations with unique reservation codes.
- **Occupancy Check**: Check if the flight capacity is full before confirming a reservation.
- **Reservation Code Generation**: Automatically generate unique alphanumeric reservation codes upon reservation creation.
- **Model validation** for the flight schedule (departure time before arrival time),different departure and destination locations and valid email addresses for reservations.

## **Setup Instructions**

### **1. Prerequisites**

- Python 3.13.1
- Django 5.1.5
- Django Rest Framework (DRF)
- SQLite (Default Database)

### **2. Clone the Repository**

Clone the project repository to your local machine.

```bash
git clone <https://github.com/gamzegenc99/airline_management_system.git>
cd <project_directory>
```

### **3. Install Dependencies**

Install the required dependencies using **`pip`**.

```bash
pip install -r requirements.txt
```

**Note: If `requirements.txt` doesn't exist, you can install the dependencies individually:**

```bash
pip install django
pip install djangorestframework
```

### **4. Set Up the Database**

Once the dependencies are installed, create and apply migrations to set up the database.

```bash
python [manage.py](http://manage.py/) makemigrations
python [manage.py](http://manage.py/) migrate
```

### **5. Create a Superuser**

Create a superuser to access the Django admin panel.

```bash
python manage.py createsuperuser

```

> Follow the prompts to create the superuser with your desired credentials.
> 

### **6. Run the Development Server**

Start the Django development server.

```bash
python manage.py runserver
```

> **The application will now be accessible at `http://127.0.0.1:8000/`**
> 

## **API Endpoints**

### **Base URL:**

**`http://127.0.0.1:8000/`**

---

### **Airplane API**

- **GET /airplanes/**: List all airplanes.
- **GET /airplanes/{id}/**: Get details of a specific airplane.
- **GET /airplanes/{id}/flights**: Get the flights assigned to a specific airplane.
- **POST /airplanes/**: Add a new airplane.
- **PATCH /airplanes/{id}/**: Update a specific airplane.
- **DELETE /airplanes/{id}/**: Delete a specific airplane.

### **Flight API**

- **GET /flights/**: List all flights.
- **GET /flights/{id}/**: Get details of a specific flight.
- **GET /flights/{id}/reservations**: Get reservations made for a specific flight.
- **POST /flights/**: Add a new flight.
- **PATCH /flights/{id}/**: Update a specific flight.
- **DELETE /flights/{id}/**: Delete a specific flight.

### **Reservation API**

- **GET /reservations/**: List all reservations.
- **GET /reservations/{id}/**: Get details of a specific reservation.
- **POST /reservations/**: Add a new reservation.
- **PATCH /reservations/{id}/**: Update a specific reservation.

## **Testing**

### **Running Tests**

This project includes test case to validate reservations.

To run the tests:

```bash
python [manage.py](http://manage.py/) test
```

### **Test Cases:**

- **ReservationTest**: Ensures that reservations cannot exceed the airplane's capacity.

## **Basic Validation**

- **Flight Validation**:
    - **`departure_time`**must be before **`arrival_time`**.
    - Departure and destination must not be the same.
- **Reservation Validation**:
    - The passenger's email address must be valid (contains "@" and ".").
    - Reservation creation fails if the number of passengers exceeds the airplane's capacity.

## **Admin Panel**

Once the server is running, access the Django Admin panel at **`http://127.0.0.1:8000/admin`**.

Use the superuser credentials created earlier to log in and manage airplanes, flights, and reservations.

## **Project Structure**

```bash
airline_management_system/
│
├── airline_management_system/
│   ├── [settings.py](http://settings.py/)        # Proje ayarları ve yapılandırmalar
│   ├── [urls.py](http://urls.py/)            # Ana URL yapılandırması
│   └── [wsgi.py](http://wsgi.py/)            # Üretim için WSGI yapılandırması
│
├── core/
│   ├── migrations/        # Veritabanı migration dosyaları
│   ├── [models.py](http://models.py/)          # Model tanımları (Airplane, Flight, Reservation)
│   ├── [serializers.py](http://serializers.py/)     # Serializer sınıfları
│   ├── [views.py](http://views.py/)           # API endpoint'leri için ViewSet'ler
│   └── [urls.py](http://urls.py/)            # API yönlendirmeleri için URL'ler
│
├── [manage.py](http://manage.py/)              # Django yönetim scripti
└── db.sqlite3
└── README.md              # Proje açıklaması ve kullanım talimatları
├── postman/
   └── airline_management_system_collection.json  # Postman koleksiyonu dosyası
```
## **API Testability**

The API endpoints can be tested using Postman. A Postman Collection file will be provided with the project to easily test all API functionality.

### Postman Collection

You can import the Postman collection for this project using the following steps:

1. Open [Postman](https://www.postman.com/) application.
2. Click on the "Import" button in the top left corner.
3. Choose the "File" tab, then click on "Choose Files" and select the `airline_management_system_collection.json` file located in the `postman/` directory of the project.
4. The collection will be imported into Postman, and you can start testing the API endpoints.
