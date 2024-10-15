# On-Demand Logistics Platform

## Overview
This application is an **On-Demand Logistics Platform** built using **Streamlit** for the frontend and **SQLite** for data storage. It provides logistics services that allow users to register, book vehicles, track shipments, and provide feedback on deliveries. The platform includes basic functionalities for drivers and admins to manage their interactions and monitor the service.

## Features
- **User Registration/Login**: Users can register and log in to the platform by providing their username, email, and password.
- **Vehicle Booking**: Users can book vehicles (car, van, truck) by selecting pickup and dropoff locations. The app estimates the price based on the distance and vehicle type.
- **Real-Time Tracking**: After booking, users can track the location of their vehicle on a map.
- **Feedback and Reviews**: After delivery, users can provide feedback and rate the service.
- **Admin Logs**: Admins can log actions and check the logs for auditing purposes.
- **Email Notifications**: Booking confirmations are sent via email to the user.
- **Driver Management**: A simple system for assigning drivers and tracking earnings.

## Technologies Used
- **Streamlit**: For the web interface and interactivity.
- **SQLite**: For local database management.
- **Geopy**: For calculating distances between pickup and dropoff locations.
- **Folium**: For mapping and real-time vehicle tracking.
- **Smtplib**: For sending email notifications.
- **Pandas**: For data manipulation.
- **HTML and CSS**: For custom styling of the web interface.

## Setup Instructions

### 1. Install Python
Ensure you have Python installed on your machine. You can download it from [python.org](https://www.python.org/downloads/). Make sure you have Python 3.6 or higher.


### 2. Database Setup

The application will automatically create the necessary tables in `logistics.db` if they don't already exist:

## Tables

- **users**: Stores user information
  - ID
  - username
  - email
  - password

- **bookings**: Stores booking information
  - ID
  - user
  - driver
  - pickup
  - dropoff
  - vehicle
  - estimated cost
  - status
  - favorite driver

- **drivers**: Stores driver details
  - ID
  - name
  - vehicle
  - availability
  - earnings

- **tracking**: Stores vehicle tracking data
  - booking ID
  - latitude
  - longitude

- **reviews**: Stores user feedback and ratings
  - booking ID
  - rating
  - feedback

- **admin_logs**: Logs admin actions
  - ID
  - action
  - timestamp

# Configuration

To modify the `send_email` function with your Gmail credentials, update the following variables in your code:

```python
from_address = "your_email@gmail.com"
password = "your_app_specific_password"
