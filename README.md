# Project Description: Django REST Framework Video Sharing Platform  

This project is a Django REST Framework (DRF) application designed to serve as the backend for a video-sharing platform. The platform incorporates features for user authentication, video uploads, subscriptions, and user-generated content such as tweets.  

---

## **Features**  

### 1. **User Management**  
- **Custom User Model**:  
  - A custom user model (`User`) extends the default `AbstractUser` to include fields such as `avatar`, `coverImage`, and `refreshToken`.  
  - Authentication is email-based with `USERNAME_FIELD` set to `email`.  
- **User Manager**:  
  - Implements `create_user` and `create_superuser` methods for user registration and admin creation.  

### 2. **Video Management**  
- **Video Uploads**:  
  - Users can upload videos with associated thumbnails using Cloudinary for media storage.  
- **Metadata**:  
  - Includes fields like `title`, `description`, and `duration` for each video.  
- **Owner Association**:  
  - Videos are linked to their respective owners through a `ForeignKey`.  

### 3. **Subscriptions**  
- **Follow Channels**:  
  - Users can subscribe to other users (channels).  
- **Relational Models**:  
  - A subscription links a `subscriber` to a `channel`.  

### 4. **Tweets**  
- **User Posts**:  
  - Users can post text-based content (`Tweet`) linked to their accounts.  

### 5. **Cloud Storage**  
- **Cloudinary Integration**:  
  - Used for storing user avatars, video files, and thumbnails.  

---

## **Folder Structure**  

### Root Directory  
- `.env`: Stores environment variables like API keys and sensitive information.  
- `.gitignore`: Lists files and folders to be excluded from version control.  
- `manage.py`: Django’s management script.  
- `requirements.txt`: Contains the list of dependencies for the project.  

### Backend Application  
- `backend/`:  
  - `settings.py`: Configuration file for the project, including middleware, database settings, and third-party apps.  
  - `urls.py`: Routes HTTP requests to appropriate views.  

### Core Application  
- `core/`: Contains primary models such as `User`, `Video`, `Tweet`, and `Subscription`.  

### Feature-Specific Applications  
- `subscriptions/`:  
  - Handles subscription-related logic, including serializers, views, and URLs.  
- `tweets/`:  
  - Manages tweet-related features such as creating, viewing, and listing tweets.  
- `videos/`:  
  - Responsible for video upload, retrieval, and management.  

### Utilities  
- `utils/`: Contains helper functions like `CloudinaryUtils.py` for Cloudinary-specific tasks.  

---

## **Database Models**  

### 1. **User**  
- Inherits `AbstractUser`.  
- Custom fields:  
  - `avatar`: User’s profile image.  
  - `coverImage`: Optional cover photo.  
  - `refreshToken`: Used for authentication refresh.  
- Methods:  
  - `__str__`: Returns the user's email.  

### 2. **Video**  
- Fields:  
  - `videoFile`: Cloudinary field for video storage.  
  - `thumbnailFile`: Cloudinary field for thumbnail storage.  
  - Metadata: `title`, `description`, `duration`.  
- Relations:  
  - Linked to the `User` model as the owner.  

### 3. **Tweet**  
- Fields:  
  - `content`: Text content of the tweet.  
  - `owner`: Links to the user who created the tweet.  

### 4. **Subscription**  
- Fields:  
  - `subscriber`: User who subscribes to another user.  
  - `channel`: User being subscribed to.  

---

## **Technologies Used**  

- **Framework**: Django REST Framework (DRF).  
- **Database**: SQLite (development) / PostgreSQL (production).  
- **Cloud Storage**: Cloudinary for media storage.  
- **Authentication**: Custom user model with email-based login.  

---

## **Endpoints (Examples)**  

### User  
- **Register**: `/api/user/register/`  
- **Login**: `/api/user/login/`  

### Videos  
- **Upload Video**: `/api/videos/upload/`  
- **List Videos**: `/api/videos/`  

### Subscriptions  
- **Subscribe**: `/api/subscriptions/subscribe/`  
- **List Subscriptions**: `/api/subscriptions/`  

### Tweets  
- **Post Tweet**: `/api/tweets/create/`  
- **List Tweets**: `/api/tweets/`  

---

## **Future Enhancements**  

1. **Comments and Likes**: Add functionality to comment on and like videos and tweets.  
2. **Recommendations**: Implement video recommendations using machine learning.  
3. **Notifications**: Notify users of new uploads or subscriptions.  
4. **Streaming**: Optimize video streaming for performance and quality.  

--- 

## **Conclusion**  

This Django REST Framework project lays the foundation for a robust and scalable video-sharing platform. With features like user authentication, video uploads, and subscriptions, it provides essential functionalities for content creators and viewers alike. Further enhancements can transform it into a fully-featured platform.
