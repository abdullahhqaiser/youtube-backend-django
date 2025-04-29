# Social Media Platform API

This project is a Django REST Framework application that provides backend API services for a social media platform with video sharing, tweets, and subscription features.

## Features

- **User Management**
  - Registration with email verification
  - Login/Logout with token authentication
  - Profile management with avatar and cover image

- **Video Sharing**
  - Upload videos to Cloudinary
  - Automatic thumbnail generation
  - CRUD operations for videos
  - Video duration tracking

- **Tweet System**
  - Post text-based tweets
  - View your tweet history
  - Delete your tweets

- **Subscription System**
  - Subscribe to other users' channels
  - Track subscribers and subscriptions

## Technology Stack

- **Django & Django REST Framework** - Backend framework
- **Cloudinary** - Media storage and management
- **dj-rest-auth** - User authentication
- **PostgreSQL** - Database (assumed)

## Database Schema

![ChatGPT Image Apr 29, 2025, 01_53_27 PM](https://github.com/user-attachments/assets/ee2df0e1-d7ca-4e4f-94ae-820e7b039881)


## Project Structure

The project is organized into several Django apps:

- **core** - Contains the main models (User, Video, Tweet, Subscription)
- **user** - Handles user authentication and profile management
- **videos** - Manages video uploading, updating, and deletion
- **tweets** - Handles tweet creation and management
- **subscriptions** - Manages channel subscriptions

## Installation

1. Clone the repository
```bash
git clone [repository-url]
cd [project-folder]
```

2. Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

4. Set up environment variables
```
# Create a .env file with the following variables
SECRET_KEY=your_secret_key
DEBUG=True
DATABASE_URL=your_database_url
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
EMAIL_HOST=your_email_host
EMAIL_PORT=your_email_port
EMAIL_HOST_USER=your_email_user
EMAIL_HOST_PASSWORD=your_email_password
EMAIL_CONFIRM_REDIRECT_BASE_URL=your_frontend_email_confirmation_url
PASSWORD_RESET_CONFIRM_REDIRECT_BASE_URL=your_frontend_password_reset_url
```

5. Run migrations
```bash
python manage.py migrate
```

6. Create a superuser
```bash
python manage.py createsuperuser
```

7. Run the server
```bash
python manage.py runserver
```

## API Endpoints

### Authentication

- `POST /user/register/` - Register a new user
- `POST /user/register/verify-email/` - Verify email
- `POST /user/register/resend-email/` - Resend verification email
- `POST /user/auth/login/` - Login
- `POST /user/auth/logout/` - Logout
- `GET /user/auth/details/` - Get user details
- `POST /user/password/reset/` - Request password reset
- `POST /user/password/reset/confirm/` - Confirm password reset

### Videos

- `GET /videos/` - List all videos (for logged-in user)
- `POST /videos/` - Upload a new video
- `GET /videos/{id}/` - Get video details
- `PUT /videos/{id}/` - Update video
- `DELETE /videos/{id}/` - Delete video

### Tweets

- `GET /tweets/` - List all tweets (for logged-in user)
- `POST /tweets/` - Create a new tweet
- `GET /tweets/{id}/` - Get tweet details
- `PUT /tweets/{id}/` - Update tweet
- `DELETE /tweets/{id}/` - Delete tweet

### Subscriptions

- `POST /subscribe/` - Subscribe to a channel

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request
