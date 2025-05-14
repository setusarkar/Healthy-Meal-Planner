# Healthy Meal Planner

A comprehensive web application that helps users plan meals, track calories, and identify food items using image recognition technology.

## Repository

Official repository: [https://github.com/setusarkar/Healthy-Meal-Planner](https://github.com/setusarkar/Healthy-Meal-Planner)

## Overview

Healthy Meal Planner is a lightweight, browser-based tool that offers two main ways to plan and track your meals:

1. **Basic Meal Planner**: Select foods from a pre-defined list with nutrition information
2. **AI Food Analysis**: Upload food images to identify items and get nutritional information

## Features

### Basic Meal Planner
- Select meals by type (Breakfast, Lunch, Dinner, Snack)
- Choose foods from a pre-defined database
- Set quantities for accurate calorie counting
- View food previews with nutritional information
- Add foods to your daily meal plan
- Track daily nutritional totals

### AI Image Analysis
- Upload food images with drag-and-drop support
- Automatic food detection using image recognition
- Retrieve nutritional information
- Add detected foods to your meal plan
- Offline mode for using without API keys

### Shared Features
- Daily calorie and nutrient summary
- Save meal plans to local storage
- Clear and intuitive user interface
- Responsive design that works on desktop and mobile

## Getting Started

### Installation

1. **Clone the repository**
   ```
   git clone https://github.com/yourusername/healthy-meal-planner.git
   cd healthy-meal-planner
   ```

2. **Launch the Application**
   
   Simply open `index.html` in your browser to start using the application.
   
   For development, you can use one of these options:
   
   - **VS Code with Live Server extension (recommended):**
     1. Install [VS Code](https://code.visualstudio.com/) if you don't have it
     2. Install the [Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
     3. Right-click on the `index.html` file and select "Open with Live Server"
     4. The application will open in your default browser and automatically reload when you make changes
   
   - **Python's built-in server:**
     ```
     python -m http.server
     ```
     Then visit `http://localhost:8000`

### Operation Modes

The application can run in three modes:

1. **Basic Mode** - No API keys required
   - Use the "Basic Meal Planner" tab
   - Select from pre-defined food items
   - All functionality works without internet connection

2. **Offline AI Mode** - No API keys required
   - Use the "AI Image Analysis" tab
   - Upload images which will be "analyzed" offline
   - Default food identification (Apple) will be used
   - Mock nutrition data will be provided

3. **Full AI Mode** - Requires API keys
   - Use with Cloudmersive API (image recognition)
   - Use with Nutritionix API (nutrition data)
   - Most accurate results

## Using Basic Meal Planner

1. The Basic Meal Planner tab is selected by default when you open the app
2. Select the meal type (Breakfast, Lunch, Dinner, Snack)
3. Choose a food item from the dropdown menu
4. Set the quantity as needed
5. Click "Add to Meal Plan"
6. View your daily meal plan and nutritional summary
7. Use the "Clear Plan" button to start over
8. Use the "Save Plan" button to store your plan in local storage

## Using AI Image Analysis

### In Offline Mode (Default)

1. Click the "AI Image Analysis" tab
2. Upload a food image by clicking the upload area or dragging and dropping
3. Select the meal type (Breakfast, Lunch, Dinner, Snack)
4. Click "Analyze Food"
5. You'll see an information message indicating offline mode
6. A default "Apple" food item will be detected with nutritional information
7. Click "Add to Meal Plan" to include it in your daily plan

### With API Integration

1. Set up API keys (see "API Configuration" section)
2. Follow the same steps as offline mode
3. The app will use actual image recognition to identify the food
4. Real nutritional data will be provided for the detected food

## API Configuration

### Cloudmersive API (Image Recognition)

1. Go to [Cloudmersive Image Recognition API](https://cloudmersive.com/image-recognition-api)
2. Sign up for the free tier (800 API calls per month)
3. Get your API key
4. Open `app.js` and update:
   ```javascript
   const CLOUDMERSIVE_API_KEY = 'YOUR_API_KEY_HERE';
   ```

### Nutritionix API (Nutritional Data)

1. Go to [Nutritionix API](https://developer.nutritionix.com/signup)
2. Sign up for an account
3. Get your App ID and API Key
4. Open `app.js` and update:
   ```javascript
   const NUTRITIONIX_APP_ID = 'YOUR_APP_ID_HERE';
   const NUTRITIONIX_API_KEY = 'YOUR_API_KEY_HERE';
   ```

## Testing APIs

The "Test API" button in the AI Image Analysis tab allows you to test your API configuration:

- In offline mode, it will show a demo result
- With valid API keys, it will test the connection to the services

## Customizing the Food Database

You can easily customize the built-in food database by modifying the `foodDatabase` array in `app.js`. Each food item requires the following properties:

```javascript
{
    id: 'unique_id',
    name: 'Food Name',
    calories: 100,
    protein: 10,
    carbs: 10,
    fat: 5,
    image: 'url_to_food_image'
}
```

## Troubleshooting

### API Issues

If you're having trouble with the API integration:

1. Check your browser console (F12 > Console tab) for detailed error messages
2. Verify your API keys are correctly entered in `app.js`
3. Ensure you have an active internet connection
4. For Cloudmersive, verify you haven't exceeded the monthly free tier limit
5. Try the "Test API" button to check API connectivity

### Image Analysis Not Working

If the image analysis doesn't recognize foods correctly:

1. Ensure the image clearly shows the food item
2. Use images with good lighting and minimal background
3. Try simpler foods (single items like an apple rather than complex dishes)
4. Verify your API configuration
5. Check if you're in offline mode (you'll see an information message)

### Meal Plan Not Saving

If your meal plan doesn't save between sessions:

1. Make sure your browser supports and allows local storage
2. Check that you're not in incognito/private browsing mode
3. Ensure you have clicked the "Save Plan" button
4. Try clearing your browser cache and reloading the page

## Technical Implementation

### Technologies Used

- **Frontend**: HTML, CSS, JavaScript, Tailwind CSS
- **API Integration**: Fetch API
- **Image Processing**: FileReader API, Base64 encoding
- **Storage**: localStorage API

### Code Structure

- `index.html` - Main application structure and UI
- `styles.css` - Custom styles and responsive design
- `app.js` - Core application logic and API integration
- `README.md` - Documentation

### Key Functions

- `init()` - Initializes the application
- `handleImageUpload()` - Processes uploaded images
- `analyzeFood()` - Coordinates the food analysis process
- `detectFoodWithVisionAPI()` - Handles image recognition
- `getNutritionInfo()` - Retrieves nutritional data
- `addFoodToMealPlan()` - Adds foods to the meal plan
- `updateDailySummary()` - Calculates nutritional totals
- `saveMealPlan()` - Saves the meal plan to localStorage

## Limitations

- In offline mode, food identification is not based on actual image analysis
- The nutritional information is an estimate and may vary from actual values
- Single-item foods are more accurately identified than mixed dishes or meals
- The basic planner uses a limited food database
- API free tiers have usage limitations

## Future Enhancements

Potential future improvements could include:

- Support for multiple days of meal planning
- Calorie and nutrient goal setting
- Recipe suggestions based on available foods
- Barcode scanning for packaged foods
- Export/import meal plans
- User accounts for cloud storage of meal plans

## License

[MIT License](LICENSE)

## Author

- **Setu Sarkar** - [GitHub Profile](https://github.com/setusarkar)

## Acknowledgements

- Cloudmersive API for image recognition
- Nutritionix API for nutrition data
- Tailwind CSS for styling
- Unsplash for food images 