# Library Management System (LMS)

A comprehensive web-based Library Management System built with PHP and MySQL that combines the functionalities of an online bookstore and a digital library. The system allows users to browse, borrow, purchase, and read books while providing administrators with tools to manage inventory, users, transactions, and generate reports.

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Database Schema](#database-schema)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

### User Management
- User registration and authentication
- Role-based access control (Admin/User)
- Profile management
- Password reset functionality
- Account status tracking

### Book Management
- Add, edit, delete, and search books
- Support for physical and e-book formats
- ISBN, author, publication date, categorization
- Book of the month designation
- Cover images and file attachments
- Inventory tracking for physical books

### Borrowing/Lending System
- Loan request submission and approval
- Configurable loan durations
- Due date tracking and automatic late fee calculation
- Loan renewal functionality
- Reading completion tracking
- Return processing

### Purchase System
- Shopping cart functionality
- Secure checkout process
- Order management (pending, completed, cancelled)
- Digital delivery for e-books
- Physical order tracking

### Payment Processing
- Multiple payment types (borrow fees, purchases, wallet top-ups, penalties)
- Payment status tracking
- Transaction ID generation
- Wallet integration for payments
- Payment method extensibility

### Wallet System
- Real-time balance tracking
- Fund wallet via payment gateway
- Deduct wallet balance for purchases/fees
- Transaction history
- Minimum balance configuration

### Social & Community Features
- Favorite books/bookmarking
- Book ratings and reviews (1-5 scale with comments)
- User groups/book clubs creation and management
- Group shared resources
- Basic discussion forums
- Activity sharing options

### Administrative Features
- Dashboard with key metrics
- Comprehensive reporting (sales, usage, financial, inventory)
- Report export (PDF/Excel)
- Database backup and restore
- Activity logging and audit trails
- Complaint/support ticket management
- System settings configuration
- Promotional slider management
- News ticker for announcements

### Notification System
- Real-time in-app notifications
- Email notifications (configurable)
- Notification types: loan approvals, payments, due dates, late fees, etc.
- Read/unread status tracking
- Notification expiration

### Security Features
- CSRF protection
- Input validation and sanitization
- Password hashing (bcrypt)
- Secure session handling
- Role-based access control
- Protection against XSS and SQL injection
- Secure file upload handling
- Comprehensive audit logging

## Tech Stack

### Backend
- **Language**: PHP 7.x+
- **Framework**: Custom PHP MVC (Model-View-Controller)
- **Database**: MySQL 8.0+
- **Web Server**: Apache/Nginx

### Frontend
- **Markup**: HTML5
- **Styling**: CSS3
- **Interactivity**: JavaScript (Vanilla)
- **Responsive Design**: Mobile-friendly layouts

### Development Tools
- **Version Control**: Git
- **Database Management**: phpMyAdmin or MySQL CLI
- **Testing**: Manual testing framework (can be extended with PHPUnit)

## Database Schema

The system consists of 20+ interconnected tables:

### Core Tables
- `users`: Admin and regular user accounts
- `books`: Book inventory with metadata
- `categories`: Book classification system
- `borrow_requests`: Loan and purchase transactions
- `payments`: Financial transaction records
- `wallets`: User account balances
- `favorite_books`: User bookmarked items
- `complaints`: Support ticket system
- `users_groups`: Book clubs/reading groups
- `notifications`: System alerts and messages
- `activity_logs`: Audit trail of system actions
- `settings`: System configuration parameters

### Additional Tables
- `book_ratings`: User ratings and reviews
- `group_members`: Group membership
- `join_requests`: Group join requests
- `messages`: System messages
- `news_ticker`: Announcements
- `slider_images`: Homepage promotions
- `wallets`: Financial wallets
- `user_categories`: User category preferences

See the `test.sql` file for the complete database schema with sample data.

## Installation

### Prerequisites
- Web server (Apache/Nginx) with PHP 7.x+ support
- MySQL 8.0+ database server
- Composer (optional, for dependency management)
- Git (for version control)

### Step-by-Step Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-repo/library-management-system.git
   cd library-management-system
   ```

2. **Set Up the Database**
   ```bash
   # Log into MySQL
   mysql -u root -p
   
   # Create database
   CREATE DATABASE library_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   
   # Create user and grant privileges
   CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'secure_password_123';
   GRANT ALL PRIVILEGES ON library_db.* TO 'app_user'@'localhost';
   FLUSH PRIVILEGES;
   EXIT;
   ```
   
   # Import the database schema
   mysql -u app_user -p library_db < test.sql
   ```

3. **Configure the Application**
   - Copy the configuration template (if applicable)
   - Edit `/includes/config.php` with your database credentials:
     ```php
     $host = "your_host";
     $user = "your_username";
     $password = "your_password";
     $dbname = "library_db";
     ```
   - Adjust `BASE_URL` in `/includes/config.php` to match your domain:
     ```php
     define('BASE_URL', 'http://your-domain.com/lms/');
     ```

4. **Set File Permissions**
   ```bash
   # Ensure the web server can write to necessary directories
   chmod -R 755 assets/
   chmod -R 755 uploads/  # if exists
   chmod -R 755 backups/
   ```

5. **Test the Installation**
   - Access the system via your web browser: `http://your-domain.com/lms/`
   - Default admin credentials (from test.sql):
     - Email: admin@gmail.com
     - Password: (hashed in DB, reset via password reset or direct DB update)
   - Regular user accounts are also available in the test data.

## Configuration

### Basic Configuration (`/includes/config.php`)
- Database connection settings
- Base URL for the application
- Session initialization and CSRF token generation

### Email Settings
To enable email notifications, configure your SMTP settings in the appropriate notification sending files (typically in `/includes/` or notification-related PHP files).

### Payment Gateway Integration
Payment processing is currently simulated. To integrate with a real payment gateway:
1. Locate payment processing files (e.g., `payment.php`, `process.php`)
2. Replace the simulated payment logic with your gateway's API calls
3. Ensure proper security measures (PCI compliance, data encryption)

### File Upload Settings
Adjust upload limits in `php.ini` if needed:
```ini
upload_max_filesize = 16M
post_max_size = 16M
max_execution_time = 300
```

## Usage

### For Administrators
1. Access the admin dashboard via `/admin/`
2. Manage books: Add new books, update inventory, set prices/discounts
3. Manage users: Create accounts, assign roles, monitor activity
4. Generate reports: Sales, usage, financial reports
5. Handle complaints: Review and resolve user support tickets
6. Configure system: Adjust settings, manage slider images, news ticker
7. Backup system: Use backup/restore functionality in admin panel

### For Regular Users
1. Register an account or log in
2. Browse the book catalog using search and filters
3. Add books to favorites for later reference
4. Request to borrow physical books (subject to availability and approval)
5. Purchase books directly through the shopping cart
6. Manage your wallet: Add funds, view transaction history
7. Participate in reading groups: Create or join groups, share resources
8. Rate and review books you've read
9. Submit complaints or suggestions through the support system
10. Monitor notifications for important updates

### Common Tasks
- **Borrowing a Book**: Search for book → Click "Borrow" → Wait for admin approval → Receive notification → Download/access book → Return when due
- **Purchasing a Book**: Search for book → Click "Buy" → Add to cart → Checkout → Payment confirmation → Access purchased book
- **Managing Wallet**: Go to Wallet section → Add funds → Use wallet for purchases/fees → View transaction history
- **Joining a Group**: Browse groups → Click "Join" → Wait for approval → Participate in discussions → Access shared resources

## API Endpoints

While the system is primarily a traditional web application, several endpoints are used for AJAX functionality:

### Authentication
- `POST /login.php` - User login
- `GET /logout.php` - User logout
- `POST /register.php` - User registration

### Book Operations
- `GET /fetch_books.php` - Fetch books with filters
- `GET /book_of_the_month.php` - Get featured book
- `GET /recommended_books.php` - Get recommended books
- `POST /add_to_cart.php` - Add item to cart
- `GET /cart.php` - View shopping cart

### User Operations
- `GET /profile.php` - View/edit profile
- `POST /update_profile.php` - Update profile information
- `GET /wallet.php` - View wallet balance
- `POST /add_funds.php` - Add funds to wallet

### Borrowing Operations
- `GET /get_favorites.php` - Get favorite books
- `POST /toggle_favorite.php` - Toggle favorite status
- `GET /get_reviews.php` - Get book reviews
- `POST /complaint.php` - Submit complaint

### Admin Operations
- Located in `/admin/` directory:
  - `manage_books.php` - Book management
  - `manage_users.php` - User management
  - `manage_reports.php` - Report generation
  - `backup_restore.php` - Database backup/restore

## Contributing

We welcome contributions to improve the Library Management System! Please follow these guidelines:

### Reporting Issues
1. Check if the issue has already been reported
2. Create a new issue with:
   - Clear title and description
   - Steps to reproduce (if applicable)
   - Expected vs actual behavior
   - Screenshots (if helpful)
   - Environment details (PHP version, MySQL version, browser)

### Submitting Pull Requests
1. Fork the repository
2. Create a new branch for your feature/bugfix
3. Make your changes following the existing code style
4. Add/update tests if applicable
5. Ensure your code follows PSR-12 coding standards
6. Submit a pull request with a clear description of changes

### Code Style
- Follow PSR-12 for PHP code
- Use meaningful variable and function names
- Comment complex logic
- Keep functions focused and reasonably sized
- Use prepared statements for database queries
- Validate and sanitize all user inputs

### Development Setup
For contributors wanting to set up a development environment:
1. Use a local development server (XAMPP, WAMP, MAMP, or Docker)
2. Enable error reporting during development
3. Use browser developer tools for debugging frontend issues
4. Consider using IDE with PHP support (VSCode, PHPStorm, etc.)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or support regarding this Library Management System:

- **GitHub Issues**: https://github.com/your-repo/library-management-system/issues
- **Email**: your-email@example.com
- **Documentation**: Refer to the [Product Requirements Document](PRD.md) for detailed feature specifications

## Acknowledgments

- Thanks to all contributors who have helped improve this system
- Special thanks to the open-source community for various libraries and tools used
- Inspired by the need for integrated library and bookstore management solutions

---

**Note**: This README provides an overview of the system. For detailed technical specifications, refer to the [Product Requirements Document](PRD.md) and the database schema in `test.sql`.

*Last updated: $(date +%Y-%m-%d)*