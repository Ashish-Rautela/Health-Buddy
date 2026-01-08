# 🥗 Health Buddy - Food Label Analyzer

> "Let food be thy medicine and medicine be thy food." - Hippocrates

A modern, AI-powered web application that analyzes food labels and provides instant nutritional insights. Simply snap a photo or upload an image of any food label to get comprehensive health analysis, ingredient breakdown, and personalized recommendations.

## ✨ Features

### 📸 **Smart Image Capture**
- **Camera Integration**: Take photos directly from your device's camera
- **File Upload**: Upload images from your device (JPEG, PNG, GIF, WebP)
- **Mobile-Friendly**: Optimized for both desktop and mobile experiences

### 🎯 **Quick Verdict System**
- **Buy/Moderate/Avoid** recommendations with clear visual indicators
- Color-coded verdicts (Green for Buy, Yellow for Moderate, Red for Avoid)
- Key points summary for quick decision-making
- "Best For" and "Avoid If" personalized suggestions

### 📊 **Comprehensive Nutrition Analysis**
- **Health Score**: Overall rating with detailed pros and cons
- **Macronutrient Distribution**: Interactive doughnut chart showing Fat, Carbs, and Protein percentages
- **Calorie Information**: Per serving nutritional data
- **Serving Size**: Clear portion information

### 🧪 **Ingredient Insights**
- **Main Ingredients**: Primary components listed
- **Beneficial Ingredients**: Health-positive components highlighted in green
- **Concerning Ingredients**: Potentially problematic items flagged in red
- **Additives & Preservatives**: Complete list of food additives

### ⚠️ **Allergen Detection**
- Automatic allergen identification
- Clear visual warnings for common allergens
- Color-coded alert system

### 💬 **Interactive AI Chat**
- Ask questions about ingredients, nutrition, or health impacts
- Get personalized insights based on your concerns
- Suggested questions for common queries
- Real-time conversational interface

### 🎨 **Modern UI/UX**
- Clean, gradient-based design
- Responsive layout for all screen sizes
- Smooth animations and transitions
- Sticky header and chat interface
- Loading states and error handling

## 🚀 Getting Started

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, Edge)
- Backend API server running (see Backend Setup section)
- Camera access for photo capture feature

### Installation

1. **Clone or download the HTML file**
   ```bash
   # Save the HTML file as index.html
   ```

2. **Configure Backend URL**
   
   Update the API base URL in the script section:
   ```javascript
   const API_BASE_URL = 'https://your-backend-url.com';
   ```

3. **Open in Browser**
   ```bash
   # Simply open index.html in your browser
   # Or serve using a local server:
   python -m http.server 8000
   # Then visit http://localhost:8000
   ```

## 🔧 Backend Requirements

The frontend expects a backend API with the following endpoints:

### 1. Health Check
```http
GET /api/health
```
Returns API status for connectivity checks.

### 2. Analyze Image
```http
POST /api/analyze
Content-Type: multipart/form-data

Body:
- image: File (JPEG, PNG, GIF, WebP)
```

**Expected Response:**
```json
{
  "success": true,
  "sessionId": "unique-session-id",
  "data": {
    "formatted": {
      "overview": {
        "productName": "Product Name",
        "brand": "Brand Name",
        "tagline": "Product tagline",
        "highlights": ["Feature 1", "Feature 2"]
      },
      "quickVerdict": {
        "recommendation": "buy|moderate|avoid",
        "title": "Verdict Title",
        "summary": "Brief summary",
        "keyPoints": ["Point 1", "Point 2"],
        "bestFor": ["Use case 1"],
        "avoidIf": ["Condition 1"]
      },
      "nutrition": {
        "calories": "200",
        "servingSize": "100g",
        "macros": {
          "fat": { "percentage": "30" },
          "carbs": { "percentage": "50" },
          "protein": { "percentage": "20" }
        }
      },
      "healthScore": {
        "overall": 75,
        "category": "Good",
        "pros": ["Pro 1", "Pro 2"],
        "cons": ["Con 1", "Con 2"]
      },
      "ingredients": {
        "main": ["Ingredient 1", "Ingredient 2"],
        "beneficial": ["Good ingredient"],
        "concerning": ["Bad ingredient"],
        "additives": ["Additive 1"]
      },
      "allergens": ["Milk", "Nuts"],
      "recommendations": "Health recommendations text"
    }
  },
  "suggestedQuestions": [
    "Is this suitable for diabetics?",
    "What are the preservatives used?"
  ]
}
```

### 3. Chat Interface
```http
POST /api/chat
Content-Type: application/json
Headers:
- X-Session-ID: session-id-from-analyze

Body:
{
  "message": "User question"
}
```

**Expected Response:**
```json
{
  "success": true,
  "response": "AI response text with formatting",
  "suggestedQuestions": ["Follow-up 1", "Follow-up 2"]
}
```

## 📱 Usage Flow

1. **Launch Application**: Open the HTML file in your browser
2. **Scan or Upload**: Choose between taking a photo or uploading an image
3. **Wait for Analysis**: The AI processes your image (takes a few seconds)
4. **Review Results**: 
   - Check the Quick Verdict at the top
   - Explore nutritional information
   - Review ingredient analysis
   - Check for allergens
5. **Ask Questions**: Use the chat interface for personalized queries
6. **New Scan**: Click "New Scan" button to analyze another product

## 🎨 Design Features

- **Gradient Backgrounds**: Modern teal/green gradient theme
- **Color-Coded System**:
  - 🟢 Green: Positive/Buy/Beneficial
  - 🟡 Yellow: Moderate/Caution
  - 🔴 Red: Negative/Avoid/Concerning
- **Responsive Grid**: Adapts to mobile, tablet, and desktop
- **Sticky Elements**: Header and chat box stay accessible
- **Loading States**: Clear feedback during processing
- **Error Handling**: User-friendly error messages

## 🛠️ Technical Stack

- **Frontend Framework**: Vanilla JavaScript (no dependencies)
- **Charting Library**: Chart.js 4.4.0 (via CDN)
- **Styling**: Custom CSS with modern features
- **Camera API**: MediaDevices WebRTC API
- **Canvas API**: For image capture processing

## 🔒 Privacy & Security

- Images are processed server-side and not stored permanently
- Session-based chat ensures conversation privacy
- Camera access requires user permission
- No tracking or analytics implemented

## 📂 File Structure

```
health-buddy/
├── index.html          # Main application file
│   ├── HTML structure
│   ├── CSS styles (embedded)
│   └── JavaScript logic (embedded)
└── README.md          # This file
```

## 🐛 Error Handling

The application includes comprehensive error handling:

- **Runtime Errors**: Visual error banners with stack traces
- **API Failures**: User-friendly error messages
- **Network Issues**: Connectivity warnings on page load
- **Camera Access**: Fallback to file upload
- **Invalid Images**: Clear feedback and retry options

## 🌐 Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ⚠️ Mobile browsers (with camera support)

## 📝 Configuration Options

### API Endpoint
```javascript
const API_BASE_URL = 'https://your-backend-url.com';
```

### Supported Image Formats
- JPEG/JPG
- PNG
- GIF
- WebP
- Maximum size: 10MB (configurable on backend)

## 🚧 Known Limitations

- Requires active internet connection for analysis
- Backend API must be running and accessible
- Camera feature requires HTTPS (except on localhost)
- Complex labels may require multiple attempts
- Chat responses depend on backend AI quality

## 🤝 Contributing

To extend or modify Health Buddy:

1. The codebase is self-contained in a single HTML file
2. CSS is in the `<style>` section
3. JavaScript is in the `<script>` section
4. Chart.js is loaded via CDN

### Key Functions to Modify:

- `processImage()`: Image upload handling
- `renderQuickVerdict()`: Verdict display
- `renderProductOverview()`: Product info display
- `sendMessage()`: Chat functionality
- `formatMessage()`: Chat message formatting

## 📄 License

This project is provided as-is for educational and personal use.

## 🆘 Support

For issues or questions:
1. Check browser console for error messages
2. Verify backend API is running and accessible
3. Ensure camera permissions are granted
4. Try different image formats or lighting conditions

## 🎯 Roadmap

Potential future enhancements:
- [ ] Offline mode with cached results
- [ ] Multiple language support
- [ ] Barcode scanning integration
- [ ] Comparison mode for multiple products
- [ ] Export reports as PDF
- [ ] User accounts and history
- [ ] Voice input for chat
- [ ] Dark mode toggle

---

**Built with ❤️ for healthier eating choices**