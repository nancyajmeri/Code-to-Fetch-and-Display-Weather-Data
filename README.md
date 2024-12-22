# Code-to-Fetch-and-Display-Weather-Data

import requests

def get_weather(city, api_key):
    base_url = "http://api.openweathermap.org/data/2.5/weather"
    params = {
        'q': city,
        'appid': api_key,
        'units': 'metric'  # Use 'imperial' for Fahrenheit
    }
    response = requests.get(base_url, params=params)
    data = response.json()

    if response.status_code == 200:
        main = data['main']
        wind = data['wind']
        weather_description = data['weather'][0]['description']

        print(f"City: {city}")
        print(f"Temperature: {main['temp']}°C")
        print(f"Humidity: {main['humidity']}%")
        print(f"Pressure: {main['pressure']} hPa")
        print(f"Wind Speed: {wind['speed']} m/s")
        print(f"Weather Description: {weather_description}")
    else:
        print(f"City {city} not found.")

if __name__ == "__main__":
    city = "London"
    api_key = "your_openweathermap_api_key_here"  # Replace with your OpenWeatherMap API key
    get_weather(city, api_key)