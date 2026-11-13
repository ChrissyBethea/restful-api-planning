# Module 4: Assignment 3 – Planning a RESTful API with Fetch GET

## 1. API Selection

For this project, I plan to create a weather information application using the **Open-Meteo Weather API**, which provides weather forecasts and current weather conditions. I selected this API because weather information is useful, easy to understand, and suitable for displaying in a dynamic table.

The application will follow REST principles by identifying weather data through resource URLs, using standard HTTP methods, and making stateless requests. Each request will contain the information needed for the API to respond without relying on previous requests.

## 2. Endpoint Mapping

The application will use the following endpoints:

- **GET `/v1/forecast`** – Retrieves weather information from Open-Meteo using latitude, longitude, and requested weather variables. Example: `https://api.open-meteo.com/v1/forecast?latitude=34.00&longitude=-81.03&current=temperature_2m,relative_humidity_2m,weather_code`
- **GET `/api/weather`** – A proposed Python backend endpoint that could retrieve weather information and return JSON to the client.
- **POST `/api/submit`** – A proposed Python backend endpoint that would accept a user's weather search preferences as JSON.

The GET requests retrieve resources without modifying them, while POST submits new information for processing. Each request will be independent, supporting REST's stateless design.

## 3. Data Flow Diagram (Textual)

The planned application will follow this process:

User opens webpage → JavaScript sends asynchronous Fetch GET request → Open-Meteo returns JSON → JavaScript processes response → Weather information appears in a table.

The application will use JavaScript's `fetch()` function with the GET method and an `Accept: application/json` header. A loading message will appear while the request is processing. The application will check the HTTP response status and display an error message if the request fails or the server returns an unsuccessful response.

Once the data is received, JavaScript will extract temperature, humidity, and weather conditions from the JSON response and dynamically create table rows.

Conditional CSS styling will highlight temperatures of 90°F or higher in red and temperatures below 50°F in blue. Other temperatures will use the default styling. The application will request Fahrenheit temperatures so the styling thresholds match the displayed values.

## 4. Form Handling

The application will include a form allowing users to enter weather search preferences.

**Planned input fields:**

- **City Name:** Required text field; cannot be empty.
- **Latitude:** Required numeric field between -90 and 90.
- **Longitude:** Required numeric field between -180 and 180.
- **Temperature Unit:** Dropdown allowing Fahrenheit or Celsius.

JavaScript will validate the form before submission. Empty fields, invalid coordinates, and unsupported temperature units will display error messages.

After validation, JavaScript will convert the information into a JSON object containing `city_name`, `latitude`, `longitude`, and `temperature_unit`.

The JSON payload will be submitted to the proposed Flask backend using POST `/api/submit` with the `Content-Type: application/json` header. The backend contract will require these fields and return a JSON confirmation or validation error. This endpoint is part of the design and does not need to be implemented for this assignment.

The city name will be used as a display label, while latitude and longitude will identify the location for the weather request.

## 5. Technology Stack

The planned application will use:

- **HTML:** Structure of the webpage and weather table.
- **CSS:** Page formatting and conditional weather highlighting.
- **JavaScript:** Asynchronous Fetch requests, JSON processing, dynamic rendering, and form validation.
- **Python and Flask:** Proposed backend service and POST endpoint.
- **Open-Meteo API:** External weather data provider.
- **Visual Studio Code:** Application development.
- **Browser Developer Tools:** Testing requests, responses, and error messages.
- **GitHub:** Version control and project documentation.

## 6. Implementation Steps

1. Create the project folder and organize the HTML, CSS, JavaScript, and Python files.
2. Review the Open-Meteo API documentation and identify the required endpoint and query parameters.
3. Create the webpage layout, including the weather table and search form.
4. Implement an asynchronous Fetch GET request with loading indicators and error handling.
5. Parse the returned JSON and dynamically display weather information.
6. Add form controls and client-side validation for location and temperature preferences.
7. Design the Flask POST endpoint contract for receiving JSON submissions.
8. Implement conditional CSS styling based on temperature values.
9. Test successful requests, invalid form entries, failed API requests, and different weather conditions.
10. Review the application design, document the endpoints, and upload the completed project to GitHub.

## Conclusion

This plan demonstrates how RESTful APIs can support interoperability between independent systems. By combining standard HTTP requests, JSON data, asynchronous Fetch, and local validation, the proposed application would allow users to retrieve and display weather information through a simple interface. The design also considers usability, error handling, and future backend integration.