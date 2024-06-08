# WeatherForecast_Vue
 
## Weather Forecast Web App with Vite, Vue.js & Tailwind CSS

This web application displays current weather and a 5-day forecast using Vite for development speed, Vue.js for building the UI, and Tailwind CSS for responsive styling.

### Features

* Displays current weather conditions for a specific location.
* Provides a 5-day weather forecast.
* Utilizes Tailwind CSS for a customizable and responsive user interface.

### Technologies

* **Frontend:**
    * Vite: Lightning-fast development server and bundler.
    * Vue.js: Progressive JavaScript framework for building user interfaces.
    * Tailwind CSS: Utility-first CSS framework for rapid styling.
* **API:** WeatherAPI.com (requires API key)

### Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/<your-username>/weather-forecast-app.git
   ```

2. Install dependencies:

   ```bash
   cd weather-forecast-app
   npm install
   ```

### Development

1. Start the development server:

   ```bash
   npm run dev
   ```

   This will open the application in your browser at http://localhost:3000/

2. Make changes to the code in the `src` directory.
3. The development server will automatically recompile and refresh the browser on file saves.

### Deployment

**Note:** Deployment instructions depend on your chosen hosting platform.

Here's a general guideline:

1. Build the production-ready version:

   ```bash
   npm run build
   ```

2. Deploy the contents of the `dist` directory to your web server.

### WeatherAPI.com Integration

1. **Obtain an API Key:** Sign up for a free account on WeatherAPI.com [https://www.weatherapi.com/](https://www.weatherapi.com/). Once registered, you'll receive an API key.
2. **API Configuration:** Update the application code to include your API key and make API calls to retrieve weather data. Refer to the WeatherAPI.com documentation [https://www.weatherapi.com/docs/](https://www.weatherapi.com/docs/) for details on API calls and available data.

**Example:**

The provided documentation offers examples and guides on integrating their API with various frameworks. You'll need to adapt those examples to fit the context of your Vue.js application.

### Contributing

We welcome contributions! See the `CONTRIBUTING.md` file for guidelines.

### License

This project is licensed under the MIT License. See the `LICENSE` file for details.
