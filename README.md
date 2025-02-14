FastAPI Application Setup Guide
Follow these steps to set up and run a simple FastAPI application.

Step 1: Install Dependencies
First, ensure you have FastAPI and Uvicorn installed. Run the following command to install them using pip:

bash
Copy
pip install fastapi uvicorn
Step 2: Create the Python Script
Create a new Python file, e.g., main.py.

Add the following code to the file:

python
Copy
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, FastAPI!"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "query": q}

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="127.0.0.1", port=8000)
Explanation:
Root Endpoint (/): Returns a message "Hello, FastAPI!" when accessed.
Items Endpoint (/items/{item_id}): Accepts an item_id in the URL and an optional query string q. It returns both values as JSON.
Step 3: Run the Application
To run the FastAPI application, use the following command in your terminal:

bash
Copy
python main.py
This will start the FastAPI server, and you'll see output like this:

pgsql
Copy
INFO:     Started server process [12345]
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
Step 4: Access the API
Open your browser or a tool like Postman.
Navigate to the following URLs:
Root Endpoint: http://127.0.0.1:8000/
You should see a JSON response:
json
Copy
{ "message": "Hello, FastAPI!" }
Items Endpoint: http://127.0.0.1:8000/items/{item_id}?q={query}
Replace {item_id} with any integer and {query} with any optional string. Example:
json
Copy
{ "item_id": 5, "query": "test" }
Step 5: Access API Documentation
FastAPI automatically generates interactive API documentation. You can view it at:

Swagger UI: http://127.0.0.1:8000/docs
ReDoc UI: http://127.0.0.1:8000/redoc
