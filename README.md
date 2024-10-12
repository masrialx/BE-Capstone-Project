# Blogging Platform API

This is a blogging platform API built using **Django** and **Django REST Framework**. The API allows users to manage blog posts with full CRUD (Create, Read, Update, Delete) capabilities, filter posts by categories and authors, search blog posts by title and content, and manage user authentication. This API is designed to simulate the backend of a real-world blogging platform.

## Features

- **Blog Post Management (CRUD)**:
  - Create, read, update, and delete blog posts.
  - Each blog post contains: Title, Content, Author, Category, Published Date, Tags (optional), and Created Date.
  - Users can create and manage their own posts.
  
- **User Management (CRUD)**:
  - Create, read, update, and delete users.
  - Unique username, email, and password are required for each user.
  - Only authenticated users can create, update, or delete their own posts.

- **View Posts by Category or Author**:
  - Filter posts by category (e.g., Technology, Health, Lifestyle).
  - Filter posts by author to view all posts from a specific user.
  
- **Search and Filter Blog Posts**:
  - Search posts by title, content, tags, or author.
  - Additional filtering by category and published date.
  
- **Pagination and Sorting**:
  - Pagination for blog post listings to handle large datasets.
  - Sorting options, including sorting by Published Date or Category.

- **User Authentication**:
  - Token-based authentication using Django’s built-in authentication system.
  - Optionally, JWT authentication for enhanced security.

## Technologies Used

- **Backend Framework**: Django, Django REST Framework
- **Database**: PostgreSQL (or any supported by Django ORM)
- **Authentication**: Django's built-in authentication, JWT (optional)
- **Web Server**: Gunicorn
- **Deployment**: Render

## Prerequisites

- Python 3.x
- Pip (Python package manager)
- Git
- PostgreSQL (optional if using SQLite for development)
  
## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/blog-platform-api.git
   cd blog-platform-api
   ```

2. **Create a virtual environment**:

   ```bash
   python -m venv venv
   source venv/bin/activate   # For Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**:
   Create a `.env` file in the root of your project and add the following:

   ```env
   SECRET_KEY=your_secret_key
   DEBUG=True
   DATABASE_URL=your_database_url
   ```

   - If you’re using PostgreSQL, replace `your_database_url` with your actual database URL.
   - For SQLite (default in Django), you don’t need the `DATABASE_URL` variable.

5. **Run database migrations**:

   ```bash
   python manage.py migrate
   ```

6. **Create a superuser** (for admin access):

   ```bash
   python manage.py createsuperuser
   ```

7. **Run the development server**:

   ```bash
   python manage.py runserver
   ```

   Now, your API is running at `http://127.0.0.1:8000/`.

## Endpoints

Here are the main API endpoints:

### Authentication

- **Login**: `/api/login/`
- **Logout**: `/api/logout/`
- **Register**: `/api/register/`

### Blog Post Management

- **List All Posts**: `/api/posts/`
- **Create Post**: `/api/posts/` (Authenticated)
- **Retrieve Post**: `/api/posts/{id}/`
- **Update Post**: `/api/posts/{id}/` (Authenticated)
- **Delete Post**: `/api/posts/{id}/` (Authenticated)

### Category and Author Filtering

- **Filter by Category**: `/api/posts/?category=Technology`
- **Filter by Author**: `/api/posts/?author=username`

### Search Posts

- **Search by Title**: `/api/posts/?search=title`
- **Search by Content**: `/api/posts/?search=content`

### User Management

- **Create User**: `/api/users/`
- **Retrieve User**: `/api/users/{id}/`
- **Update User**: `/api/users/{id}/` (Authenticated)
- **Delete User**: `/api/users/{id}/` (Authenticated)

## Deployment

This project can be easily deployed to **Render**. Follow these steps:

1. **Sign up for a Render account**.
2. **Push your code to GitHub**.
3. **Create a new Web Service** on Render.
4. Configure the following:
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn blog_platform.wsgi`
5. **Set environment variables**:
   - `SECRET_KEY`
   - `DEBUG=False`
   - `DATABASE_URL` (for PostgreSQL if needed)

Render will automatically build and deploy your application. The API will be accessible at the URL provided by Render.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
