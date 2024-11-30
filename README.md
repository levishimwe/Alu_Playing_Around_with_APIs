# Weather-Based Activity Planner
Overview
The Weather-Based Activity Planner is a web application that helps users plan their activities based on current and forecasted weather conditions. By combining weather data with local activity recommendations, it provides intelligent suggestions for both indoor and outdoor activities, helping users make informed decisions about their plans.
Features

Real-Time Weather Data:

Current weather conditions
3-day weather forecast
Temperature, precipitation, wind conditions, and more


# Activity Recommendations:

Filtered suggestions based on weather conditions
Indoor alternatives during bad weather
Outdoor opportunities during favorable conditions
Category-based filtering system


# User-Friendly Interface:

Responsive design for all devices
Intuitive search functionality
Easy-to-read weather displays

# Technical Stack

Frontend:

HTML5
CSS3 (with responsive design)
JavaScript (Vanilla JS)



APIs Used:

WeatherAPI (for weather data)
Foursquare Places API (for activity recommendations)



Installation and Local Setup
Prerequisites
API keys for WeatherAPI and Foursquare

# Local Development Setup

Clone the repository:
bashCopygit clone https://github.com/levishimwe/Alu_Playing_Around_with_APIs.git
cd weather-activity-planner

Create a .env file in the root directory:
CopyWEATHER_API_KEY=your_weather_api_key
FOURSQUARE_API_KEY=your_foursquare_api_key
PORT=5500

Start the development server:
Access the application at http://localhost:5500

Deployment Guide
Server Prerequisites

Ubuntu 20.04 or higher
Nginx installed and configured
SSL certificates (recommended for production)

# Deployment Steps

Server Setup (Web01 and Web02):
bashCopy# Update system
sudo apt update && sudo apt upgrade



Nginx Configuration:
nginxCopyserver {
    listen 80;
    server web01.levi02.tech;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

Load Balancer Setup (Lb01):
nginxCopyupstream backend {
    server web01.levi02.tech;
    server web02.levi02.tech;
}

server {
    listen 80;
    server_name levi02.tech;

    location / {
        proxy_pass http://backend;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}


# Security Considerations

API keys are stored securely in environment variables
Input validation implemented for all user inputs
Rate limiting configured for API endpoints
HTTPS enforced in production
Regular security updates and dependency maintenance

Error Handling
The application implements comprehensive error handling for:

API failures
Network connectivity issues
Invalid user inputs
Server errors
Rate limit exceedances

# Performance Optimization

Caching implemented for API responses
Optimized images and assets
Minified CSS and JavaScript in production
Gzip compression enabled
Load balancing for scalability

# Monitoring and Maintenance

Health check endpoints implemented
Error logging and monitoring
Regular backup procedures
Performance monitoring
API usage tracking

Development Challenges and Solutions
During the development of this application, several challenges were encountered and solved:

# API Rate Limiting:

Implemented caching system for API responses
Added retry logic for failed requests


# Cross-Browser Compatibility:

Extensive testing across different browsers
Implemented fallbacks for older browsers


# Mobile Responsiveness:

Developed mobile-first approach
Implemented responsive design patterns



# Future Enhancements
WeatherAPI for weather data
Foursquare for places API
Contributors and testers
Open source community

 # Contact
Levis Ishimwe  - i.levis@alustudent.com
Project Link: https://github.com/levishimwe/Alu_Playing_Around_with_APIs
Youtube Link: https://youtu.be/VLr5XV-fY1g?si=yQe_GwQJ-4IXzwUz
