# ANGRBC Web Platform

## Overview
This is a Django-based web platform designed for the Association of Northern Ghana Regular Baptist Churches (ANGRBC) to manage their affiliated churches, programs, and events. The platform serves as both a central hub for ANGRBC and provides individual web presence for member churches.

## 🌟 Key Features
- **Multi-Church Management**: Central ANGRBC hub with linked individual church websites
- **Program Management**: Create and manage ANGRBC-wide programs
- **Custom Registration System**: Dynamic form builder for program registrations 
- **Content Management**: Each member church can manage its own content
- **User Management**: Role-based access control system

## 📁 Project Structure
```plaintext
church_organization/
│
├── manage.py                  # Django's command-line utility for administrative tasks
├── requirements.txt           # Project dependencies
├── .env                      # Environment variables (not in version control)
├── .gitignore                # Git ignore file
│
├── config/                   # Project configuration
│   ├── settings.py          # Project settings
│   ├── urls.py              # Main URL configuration
│   └── wsgi.py              # WSGI configuration for deployment
│
├── apps/                    # Application modules
│   ├── core/               # Core functionality shared across apps
│   ├── accounts/           # User authentication and management
│   ├── churches/           # Church management
│   ├── programs/           # Program and registration management
│   └── website/            # Content management
│
├── static/                 # Static files (CSS, JavaScript, Images)
├── media/                  # User-uploaded content
└── templates/              # HTML templates
```

## 🔍 Detailed Component Description

### 1. Apps Structure

#### Core App (`apps/core/`)
- Base models and utilities used across the platform
- Contains the main Organization model
- Shared functionality and helper functions

#### Accounts App (`apps/accounts/`)
- User authentication and authorization
- Profile management
- Role-based permissions:
  - Super Admin (Organization level)
  - Church Admin
  - Program Manager
  - Regular User

#### Churches App (`apps/churches/`)
- Church profile management
- Individual church websites
- Features for each church:
  - Events management
  - Service times
  - Ministry groups
  - Announcements
  - Photo gallery

#### Programs App (`apps/programs/`)
- Organization-wide program management
- Custom form builder for registrations
- Registration processing
- Attendance tracking
- Program schedules and details

#### Website App (`apps/website/`)
- Content management system
- Blog/News functionality
- Media management
- Contact forms
- Static page management

### 2. Key Models

```python
# Core Models Overview

class Organization:
    - name
    - description
    - logo
    - contact information
    - address

class Church:
    - name
    - organization (ForeignKey)
    - description
    - logo
    - website information
    - contact details

class Program:
    - title
    - organization (ForeignKey)
    - dates
    - location
    - registration details

class ProgramRegistrationForm:
    - program (OneToOneField)
    - form_fields (JSON)

class Registration:
    - program (ForeignKey)
    - user (ForeignKey)
    - form_data (JSON)
    - status
```

## 🚀 Getting Started

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Virtual environment tool (virtualenv or venv)

### Installation

1. Clone the repository
```bash
git clone https://github.com/your-username/church-organization.git
cd church-organization
```

2. Create and activate virtual environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

4. Set up environment variables
```bash
# Create .env file and add:
DEBUG=True
SECRET_KEY=your-secret-key
DATABASE_URL=your-database-url
```

5. Run migrations
```bash
python manage.py migrate
```

6. Create superuser
```bash
python manage.py createsuperuser
```

7. Run development server
```bash
python manage.py runserver
```

## 💻 Development Guidelines

### Code Style
- Follow PEP 8 guidelines
- Use meaningful variable and function names
- Add docstrings to all functions and classes
- Comment complex logic

### Database Migrations
- Create migrations after model changes:
  ```bash
  python manage.py makemigrations
  ```
- Apply migrations:
  ```bash
  python manage.py migrate
  ```

### Static Files
- Place all static files in their respective directories:
  - CSS files in `static/css/`
  - JavaScript files in `static/js/`
  - Images in `static/images/`
- Run `python manage.py collectstatic` before deployment

### Templates
- Base templates are in `templates/`
- Each app has its own template directory
- Extend base templates using Django template inheritance

## 🔐 Security Considerations
- Never commit `.env` file
- Keep `SECRET_KEY` secure
- Use environment variables for sensitive data
- Implement proper user authentication
- Use HTTPS in production
- Regularly update dependencies

## 📝 Testing
- Write tests for all new features
- Run tests using:
  ```bash
  python manage.py test
  ```

## 🚀 Deployment
- Set `DEBUG=False` in production
- Configure proper database settings
- Set up static files serving
- Configure HTTPS
- Set up proper email backend
- Configure cache if needed

## 🤝 Contributing
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details

## 📞 Support
For support, email support@churchorg.com or create an issue in the repository.

## 🔄 Version History
- v0.1.0 - Initial Release
  - Basic church management
  - Program registration system
  - User authentication

## 🙏 Acknowledgments
- Django Documentation
- Django REST Framework
- Bootstrap
- Other open source libraries used in this project