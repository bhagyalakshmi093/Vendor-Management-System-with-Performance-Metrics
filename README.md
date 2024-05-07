Features
Vendor Profile Management:

Create, retrieve, update, and delete vendor profiles.
Calculate and display vendor performance metrics.
Purchase Order Tracking:

Create, retrieve, update, and delete purchase orders.
Track delivery status, items, quantity, and other details.
Vendor Performance Evaluation:

Calculate performance metrics, including on-time delivery rate, quality rating average, average response time, and fulfillment rate.
Historical performance tracking for trend analysis.
Technical Requirements
Django (latest stable version)
Django REST Framework (latest stable version)
Token-based authentication
PEP 8 compliant code
Comprehensive data validations
Django ORM for database interactions
Installation
Create and activate a virtual environment:
python -m venv venv
.\venv\Scripts\activate

Install dependencies:
 pip install -r requirements.txt
Run migrations:
python manage.py makemigrations
python manage.py migrate
Run :
python manage.py runserver
API
```bash 
http://127.0.0.1:8000/admin/
http://127.0.0.1:8000/vendors/api 
http://127.0.0.1:8000/api/vendors/<int:pk>/ 
http://127.0.0.1:8000/purchase_orders/api
http://127.0.0.1:8000/api/purchase_orders/<int:pk>/ 
http://127.0.0.1:8000/historical_performance/api 
http://127.0.0.1:8000/api/vendors/<int:vendor_id>/performance/ 
http://127.0.0.1:8000/api/purchase_orders/<int:pk>/acknowledge/ 
API Documentation
Detailed API documentation is available in the API Documentation file. Please refer to this documentation for detailed information about each API endpoint, including input parameters, authentication requirements, and response formats.

Sample JSON for Creating a New Vendor
{
"name": " Vendor1",
"contact_details": "123-456-7890",
"address": "india",
"vendor_code": "SAMPLE123",
"on_time_delivery_rate": 95.0,
"quality_rating_avg": 4.5,
"average_response_time": 2.5,
"fulfillment_rate": 98.0
}

Sample JSON for Acknowledging a Purchase Order Create a file named acknowledge_purchase_order.json with the following content:

json  

{
"acknowledgment_date": "2024-07-05T10:00:00"
}
Vendor Endpoints
Create a new vendor:

URL: POST /api/vendors/ Payload Example:

    json
    {
        "name": "Vendor Name",
        "contact_details": "Contact Information",
        "address": "Vendor Address",
        "vendor_code": "ABC123"
    }
*Authentication: Token-based authentication required.

List all vendors:

URL: GET /api/vendors/
Authentication: Token-based authentication required.
Retrieve a specific vendor's details:

URL: GET /api/vendors/{vendor_id}/
Authentication: Token-based authentication required.
Update a vendor's details:

URL: PUT /api/vendors/{vendor_id}/
Payload Example:

json
 
{
"name": "Updated Vendor Name",
"contact_details": "Updated Contact Information",
"address": "Updated Vendor Address",
"vendor_code": "ABC123"
}
*Authentication: Token-based authentication required.

Delete a vendor:

URL: DELETE /api/vendors/{vendor_id}/
Authentication: Token-based authentication required.
Retrieve a vendor's performance metrics:

URL: GET /api/vendors/{vendor_id}/performance/
Authentication: Token-based authentication required.
Purchase Order Endpoints

Create a new purchase order:

URL: POST /api/purchase_orders/

Payload Example:
json

{
"po_number": "PO123",
"vendor": 1,
"order_date": "2024-05-07T10:00:00",
"delivery_date": "2024-05-20T10:00:00",
"items": [{"name": "Item1", "quantity": 20}],
"quantity": 20,
"status": "pending"
}
*Authentication: Token-based authentication required.

List all purchase orders:

URL: GET /api/purchase_orders/
Authentication: Token-based authentication required.
Retrieve details of a specific purchase order:

URL: GET /api/purchase_orders/{po_id}/
Authentication: Token-based authentication required.
Update a purchase order:

URL: PUT /api/purchase_orders/{po_id}/
Payload Example:

json
{
"status": "completed",
"acknowledgment_date": "2024-05-07T10:00:00"
}
*Authentication: Token-based authentication required.

Delete a purchase order:

URL: DELETE /api/purchase_orders/{po_id}/
*Authentication: Token-based authentication required.

Acknowledge Purchase Order Endpoint
Acknowledge a purchase order:
URL: PATCH /api/purchase_orders/{po_id}/acknowledge/
Payload Example:

json
{
"acknowledgment_date": "2024-05-07T10:00:00"
}
*Authentication: Token-based authentication required. Please note that you should replace {vendor_id} and {po_id} in the URLs with the actual vendor and purchase order IDs you want to interact with.

Ensure you have the appropriate authentication token and include it in the request headers
