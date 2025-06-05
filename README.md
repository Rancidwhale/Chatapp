# VootlaSaiCharan_Chatroom-1

A real-time one to one chat web application built using Java 17, MySQL, Spring Boot, Spring Security, WebSocket, and Thymeleaf. This application allows users to chat with other users is a seperate environment, featuring a modern tech stack with a responsive user interface.

## Features

- **Instant Messaging**: Seamless, real-time communication enabled by WebSocket technology for instantaneous message delivery.
- **Secure Login and Registration**: User authentication and access management powered by Spring Security for a robust and secure experience.
- **User Notifications**: Instant alerts for new messages and user activity, such as logins, ensuring you stay updated in real-time.
- **Chat History Persistence**: Effortless storage and retrieval of chat data from a MySQL database, providing access to previous conversations anytime.
- **Responsive Interface**: Optimized for all devices using Bootstrap, delivering a consistent and user-friendly design across platforms.
- **Integrated Social Media Links**: Quick access to social profiles directly from the chatroom header for easy networking.

## Tech Stack

- **Backend**: Java 17, Spring Boot, Spring Security, MySQL Database, Lombok
- **Frontend**: Thymeleaf, Bootstrap, Font Awesome
- **Real-Time Communication**: Spring WebSocket, STOMP protocol
- **Build Tool**: Maven

## Setup Instructions

### Prerequisites
- Java 17 or higher
- Maven 3.6+

### Steps to Run Locally

1. **Clone the Repository**:
   ```sh
   git clone https://github.com/vootlasaicharan/chatroom-1.git
   cd ChatApp
   ```
   
2. Create MySQL database using [SQLScript](src/main/resources/static/sql-script/SQLScript.txt)

3. Update MySQL password in [application.properties](src/main/resources/application.properties)

4. **Build the Project**:
   ```sh
   mvn clean install
   ```

5. **Run the Application**:
   ```sh
   mvn spring-boot:run
   ```

6. **Access the Application**:
   Open your browser and navigate to `http://localhost:8080`.

## Usage

- **Login**: Create a new account or securely log in using your existing credentials to access the platform.
- **Chat**: Engage in real-time conversations with other users. Stay informed with instant notifications when new users join or send you messages.


# Installing MySQL on Ubuntu

Follow these steps to install MySQL on an Ubuntu system:

1. **Update Package Index:**
    - Open a terminal.
    - Run the command:
      ```sh
      sudo apt update
      ```
      This updates the package index to ensure you get the latest version of MySQL.

2. **Install MySQL Server:**
    - Run the command:
      ```sh
      sudo apt install mysql-server
      ```
      This installs the MySQL server package on your system.

3. **Start MySQL Service:**
    - Run the command:
      ```sh
      sudo systemctl start mysql
      ```
      This starts the MySQL service.
    - Optionally, run:
      ```sh
      sudo systemctl enable mysql
      ```
      This enables MySQL to start automatically at boot.

4. **Verify MySQL Installation:**
    - Run the command:
      ```sh
      sudo systemctl status mysql
      ```
      This checks the status of the MySQL service. You should see a message indicating that MySQL is active and running.

5. **Secure MySQL Installation:**
    - Run the command:
      ```sh
      sudo mysql_secure_installation
      ```
      This script helps you improve the security of your MySQL installation. Follow the prompts to set the root password, remove anonymous users, disallow root login remotely, remove test databases, and reload privilege tables.

6. **Access MySQL:**
    - Run the command:
      ```sh
      sudo mysql
      ```
      This opens the MySQL shell as the root user. You can now start creating databases and users.

You have successfully installed MySQL on your Ubuntu system.

## Creating a MySQL User with a Password

To create a new MySQL user with the username `root` and password `Test@123`, follow these steps:

1. **Create a New User:**
    - In the MySQL shell, run the following command:
      ```sql
      ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Test@123';
      ```
      This creates a new user `root` with the password `Test@123`.

2. **Grant Privileges to the User:**
    - Run the command:
      ```sql
      GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION;
      ```
      This grants all privileges to the user `root` on all databases and tables.

3. **Flush Privileges:**
    - Run the command:
      ```sql
      FLUSH PRIVILEGES;
      ```
      This reloads the privilege tables to ensure that the changes take effect.

4. **Exit MySQL Shell:**
    - Run the command:
      ```sql
      EXIT;
      ```
      This exits the MySQL shell.

You have successfully created a MySQL user with the username `root` and password `Test@123`.
