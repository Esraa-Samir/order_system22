# order_system

# About this project

A simple ordering system based of Django Rest Framework.

# Technologies

Django
Django Rest Framework
python3.7

# To run the app locally

 - Create a new virtualenv -> virtualenv venv
 - Activate virtual env -> /venv/Scripts/activate
 - Install required libraries -> pip install -r requirements.txt
 - Run project -> python manage.py runserver
 
 # Consuming APIs
  
 To test APIs you can use curl commands or applications ike postman.
 
 To conume any of the following API you need to be authenticated.
 
 <pre> 
 To create a user -> 
     curl -X POST \
     http://127.0.0.1:8000/products/ \
     -H 'Content-Type: application/json' \
     -H 'cache-control: no-cache' \
     -d '{
     "username": "user",
     "email": "user@test.com",
     "password": 123456,
     "is_admin": True // False by default 
     }' 
</pre>
                    
 Login -> curl -X POST \
               -H 'Content-Type: application/json' \
               http://127.0.0.1:8000/auth/token/login/ \
               -d '{"username":"user@test.com","password":"123456"}'


 Login API returns a token that you can to consume the following APIs
 
 
 Create_product -> curl -X POST \
                      http://127.0.0.1:8000/products/ \
                      -H 'Content-Type: application/json' \
                      -H 'cache-control: no-cache' \
                      -H "Authorization: Token {token}" \
                      -d '{
                      "name": "Iphone",
                      "description": "mobile phone",
                      "price": 1000,
                      "price_currency": "USD", // set by dafault to EGP but can be changed 
                      "is_available": True
                    }'
                    
  Modify_product -> curl -X PATCH \
                      http://127.0.0.1:8000/products/update/<product_id> \
                      -H 'Content-Type: application/json' \
                      -H 'cache-control: no-cache' \
                      -H "Authorization: Token {token}" \
                      -d '{
                      "name": "Iphone",
                      "description": "mobile phone",
                      "price": 2000,
                      "is_available": False
                    }' 
                    
  Delete_product -> curl -X DELETE \
                      http://127.0.0.1:8000/products/delete/<product_id> \
                      -H 'Content-Type: application/json' \
                      -H 'cache-control: no-cache' \
                      -H "Authorization: Token {token}" \
                      
   Get_products -> curl -X GET \
                      http://127.0.0.1:8000/products/ \
                      -H 'Content-Type: application/json' \
                      -H 'cache-control: no-cache' \
                      -H "Authorization: Token {token}" \
                      
   Get_total_revenu -> curl -X GET \
                      http://127.0.0.1:8000/purchases/profit \
                      -H 'Content-Type: application/json' \
                      -H 'cache-control: no-cache' \
                      -H "Authorization: Token {token}" \
                      
   Get_purchased_products -> curl -X GET \
                      http://127.0.0.1:8000/purchases/history \
                      -H 'Content-Type: application/json' \
                      -H 'cache-control: no-cache' \
                      -H "Authorization: Token {token}" \
                      
   Purchase_product -> curl -X POST \
                      http://127.0.0.1:8000/purchases/profit \
                      -H 'Content-Type: application/json' \
                      -H 'cache-control: no-cache' \
                      -H "Authorization: Token {token}" \
                      -d '{"item": "5"}' // id of purchased product
                      
   Get_all_products ->  curl -X GET \
                      http://127.0.0.1:8000/products/available \
                      -H 'Content-Type: application/json' \
                      -H 'cache-control: no-cache' \
                      -H "Authorization: Token {token}" 
 
 # Run unit tests
  
  - Run -> python manage.py test
 
