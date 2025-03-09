# WordPress Docker Compose

A complete WordPress development environment using Docker Compose with MariaDB, WordPress, and phpMyAdmin.

## Components

- **WordPress**: Latest WordPress container
- **MariaDB**: MySQL database for WordPress
- **phpMyAdmin**: Web interface for database management

## Configuration

All major configuration options are centralized in the `.env` file:

### Database Settings
- `MYSQL_DATABASE`: WordPress database name
- `MYSQL_USER`: Database username
- `MYSQL_PASSWORD`: Database user password
- `MYSQL_ROOT_PASSWORD`: MySQL root password

### Port Configuration
- `DB_PORT`: MariaDB port (default: 3306)
- `PHPMYADMIN_PORT`: phpMyAdmin web interface port (default: 8081)
- `WORDPRESS_PORT`: WordPress site port (default: 8080)

### Resource Limits
- `DB_MEMORY_LIMIT`: Memory limit for the database container (default: 2048m)

### phpMyAdmin Settings
- `PMA_UPLOAD_LIMIT`: Maximum upload size for phpMyAdmin (default: 750M)
- `PMA_MAX_EXECUTION_TIME`: Maximum execution time for phpMyAdmin operations (default: 5000)

## PHP Configuration

The environment includes custom PHP configuration files:

### uploads.ini
Controls file upload settings for WordPress:
- File uploads enabled
- 500M memory limit
- 500M maximum upload file size
- 500M post maximum size
- 600 seconds maximum execution time

### php.ini
General PHP settings:
- 1024M memory limit
- ionCube loader configuration
- SOAP extension enabled
- 3000 maximum input variables

## Usage

### Starting the Environment

```bash
# Start all services
docker-compose up -d

# Stop all services
docker-compose down
```

### Accessing Services

- **WordPress**: http://localhost:8080
- **phpMyAdmin**: http://localhost:8081 (Server: database, Username: root, Password: from .env)

### Persistent Data

Data is persisted using Docker volumes:
- WordPress files: `./wordpress` directory
- Database data: Docker volume `db-data`

## Customization

- Modify the `.env` file to change configuration settings without editing docker-compose.yml
- Adjust PHP settings by editing `uploads.ini` or `php.ini`