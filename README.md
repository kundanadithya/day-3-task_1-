# FastAPI Example
 
This repository contains a simple FastAPI application with two endpoints:
 
*   `/`: Returns a greeting message.

*   `/items/{item_id}`: Returns an item ID and an optional query parameter.
 
## Getting Started
 
### Prerequisites
 
*   Python 3.7+

*   pip (or similar package manager)
 
### Installation
 
1.  Clone the repository (optional, if you're not starting from scratch):
 
    ```bash

    git clone [https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git](https://www.google.com/search?q=https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git)  # Replace with your repo URL

    cd YOUR_REPOSITORY_NAME

    ```
 
2.  Create a virtual environment (recommended):
 
    ```bash

    python3 -m venv venv  # Create the environment

    source venv/bin/activate  # Activate on Linux/macOS

    venv\Scripts\activate  # Activate on Windows

    ```
 
3.  Install the required packages:
 
    ```bash

    pip install fastapi uvicorn

    ```
 
### Running the Application
 
1.  Navigate to the directory containing the `main.py` file.
 
2.  Run the application using Uvicorn:
 
    ```bash

    python main.py

    ```
 
    This will start the server at `http://127.0.0.1:8000`.
 
### Endpoints
 
*   **GET `/`:**
 
    Returns:
 
    ```json

    {"message": "Hello, FastAPI!"}

    ```
 
*   **GET `/items/{item_id}`:**
 
    *   `item_id`:  An integer representing the item ID.

    *   `q` (optional): A string query parameter.
 
    Returns:
 
    ```json

    {"item_id": 123, "query": "somequery"}  # Example with query parameter

    ```
 
    ```json

    {"item_id": 456, "query": null}  # Example without query parameter

    ```
 
### Testing the Endpoints
 
You can test the endpoints using a web browser, `curl`, or a tool like Postman.
 
*   **Browser:** Open your browser and go to `http://127.0.0.1:8000` or `http://127.0.0.1:8000/items/123?q=test`.
 
*   **curl:**
 
    ```bash

    curl [http://127.0.0.1:8000](http://127.0.0.1:8000)

    curl [http://127.0.0.1:8000/items/123?q=test](http://127.0.0.1:8000/items/123?q=test)

    ```
 
*   **Postman:** Create GET requests to the specified URLs.
 
### API Documentation (Swagger/Redoc)
 
FastAPI automatically generates interactive API documentation.  Once the application is running, you can access it at:
 
*   Swagger UI: `http://127.0.0.1:8000/docs`

*   Redoc: `http://127.0.0.1:8000/redoc`
 
## Example Code (`main.py`)
 
```python

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
 
