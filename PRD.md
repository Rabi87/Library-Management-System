# Product Requirements Document (PRD)
## Library Management System (LMS)

### 1. Executive Summary
The Library Management System (LMS) is a comprehensive web application built with PHP and MySQL that combines the functionalities of an online bookstore and a digital library. The system allows users to browse, borrow, purchase, and read books while providing administrators with tools to manage inventory, users, transactions, and generate reports.

### 2. Product Overview
#### 2.1 Purpose
To provide a unified platform for managing library operations, book sales, and user interactions in an educational or community setting.

#### 2.2 Target Users
- **Administrators**: Manage system configuration, book inventory, user accounts, and generate reports
- **Regular Users**: Browse books, borrow/purchase materials, manage their accounts, and participate in reading groups
- **Guest Users**: Browse available books and public information (limited functionality)

#### 2.3 Key Features
- User authentication and authorization (admin/user roles)
- Book catalog management (physical and e-books)
- Category-based organization
- Borrowing/loan system with due dates and penalties
- Purchase system for buying books
- Wallet system for storing user funds
- Payment processing integration
- Book ratings and reviews
- Favorite books/bookmarking
- User groups/book clubs functionality
- Complaint/support ticket system
- Notification system
- Activity logging and audit trails
- Reports generation (sales, usage, user activity)
- Homepage slider for promotions
- News ticker for announcements
- Responsive web interface

### 3. System Architecture
#### 3.1 Technology Stack
- **Backend**: PHP 7.x+
- **Database**: MySQL 8.0+
- **Frontend**: HTML5, CSS3, JavaScript
- **Session Management**: PHP sessions with CSRF protection
- **Web Server**: Apache/Nginx

#### 3.2 Database Schema Overview
The system consists of 20+ interconnected tables including:
- **Users**: Admin and regular user accounts
- **Books**: Book inventory with metadata (title, author, ISBN, pricing, etc.)
- **Categories**: Book classification system
- **Borrow_Requests**: Loan transactions and purchase records
- **Payments**: Financial transaction records
- **Wallets**: User account balances
- **Favorite_Books**: User bookmarked items
- **Complaints**: Support ticket system
- **Users_Groups**: Book clubs/reading groups
- **Notifications**: System alerts and messages
- **Activity_Logs**: Audit trail of system actions
- **Settings**: System configuration parameters

### 4. Functional Requirements

#### 4.1 User Management
- **Registration**: New users can create accounts with email verification
- **Authentication**: Secure login/logout with password hashing
- **Authorization**: Role-based access control (admin vs user)
- **Profile Management**: Users can update personal information
- **Password Reset**: Secure password recovery mechanism
- **Account Status**: Activation/deactivation capabilities
- **Last Activity Tracking**: Monitoring user engagement

#### 4.2 Book Management
- **Catalog Operations**: Add, edit, delete, and search books
- **Book Attributes**: 
  - Title, author, ISBN, publication date
  - Physical vs e-book format
  - Material type (book, magazine, newspaper)
  - Quantity available (for physical books)
  - Pricing and discount management
  - Book of the month designation
  - Cover images and file attachments
  - Description and evaluation/rating
- **Inventory Control**: Track available quantities for physical books
- **Categorization**: Assign books to one or more categories

#### 4.3 Borrowing/Lending System
- **Loan Requests**: Users can request to borrow physical books
- **Approval Workflow**: Admin approval/rejection of loan requests
- **Loan Terms**: Configurable loan duration (default 14 days)
- **Due Dates**: Automatic calculation based on loan duration
- **Renewals**: Option to extend loan period (if not reserved by others)
- **Returns**: Marking books as returned when completed
- **Late Fees**: Automatic penalty calculation for overdue items
- **Reading Completion Tracking**: Option to mark when reading is finished

#### 4.4 Purchase System
- **Book Purchases**: Users can buy books (physical or digital)
- **Shopping Cart**: Temporary storage for selected items
- **Checkout Process**: Payment collection and order confirmation
- **Order Management**: Tracking order status (pending, completed, cancelled)
- **Digital Delivery**: Providing access to purchased e-books
- **Physical Shipping**: Tracking for physical book shipments (if applicable)

#### 4.5 Payment Processing
- **Multiple Payment Types**: 
  - Borrow fees (loan processing)
  - Purchase payments (book sales)
  - Wallet top-ups (adding funds)
  - Penalty payments (late fees)
  - Renewal fees (extending loan periods)
- **Payment Status Tracking**: Pending, completed, failed, refunded
- **Transaction IDs**: Unique identifiers for payment reconciliation
- **Payment Methods**: Support for various payment gateways (configurable)
- **Wallet Integration**: Ability to pay from user wallet balance

#### 4.6 Wallet System
- **Balance Tracking**: Real-time wallet balance for each user
- **Funding Options**: Adding money to wallet via payment gateway
- **Usage**: Deducting wallet balance for purchases/fees
- **Transaction History**: Record of all wallet transactions
- **Minimum Balance**: Configurable minimum balance requirements

#### 4.7 Social & Community Features
- **Favorite Books**: Users can bookmark books for later reference
- **Ratings & Reviews**: Users can rate books (1-5 scale) and leave comments
- **Reading Groups**: Users can create/join book clubs or reading groups
- **Group Management**: Group admins can manage membership and shared content
- **Discussion Forums**: Basic forum functionality for group discussions
- **Activity Sharing**: Optional sharing of reading activities

#### 4.8 Administrative Features
- **Dashboard**: Overview of key metrics and system status
- **Reports Generation**: 
  - Sales reports (revenue, popular books)
  - Usage reports (borrow statistics, active users)
  - User activity reports
  - Financial reports
  - Inventory reports
- **Export Functionality**: Export reports to PDF/Excel formats
- **Backup & Restore**: Database backup and recovery capabilities
- **Log Management**: View and manage system activity logs
- **Complaint Management**: Tracking and resolving user complaints
- **Settings Management**: Configuring system parameters (prices, fees, etc.)
- **Slider Management**: Managing homepage promotional banners
- **News Ticker**: Managing announcements and updates

#### 4.9 Notification System
- **Real-time Alerts**: Instant notifications for important events
- **Email Notifications**: Optional email alerts for key actions
- **In-app Notifications**: Bell icon with unread count
- **Notification Types**:
  - Loan approval/rejection
  - Payment confirmations
  - Due date reminders
  - Late fee warnings
  - Book availability notifications
  - Group invitations and updates
  - Administrative announcements
- **Read Status**: Tracking which notifications have been viewed
- **Expiration**: Automatic cleanup of old notifications

#### 4.10 Security Features
- **CSRF Protection**: Cross-site request forgery tokens
- **Input Validation**: Server-side validation of all user inputs
- **Password Hashing**: Strong password encryption (bcrypt)
- **Session Security**: Secure session handling with timeout
- **Access Control**: Role-based permissions for all operations
- **Data Sanitization**: Prevention of XSS and SQL injection attacks
- **File Upload Validation**: Secure handling of uploaded files
- **Audit Logging**: Comprehensive logging of all system actions

### 5. Non-Functional Requirements

#### 5.1 Performance
- Page load time < 3 seconds for 95% of pages
- Support for concurrent users (minimum 50 simultaneous users)
- Database query optimization for common operations
- Caching strategies for frequently accessed data

#### 5.2 Scalability
- Horizontal scaling capability for web servers
- Database indexing for optimal query performance
- Modular architecture for easy feature expansion
- Efficient resource utilization

#### 5.3 Reliability
- 99.% uptime SLA target
- Automated backup schedules (daily incremental, weekly full)
- Error handling and graceful degradation
- Health monitoring and alerting systems

#### 5.4 Usability
- Intuitive user interface with consistent design
- Responsive design for mobile and desktop access
- Clear navigation and information architecture
- Accessibility compliance (WCAG 2.1 AA)
- Multi-language support (Arabic/English based on current implementation)
- Contextual help and tooltips

#### 5.5 Security
- OWASP Top 10 protection
- Regular security audits and penetration testing
- Data encryption at rest and in transit
- GDPR/compliance readiness for user data protection
- Role-based access control with principle of least privilege

#### 5.6 Maintainability
- Well-documented codebase with clear comments
- Modular architecture following MVC principles
- Consistent coding standards and practices
- Automated testing framework (unit/integration tests)
- Clear deployment procedures and documentation

### 6. User Interface Requirements

#### 6.1 User Interface (Public)
- **Homepage**: Featured books, slider promotions, news ticker
- **Book Catalog**: Grid/list view with filtering and sorting
- **Book Detail Page**: Comprehensive book information, ratings, actions (borrow/buy/favorite)
- **Search Functionality**: Full-text search with filters (category, author, material type)
- **User Login/Registration**: Secure authentication forms
- **Shopping Cart**: Review and modify selected items before checkout
- **Checkout Process**: Multi-step payment and confirmation flow

#### 6.2 User Interface (Authenticated Users)
- **Dashboard**: Personal overview (wallet balance, active loans, favorites, etc.)
- **Profile Management**: Edit personal information and preferences
- **Loan History**: View past and current borrowing activities
- **Purchase History**: Track all purchased items
- **Wallet Management**: View balance and transaction history
- **Favorite Books**: Manage bookmarked items
- **Groups**: Create/join and manage reading groups
- **Complaints**: Submit and track support tickets
- **Notifications**: View and manage system notifications

#### 6.3 Administrator Interface
- **Admin Dashboard**: System overview with key metrics
- **Book Management**: Complete CRUD operations for book inventory
- **User Management**: Create/edit/delete user accounts, manage roles
- **Reports Section**: Generate and export various reports
- **Payment Management**: View and reconcile transactions
- **Group Administration**: Oversee all user groups
- **Complaint Management**: Track and resolve user issues
- **Settings Configuration**: Adjust system parameters
- **Log Viewer**: Monitor system activity and security events
- **Backup Tools**: Database backup and restoration interface

### 7. Dependencies
- **External Services**:
  - Payment gateway integration (to be configured)
  - Email service for notifications (SMTP/SendGrid/etc.)
  - File storage for book uploads and cover images
  - Optional: SMS gateway for notifications
- **Internal Dependencies**:
  - Properly configured LAMP/LNMP stack
  - Sufficient disk space for book storage
  - Adequate memory for concurrent user handling
  - Regular database maintenance schedule

### 8. Assumptions and Constraints
- **Assumptions**:
  - Users have basic computer literacy
  - Institution has IT support for server maintenance
  - Budget available for payment gateway fees
  - Copyright compliance for digital book distribution
  - Regular content updates by librarians/administrators

- **Constraints**:
  - Must comply with local data protection regulations
  - Physical book lending limited by actual inventory
  - Digital rights management for e-books (if applicable)
  - Budget limitations for premium features
  - Technical expertise available for customization

### 9. Success Metrics
- **User Adoption**: Number of registered active users
- **Engagement**: Average books borrowed/purchased per user per month
- **Satisfaction**: User survey ratings and feedback
- **Operational Efficiency**: Reduction in manual processing time
- **Financial**: Revenue growth from book sales and services
- **Retention**: Month-over-month user retention rate
- **System Performance**: Page load times and uptime percentages
- **Support Metrics**: Number and resolution time of complaints

### 10. Implementation Roadmap
#### Phase 1: Core Foundation (Weeks 1-4)
- User authentication and authorization system
- Basic book catalog (CRUD operations)
- Simple borrowing system
- Basic payment integration
- Wallet system implementation

#### Phase 2: Enhanced Features (Weeks 5-8)
- Advanced search and filtering
- Ratings and reviews system
- Favorite books functionality
- Basic reporting capabilities
- Notification system

#### Phase 3: Community & Social Features (Weeks 9-12)
- User groups/book clubs
- Complaint/support system
- Advanced reporting and export
- Administrative dashboard enhancements
- Backup and restore functionality

#### Phase 4: Optimization & Launch (Weeks 13-16)
- Performance optimization
- Security hardening
- Usability testing and refinement
- Documentation and training materials
- Production deployment and monitoring

### 11. Appendix
#### 11.1 Glossary of Terms
- **LMS**: Library Management System
- **ISBN**: International Standard Book Number
- **CSRF**: Cross-Site Request Forgery
- **CRUD**: Create, Read, Update, Delete operations
- **SLA**: Service Level Agreement
- **WCAG**: Web Content Accessibility Guidelines
- **GDPR**: General Data Protection Regulation

#### 11.2 Related Documents
- Technical Specification Document
- Database Schema Documentation
- API Documentation (if applicable)
- User Manuals (Admin and User versions)
- Deployment and Operations Guide
- Test Plans and Test Cases

