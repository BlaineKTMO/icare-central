# iCare Central - AI-Powered Smart Wheelchair & Health Management System

## Table of Contents

1. [Overview](#overview)
2. [System Architecture](#system-architecture)
3. [Core Components](#core-components)
4. [Technical Stack](#technical-stack)
5. [Installation and Setup](#installation-and-setup)
6. [Development Guidelines](#development-guidelines)
7. [API Documentation](#api-documentation)
8. [Security and Compliance](#security-and-compliance)
9. [Deployment](#deployment)
10. [Contributing](#contributing)
11. [License](#license)

## Overview

iCare Central is a comprehensive system that combines AI-powered wheelchair navigation with health monitoring capabilities. The system uses eye tracking technology for wheelchair control and integrates various sensors for health monitoring, creating a unified platform for mobility assistance and health oversight.

### Key Features

#### Smart Wheelchair Capabilities

- AI-powered eye tracking for wheelchair navigation
- Real-time obstacle detection
- Stability monitoring
- Emergency stop protocols
- Battery monitoring

#### Health Management Features

- Integrated vital monitoring sensors
- Heart rate variability analysis using camera-based technology
- Real-time health alerts
- Activity monitoring
- Emergency response integration

## System Architecture

The system follows a modular architecture with components for both wheelchair control and health monitoring:

### High-Level Architecture

```
icare-central/
├── care-app/           # Main control and monitoring interface
├── cam_hrv/           # Camera-based health monitoring
├── eye_tracking/      # AI eye tracking for navigation
├── icare-imu/         # IMU integration for stability
├── icare-mongo/       # Health and usage data management
├── icare-nav/         # Navigation and safety systems
└── icare-patient/     # Health management system
```

## Core Components

### 1. Care App (care-app/)

The main interface that provides:

- Wheelchair control dashboard
- Health data visualization
- System configuration
- Sensor integration
- Health monitoring interface

### 2. Camera-based HRV Monitoring (cam_hrv/)

Health monitoring system that:

- Uses camera-based photoplethysmography (PPG)
- Processes video streams in real-time
- Calculates HRV metrics
- Provides continuous health monitoring
- Integrates with mobility controls

### 3. AI Eye Tracking System (eye_tracking/)

Navigation system that:

- Tracks eye movements using deep learning
- Translates gaze patterns into wheelchair commands
- Provides navigation control
- Includes safety features
- Adapts to user patterns

### 4. IMU Integration (icare-imu/)

Movement monitoring system that:

- Tracks wheelchair movement and position
- Monitors stability and tilt
- Detects potential falls
- Provides movement analytics
- Alerts caregivers of issues

### 5. Database Management (icare-mongo/)

Data management system that:

- Stores health and mobility data
- Manages system configurations
- Handles data backup and recovery
- Provides secure data access
- Ensures data integrity

### 6. Navigation System (icare-nav/)

Mobility system that:

- Processes AI eye tracking commands
- Implements obstacle detection
- Manages movement patterns
- Integrates safety systems
- Provides navigation assistance

### 7. Health Management System (icare-patient/)

Health platform that:

- Manages user health profiles
- Tracks medical history
- Processes health monitoring data
- Manages emergency contacts
- Generates health reports

## User Interfaces

### Caregiver Interface

The caregiver interface provides tools for monitoring and assistance:

#### Dashboard Features

- Real-time wheelchair location and status
- Live vital signs monitoring
- Health trend analysis
- Emergency alerts
- Battery and system status
- Usage statistics

#### Patient Management

- Health profiles
- Medical history access
- Emergency contact information
- Care schedule management
- Activity logs

#### Monitoring Tools

- Live health data feed
- Vital signs trends
- Movement patterns
- Fall detection
- Custom health alerts

#### Communication Features

- Direct patient messaging
- Emergency broadcast
- Care team coordination
- Family updates
- Emergency protocols

### Patient Interface

The patient interface combines mobility control with health monitoring:

#### Navigation Control

- AI eye tracking calibration
- Movement sensitivity settings
- Emergency controls
- Location management
- Route planning

#### Health Monitoring

- Personal vital signs
- Activity tracking
- Progress reports
- Emergency contacts

#### Safety Features

- Obstacle warnings
- Fall prevention
- Battery monitoring
- Emergency assistance
- Location sharing

#### Communication Tools

- Caregiver messaging
- Emergency alerts
- Family updates
- Care team contact
- Voice commands

#### Accessibility Features

- High contrast mode
- Voice navigation
- Customizable display
- Screen reader support
- Gesture controls

### Interface Benefits

#### For Caregivers

- Comprehensive monitoring
- Efficient care coordination
- Quick emergency response
- Data-driven decisions
- Enhanced patient safety

#### For Patients

- Enhanced independence
- Intuitive wheelchair control
- Real-time health monitoring
- Improved safety
- Better communication

## Technical Stack

### Frontend

- React.js for the control interface
- Material-UI for component design
- Redux for state management
- WebSocket for real-time communication
- Chart.js for data visualization
- TensorFlow.js for AI processing

### Backend

- Node.js for server-side operations
- Express.js for API endpoints
- MongoDB for data storage
- Python for AI/ML components
- WebSocket for real-time updates
- TensorFlow for eye tracking AI

### Infrastructure

- Docker for containerization
- AWS for cloud hosting
- CI/CD pipeline with GitHub Actions
- Monitoring with Prometheus and Grafana

## Installation and Setup

### Prerequisites

- Node.js (v14 or higher)
- Python 3.8+
- MongoDB 4.4+
- Docker and Docker Compose
- Git

### Environment Setup

1. Clone the repository:

```bash
git clone https://github.com/yourusername/icare-central.git
cd icare-central
```

2. Install dependencies:

```bash
# Main application
cd care-app
npm install

# Python components
cd ../cam_hrv
pip install -r requirements.txt
```

3. Configure environment variables:
Create a `.env` file in the root directory:

```env
# Database Configuration
MONGODB_URI=mongodb://localhost:27017/icare
MONGODB_USER=your_username
MONGODB_PASSWORD=your_password

# Application Configuration
NODE_ENV=development
PORT=3000
API_KEY=your_api_key

# Security
JWT_SECRET=your_jwt_secret
ENCRYPTION_KEY=your_encryption_key
```

4. Start the development servers:

```bash
# Start MongoDB
docker-compose up -d mongodb

# Start the main application
cd care-app
npm run dev

# Start Python components
cd ../cam_hrv
python main.py
```

## Development Guidelines

### Code Style

- Follow ESLint configuration for JavaScript/TypeScript
- Use Prettier for code formatting
- Follow PEP 8 for Python code
- Maintain consistent documentation

### Git Workflow

1. Create feature branches from development
2. Use conventional commits
3. Require code review before merging
4. Maintain clean commit history

### Testing

- Unit tests for all components
- Integration tests for API endpoints
- End-to-end testing for critical paths
- Performance testing for real-time components

## API Documentation

### REST API Endpoints

#### Patient Management

```
GET /api/patients
POST /api/patients
GET /api/patients/:id
PUT /api/patients/:id
DELETE /api/patients/:id
```

#### Monitoring Data

```
GET /api/monitoring/:patientId
POST /api/monitoring/data
GET /api/monitoring/alerts
```

#### System Configuration

```
GET /api/config
PUT /api/config
POST /api/config/backup
```

### WebSocket Events

- `patient:update` - Real-time patient data updates
- `alert:new` - New alert notifications
- `system:status` - System status updates

## Security and Compliance

### Security Measures

- JWT-based authentication
- Role-based access control
- Data encryption at rest and in transit
- Regular security audits
- Input validation and sanitization
- Emergency override protocols
- Secure wheelchair control systems

### Compliance

- HIPAA compliance
- GDPR compliance
- Data retention policies
- Audit logging
- Regular compliance reviews
- Medical device regulations
- Accessibility standards

## Deployment

### Production Deployment

1. Build the application:

```bash
cd care-app
npm run build
```

2. Deploy using Docker:

```bash
docker-compose -f docker-compose.prod.yml up -d
```

### Monitoring

- Application metrics
- System health checks
- Error tracking
- Performance monitoring
- Resource utilization

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

### Development Process

- Follow the coding standards
- Write comprehensive tests
- Update documentation
- Create detailed PR descriptions
- Address review comments

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support, please contact:

- Technical Support: <HD7946@wayne.edu>
- Security Issues:   <Tlatelpa@wayne.edu>
- Sales Inquiries:   <HO5863@wayne.edu>
- General Inquiries: <rkanna@wayne.edu>

## Acknowledgments

- Medical staff and healthcare professionals who provided input
- Open-source community for various tools and libraries
- Development team and contributors
- Healthcare institutions for testing and feedback
- Wheelchair users who provided valuable feedback
- AI/ML researchers and developers
- Accessibility experts and consultants
