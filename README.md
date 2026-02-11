# DataExtractionAPI

Building A Data Engineering Project
      Extracting data from an API

Tech Stack:

Apache Airflow – orchestration & scheduling

PostgreSQL – database / “warehouse”

MinIO – S3-like object storage (local)

Docker Compose – glue everything together

# First, Understand the basic API foundation

1️⃣ REST API Basics

REST = Representational State Transfer

It’s just a standard way systems communicate over the internet.

Think like this:

You → send request
Server → send response

Example:

GET https://api.weather.com/current


Server replies with JSON:

{
  "city": "Kuala Lumpur",
  "temperature": 32
}


So REST API = URL + HTTP method + JSON response.

Most modern APIs (Spotify, OpenAI, Twitter, etc.) use REST.
--------------------------------------------------------------

2️⃣ JSON Structure

JSON = JavaScript Object Notation
It’s how data is returned from APIs.

Looks like Python dictionary:

{
  "name": "Amir",
  "age": 21,
  "skills": ["Python", "SQL", "Spark"]
}


In Python:

data = response.json()
print(data["name"])


Important JSON concepts:

{} → object (dictionary)

[] → list

key-value pair

Understanding JSON is VERY important in data engineering.

---
3️⃣ HTTP Methods

These tell the server what you want to do.

🔹 GET

Used to retrieve data
Most common.

requests.get(url)

🔹 POST

Used to send data to server

Example:
Login, create account, insert data

requests.post(url, json=data)

🔹 PUT

Update existing data

🔹 DELETE

Delete data

For beginners, focus on GET first.

4️⃣ Status Codes

When you send request, server replies with a code.

Common ones:

Code	Meaning
200	Success
201	Created
400	Bad request
401	Unauthorized
404	Not found
500	Server error

Example:

response = requests.get(url)
print(response.status_code)


If 200 → good
If 404 → wrong URL
If 401 → missing API key

How Everything Connects

You:

Send HTTP request (GET)

Server returns Status Code

If 200 → read JSON

Extract fields from JSON

That’s it.

If you master this, you can:

Pull crypto prices

Pull weather data

Pull stock data

Pull football stats

Build dashboards

Build pipelines
