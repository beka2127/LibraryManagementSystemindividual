# LibraryManagementSystemindividual
## Features

* **API Consumption:** Makes HTTP requests (GET, POST, PUT, DELETE) to a RESTful API.
* **Data Display:** Shows data fetched from the API in a user-friendly Windows Forms interface.
* **CRUD Operations:** Allows users to perform Create, Read, Update, and Delete operations on data (e.g., Books, Borrowers, Loans, depending on the API it connects to).
* **User Interface:** A standard Windows Forms graphical user interface.

## Technologies Used

* **C#:** The primary programming language.
* **Windows Forms:** For building the desktop graphical user interface.
* **.NET Framework / .NET Core (depending on project setup):** The framework on which the application is built.
* **HttpClient:** For making HTTP requests to the web API.
* **JSON.NET (Newtonsoft.Json):** For serializing and deserializing JSON data.

## Prerequisites

Before you begin, ensure you have the following installed on your machine:

* **Visual Studio:** A powerful IDE for C# and .NET development.
    * Ensure the ".NET desktop development" workload is installed.
* **.NET SDK:** The specific version corresponding to your project (e.g., .NET 6.0, .NET 7.0, or older .NET Framework versions).
* **A Running Backend API:** This application requires a separate backend API to function. Ensure your API (e.g., the Library Management System API) is up and running and accessible.

## Installation Guide

Follow these steps to set up and run the Windows Forms application on your local machine.

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YourUsername/YourRepoName.git](https://github.com/YourUsername/YourRepoName.git)
    cd YourRepoName
    ```
    *(Adjust `YourRepoName` if this Windows Forms project is in a subfolder, e.g., `cd YourRepoName/WindowsFormsClient`)*
2.  **Open the project in Visual Studio:**
    * Navigate to the project folder (e.g., `WindowsFormsClient.sln` or `WindowsFormsClient.csproj`).
    * Double-click the `.sln` file to open the solution in Visual Studio.
3.  **Update API Base URL:**
    * Locate the configuration file where the API base URL is defined (ee.g., `App.config`, or directly in your `Form1.cs` or a dedicated `ApiClient.cs` class).
    * Ensure the URL points to your running backend API (e.g., `https://localhost:7086`).
        ```csharp
        // Example in C# code:
        private const string ApiBaseUrl = "https://localhost:7086/"; // Adjust if your API runs on a different port/address
        ```
4.  **Restore NuGet Packages:**
    * In Visual Studio, right-click on the project in the Solution Explorer.
    * Select "Manage NuGet Packages..."
    * Click "Restore" to download any missing dependencies (like Newtonsoft.Json).
5.  **Build the Project:**
    * In Visual Studio, go to `Build` > `Build Solution` (or press `Ctrl+Shift+B`).
6.  **Run the Application:**
    * Press `F5` in Visual Studio, or click the "Start" button.

## How It Works

This Windows Forms application functions as a client to a RESTful API.

1.  **API Client Layer:** The application uses `HttpClient` to send HTTP requests (GET, POST, PUT, DELETE) to specific endpoints of the backend API.
2.  **Data Serialization/Deserialization:** JSON.NET is used to convert C# objects into JSON strings for sending data to the API, and to parse JSON responses from the API back into C# objects.
3.  **User Interface:** The Windows Forms provide text boxes for input, buttons for actions (Add, Edit, Delete, Refresh), and DataGridViews or ListBoxes to display retrieved data.
4.  **Asynchronous Operations:** API calls are often made asynchronously (`async/await`) to keep the UI responsive while waiting for network responses.

*(You can expand on this section with more specific details about how your forms are structured and what actions trigger which API calls, e.g.:)*

* **Main Form:** Likely `Form1.cs` or a dashboard form, acting as the main entry point.
* **Data Grids:** Display lists of Books, Borrowers, or Loans.
* **Input Forms:** Separate forms or panels for adding/editing specific entities.

## Screenshots

*(Create an `images/` folder in your repository root (or within this project's folder) and place your screenshots there. Then link them.)*

* **Main Application Window:**
    ![Main Application Window](images/windows_form_main_window.png)
* **Adding a New Record (e.g., Book Form):**
    ![Add New Record Form](images/windows_form_add_record.png)
* **Editing a Record:**
    ![Edit Record Form](images/windows_form_edit_record.png)
* **Data Display (e.g., Books List):**
    ![Data Display Example](images/windows_form_data_display.png)

*(Add more screenshots here for all functionalities you have, similar to the React app README.)*

## Troubleshooting

* **"The remote server returned an error: (401) Unauthorized."**:
    * Ensure your backend API requires authentication and you are providing a valid JWT token (if applicable for your desktop client).
    * If your API requires login, ensure the desktop application has a mechanism to log in and obtain/send the token.
* **"No connection could be made because the target machine actively refused it" / "The remote name could not be resolved"**:
    * The backend API is not running or is not accessible at the configured `ApiBaseUrl`.
    * Verify the `ApiBaseUrl` in your application's code or config file is correct.
    * Ensure your backend API is running and accessible (e.g., can you access its Swagger UI in a browser?).
    * Check for firewall issues blocking the connection.
* **JSON Serialization/Deserialization Errors:**
    * Ensure the C# model classes in your Windows Forms application exactly match the JSON structure returned by your API.
    * Check for type mismatches (e.g., trying to parse a string into an integer).
* **UI Not Responding:**
    * Ensure you are using `async/await` for all network (API) calls to prevent freezing the UI.
as usual i attached screenshots of the working api in the images folder
