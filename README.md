# Atlan-Challenge-

# Atlan Engineering Internship Task

### On-Demand Logistics Platform for Goods Transportation

---

### **Context:**

You are tasked with designing and building a highly scalable logistics platform that allows users to book transportation services for moving goods. The platform connects users who need to transport items with a fleet of drivers, providing real-time availability, pricing, and tracking of vehicles. The system should be able to handle extremely high traffic efficiently while ensuring smooth coordination between users and drivers.

The platform must be able to handle 10,000 requests per second, with a registered base of 100,000 drivers and 50 million users globally.

---

### **Problem Statement:**

Design a scalable system that handles the following aspects of the logistics platform:

### **1. User Features:**

- **Booking Service:**
    - Users should be able to book a vehicle for transporting goods.
    - The booking should include details like pickup location, drop-off location, type of vehicle required, and an estimated cost.
- **Real-Time Tracking:**
    - Once a vehicle is booked, users should be able to track the driver’s location in real-time.
- **Price Estimation:**
    - Provide an upfront price estimation based on factors like distance, vehicle type, and current demand.

### **2. Driver Features:**

- **Job Assignment:**
    - Drivers should receive and accept booking requests.
    - After accepting, they should see the pickup and drop-off locations and start the journey.
- **Job Status Updates:**
    - Drivers can update the status of the job (e.g., en route to pickup, goods collected, delivered).

### **3. Admin Features:**

- **Fleet Management:**
    - Admins should be able to manage the fleet of available vehicles, monitor driver activity, and analyze booking data.
- **Data Analytics:**
    - Implement basic analytics to track the number of trips completed, average trip time, and driver performance.

---

### **System Design Requirements:**

1. **Scalability:**
    - The system should handle **10,000 concurrent requests per second** globally.
    - Design the system to support a large user base with **50 million registered users** and **100,000 registered drivers**.
    - Explain how you will handle load balancing, distributed database architectures, and any other techniques to manage this scale.
2. **Real-Time Data and GPS Tracking:**
    - Design a mechanism to handle real-time GPS data for **thousands of concurrent users** tracking vehicles.
    - Discuss how to manage frequent updates to vehicle locations without overloading the system.
3. **Database Design:**
    - Design a database schema that supports managing users, drivers, bookings, vehicles, and tracking data for this large-scale operation.
    - Address how you will handle high-frequency updates (such as vehicle location) while ensuring consistency and performance across databases.
4. **Matching Algorithm:**
    - Implement a matching algorithm that efficiently assigns drivers to users based on factors like proximity, vehicle type, and availability, at scale.
    - Explain how this algorithm will handle **thousands of concurrent users and drivers.**
5. **Pricing Model:**
    - Explain how you will build a pricing model that accounts for variables like distance, vehicle size, demand, and global regions.
    - Address how surge pricing could be implemented and scaled.

---

### **Bonus:**

- Add a feature for users to schedule future bookings, and explain how it would impact system performance.

---

### **Deliverables:**

### **1. Working Application:**

- Build a web or mobile application that allows users to book transportation services, track vehicles in real-time, and receive price estimates.
- The application should also allow drivers to accept bookings and update job statuses.

### **2. High-Level Architecture Diagram:**

- Provide a diagram showing the structure of the system, including key components such as load balancers, databases, real-time GPS tracking mechanisms, and caching systems.

### **3. Entity-Relationship (ER) Diagram:**

- Create an ER diagram that defines the relationships between key entities like users, drivers, bookings, vehicles, and payment records.

### **4. Explanation Document:**

- Write a brief document (1-2 pages) explaining:
    - Major design decisions and trade-offs, especially related to scalability and high-performance handling of real-time data.
    - How the system is capable of managing the specified high-volume traffic.
    - How you’ve implemented load balancing and distributed data handling.

### **5. Video Submission:**

- Record a 5-7 minute video where you:
    - Walk through the application and demonstrate its key features.
    - Explain the system design and technical decisions made.
    - Discuss any challenges you faced while building a system of this scale, and how you resolved them.

---

### **Evaluation Criteria:**

### **1. System Design:**

- **Scalability and Performance:** Can the system handle 10,000 requests per second, 100,000 drivers, and 50 million registered users?
- **Real-Time Data Handling:** How efficiently does the system manage real-time GPS tracking and booking updates?
- **Database Design:** Does the schema support large-scale operations with frequent updates and transactions?

### **2. App Implementation:**

- **Functionality:** Does the app allow users to book rides, track vehicles, and provide accurate price estimates?
- **Code Quality:** Is the code clean, structured, and maintainable?
- **Creativity:** Are there any unique features or optimizations that enhance the user or driver experience?

### **3. Communication and Presentation:**

- **Clarity:** How well does the candidate explain their design and approach in the video?
- **Depth:** Does the candidate demonstrate an understanding of scalability, system performance, and real-time data handling?

---

### **Submission Guidelines:**

- **Code:** Upload your project to a GitHub repository and share the link. To prevent plagiarism, we recommend using a meaningless or obfuscated project name.
- **App:** Optionally deploy the app using a platform like Vercel, Netlify, or Heroku, and share the link.
- **Documentation, ER Diagram, and Video:** Share links to your architecture diagram, ER diagram, explanation document (PDF), and video walkthrough.
