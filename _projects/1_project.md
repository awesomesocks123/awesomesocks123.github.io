---
layout: page
title: Weather Color Palette
description: A web-app that suggests color palettes for outfits based on live weather conditions
img: assets/img/12.jpg
importance: 2
category: personal
github: https://github.com/awesomesocks123/weather-palette
---

# Weather Color Palette

[View Live Demo](https://weather-app-puce-pi-66.vercel.app/) | [View on GitHub](https://github.com/awesomesocks123/weather-app)

## Project Overview

Weather Color Palette is an intuitive web application that suggests outfit color combinations based on real-time weather conditions. By entering any city worldwide, users receive color palette recommendations that complement the current weather, helping them dress appropriately while maintaining style.

## Key Features

- **Global Weather Search**: Access current conditions for any city worldwide
- **Dynamic Color Suggestions**: Receive color palettes that match the weather mood
- **Palette Shuffling**: Generate new color combinations with a single click
- **Responsive Design**: Seamless experience across desktop and mobile devices
- **Real-time Updates**: Current weather data from OpenWeather API

## Implementation

The application uses a combination of modern web technologies and third-party APIs to deliver a seamless user experience:

- **React**: Component-based UI architecture
- **OpenWeather API**: Real-time weather data
- **Color Theory Algorithms**: Custom logic for weather-to-color mapping
- **CSS Variables**: Dynamic color application throughout the interface
- **Responsive Design**: Mobile-first approach with adaptive layouts

## Tech Stack
- **Frontend:** React 19, Next.js 15 (App Router), Tailwind CSS, DaisyUI
- **Backend/API:** Next.js API Routes (Edge/serverless functions)
- **Weather Data:** [WeatherAPI.com](https://weatherapi.com)
- **Color Data:** [Using Sanzo Wada's color combination via mattdesl dicionary of colour combinations](https://github.com/mattdesl/dictionary-of-colour-combinations)
- **Deployment:** Vercel

## How It Works
1. Enter a city name to get instant suggestions.
2. Select a city to see live weather and a color palette for your outfit.
3. All weather data is securely fetched via backend API routes.

**Created with Next.js, React, and Tailwind CSS.**
