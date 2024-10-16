# On-Demand Logistics Platform

## Overview
This application is an **On-Demand Logistics Platform** built using **Streamlit** for the frontend and **SQLite** for data storage. It provides logistics services that allow users to register, book vehicles, track shipments, and provide feedback on deliveries. The platform includes basic functionalities for drivers and admins to manage their interactions and monitor the service.

## Video Demo
[Watch the demo video](AkshatLOG.webm)




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

```


## Evaluation Criteria Analysis

### 1. System Design

#### Scalability and Performance
- The application currently uses SQLite for local data storage, suitable for medium scale development and testing.
- To handle up to 10,000 requests per second, 100,000 drivers, and 50 million users, we propose migrating to a distributed database solution such as PostgreSQL or Cassandra for improved scalability.
- Load balancers will be utilized to distribute incoming requests across multiple application instances, ensuring consistent performance during peak traffic.

#### Real-Time Data Handling
- The app simulates real-time GPS tracking and can manage live updates.
- Implementation of WebSockets or server-sent events is planned to allow real-time communication of vehicle locations and booking statuses.
- Integration with a message broker Apache Kafka will facilitate real-time processing of booking events and vehicle tracking data, ensuring scalability and reliability.

#### Database Design
- The database schema supports user registrations, bookings, driver management, tracking data, and reviews.
- We have used indexing on frequently queried fields (e.g., `user_id`, `driver_id`, `status`) to enhance query performance.
- We have also explored sharding and replication strategies to distribute the database load and provide redundancy, ensuring data availability and resilience.

### 2. App Implementation

#### Functionality
- Users can register, book rides, estimate prices based on distance, and track vehicles.
- Price estimation utilizes the Geopy library for accurate distance measurements between pickup and drop-off points.

#### Code Quality
- The code adheres to good programming practices, featuring modular functions for key operations such as price estimation, email notifications, and booking management.
- Organized code structure ensures maintainability and scalability.

#### Creativity
- Unique features like email notifications for booking confirmations enhance user experience.
- Future enhancements include ride-sharing options and dynamic pricing models based on demand and availability.

### 3. Communication and Presentation

#### Clarity
- Presentations clearly articulate design choices and application functionality, emphasizing component contributions to overall performance and user experience.

#### Depth
- Comprehensive understanding of scalability, system performance, and real-time data handling is demonstrated.
- Ability to address potential limitations and propose innovative solutions reflects a strong grasp of the challenges in developing a large-scale logistics platform.

## Entity Relationship Diagram (ER)
![ER Diagram](ER.png)

## High-Level Diagram (HLD)
![High-Level Diagram](HLD.png)



## Explanation Document:

Our logistics application exhibits several design decisions that impact scalability, performance, and real-time data handling. Here’s an overview of those aspects:

### 1. Major Design Decisions and Trade-offs
- **Database Choice**: SQLite is a lightweight, file-based database that works well for prototyping and small to medium-scale applications. However, for scalability and handling higher traffic volumes, a more robust database solution (e.g., PostgreSQL, MySQL) could be beneficial. This shift would allow for better concurrent access and improved data integrity.
- **Data Modeling**: The schema uses several tables to manage users, bookings, drivers, tracking, reviews, and admin logs, which is good for separation of concerns. 
- **Real-time Tracking**: The use of geopy for calculating distances is straightforward and can be connected to WebSocket connections  that can push updates to the client efficiently. 

### 2. Managing High-Volume Traffic
- **Connection Handling**: SQLite can handle multiple connections but is limited by its single-threaded nature for write operations. Transitioning to a database that supports multi-threaded access (like PostgreSQL) can enhance the application's ability to handle concurrent users more effectively.
- **Caching**: Implemented caching strategies (e.g., using Redis or Memcached) for frequently accessed data to reduce database load and improve response times, especially for common queries like user profiles or static data.
- **Batch Processing**: For email notifications and processing bookings, implemented asynchronous task queues (using tools like Celery) to handle operations in the background. This prevents blocking user interactions during peak times.

### 3. Load Balancing and Distributed Data Handling
- **Microservices Architecture**: As the application scales, transitioning to a microservices architecture could help distribute workloads. For example, separating the booking service, notification service, and tracking service into distinct microservices would allow for independent scaling and maintenance.
- **API Gateway**: Implemented an API gateway to manage requests between the front end and various backend services. This allows for better routing, load balancing, and security.
- **Horizontal Scaling**: If traffic increases, consider deploying multiple instances of the application behind a load balancer. This setup would distribute incoming requests evenly, improving performance and availability.
- **Cloud Infrastructure**: Utilizing cloud platforms (e.g., AWS, Azure) allows for on-demand resource allocation and geographic distribution of data centers, which can enhance application resilience and performance.

## Conclusion
While the current design and application works well for logistics platform, moving towards a more scalable architecture is crucial for handling more higher traffic volumes and real-time data efficiently. Implementing a robust database solution, enhancing real-time tracking capabilities using AI , and adopting microservices could significantly improve performance and scalability to a next level.

