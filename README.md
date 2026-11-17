# CS208 Full Stack Final Project - TODO Application

- **Name:** Jared Hartzell
- **GitHub:** [https://github.com/jaredhartzell]
- **Term:** Fall 2026

## Project Description

This is my full-stack application for CS208, built using Node.js, Express, Pug, and MariaDB (MySQL). I developed a task management application that allows users to create, view, edit, complete, and delete tasks through a web interface.
The application uses Express for the backend, Pug for dynamically generating HTML, and MariaDB for storing task information. I also implemented a custom dark-themed interface using CSS.

## Application Features

- **Create Tasks:** Users can add new tasks to the database.
- **View Tasks:** All existing tasks are displayed on the main page.
- **Edit Tasks:** Users can modify task descriptions and save their changes.
- **Complete Tasks:** Users can mark tasks as completed or change them back to not completed.
- **Delete Tasks:** Users can permanently remove tasks.
- **Input Validation:** Blank or whitespace-only tasks are rejected by the backend.
- **Dark Theme:** The application features a custom dark-themed interface with styled buttons, input fields, and visual indicators for completed tasks.

Task descriptions and completion statuses are stored in the MariaDB database, allowing changes to persist after refreshing the page.

## Install the Database

The application requires MariaDB to be installed and running.

To install the database, run the `install_db.sh` script from the project root directory:

```bash
./setup_scripts/install_db.sh
```

This script is designed for an Ubuntu Linux environment, such as GitHub Codespaces or WSL2.

If the script fails because the MariaDB security configuration command is unavailable, install MariaDB manually:

```bash
sudo apt update
sudo apt install mariadb-server mariadb-client -y
sudo service mariadb start
```

If necessary, run the MariaDB security configuration utility:

```bash
sudo mariadb-secure-installation
```

Configure the MariaDB root account with a password and complete the security configuration prompts.

The database installation only needs to be performed once per environment.

## Create the Database Tables

After MariaDB has been installed and configured, create the database and initial tables using the provided SQL script:

```bash
sudo mysql -u root -p < ./setup_scripts/create_demo_table.sql
```

Enter the MariaDB root password when prompted.

The application uses a `todos` table containing the task ID, task description, and completion status.

## Install Dependencies

Install the Node.js dependencies from the project root directory:

```bash
npm install
```

Node.js and npm must already be installed. For WSL2, I recommend installing Node.js using NVM.

## Run the Application

Start the Express application using:

```bash
npm start
```

The server runs on port 3000.

MariaDB must be running before starting the application.

If necessary, start MariaDB using:

```bash
sudo service mariadb start
```

## Access the Application

### GitHub Codespaces

If running the project in GitHub Codespaces, forward port 3000 and open the forwarded port in a web browser.

### Local Development (WSL2 / Ubuntu)

If running the project locally using WSL2 or Ubuntu, open a web browser and navigate to:

[http://localhost:3000]

## Using the Application

1. Enter a task description in the **Add a New Task** field and click **Add Task**.
2. Existing tasks will appear in the **My Tasks** section.
3. To edit a task, modify its description and click **Save**.
4. To complete a task, select its **Completed** checkbox and click **Save**.
5. Completed tasks are visually distinguished with green styling and a strikethrough description.
6. To mark a task as not completed, uncheck **Completed** and click **Save**.
7. To remove a task, click **Delete**.

The application does not allow blank task descriptions to be created or saved.

## Project Structure

```text
CS208-full-stack/
├── app.js
├── routes/
│   └── index.js
├── views/
│   ├── index.pug
│   ├── layout.pug
│   └── error.pug
├── public/
│   └── stylesheets/
│       └── style.css
├── setup_scripts/
│   ├── install_db.sh
│   └── create_demo_table.sql
├── package.json
└── README.md
```

The `routes/index.js` file handles database operations, `views/index.pug` generates the main task management interface, and `public/stylesheets/style.css` contains the custom dark-theme styling.