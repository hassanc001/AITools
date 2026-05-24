---
name: Job Seeker Tracker
description: "Scaffold and develop a Spring Boot application for job seekers to track their job applications, interview dates, interview prep notes, impressions, and outcomes. Includes database design, REST APIs, and UI suggestions."
---

# Job Seeker Tracker - Spring Boot Application

## Project Overview

Build a comprehensive Spring Boot application that helps job seekers maintain a detailed record of:
- Job positions they applied for
- Application dates
- Company information
- Interview dates and times
- Interview preparation notes
- Interview impressions and feedback
- Final outcomes (accepted, rejected, pending)

## Data Model / Entities

### JobApplication
```
- id (Long, PK)
- positionTitle (String, required)
- companyName (String, required)
- companyWebsite (String)
- applicationDate (LocalDateTime, required)
- jobDescription (String, large text)
- applicationStatus (Enum: APPLIED, INTERVIEW_SCHEDULED, REJECTED, OFFERED, ACCEPTED)
- salary (BigDecimal)
- jobLocation (String)
- employmentType (Enum: FULL_TIME, PART_TIME, CONTRACT, FREELANCE)
- createdAt (LocalDateTime)
- updatedAt (LocalDateTime)
```

### Interview
```
- id (Long, PK)
- jobApplicationId (Long, FK to JobApplication)
- interviewDate (LocalDateTime, required)
- interviewType (Enum: PHONE, VIDEO, IN_PERSON, PANEL)
- interviewer (String)
- duration (Integer, in minutes)
- prepNotes (String, large text)
- impression (Enum: EXCELLENT, GOOD, NEUTRAL, POOR)
- impressionDetails (String, large text)
- questionsAsked (String, large text)
- responseNotes (String, large text)
- followUpRequired (Boolean)
- createdAt (LocalDateTime)
- updatedAt (LocalDateTime)
```

### Outcome
```
- id (Long, PK)
- jobApplicationId (Long, FK to JobApplication)
- finalOutcome (Enum: ACCEPTED, REJECTED, GHOSTED, WITHDREW)
- outcomeDate (LocalDateTime)
- feedbackReceived (String, large text)
- reason (String, large text)
- nextSteps (String)
- createdAt (LocalDateTime)
- updatedAt (LocalDateTime)
```

## REST API Endpoints

### Job Applications
- `GET /api/applications` - Get all applications (with pagination, filtering)
- `GET /api/applications/{id}` - Get single application with all interviews
- `POST /api/applications` - Create new application
- `PUT /api/applications/{id}` - Update application
- `DELETE /api/applications/{id}` - Delete application
- `GET /api/applications/status/{status}` - Filter by status

### Interviews
- `GET /api/applications/{appId}/interviews` - Get all interviews for an application
- `GET /api/applications/{appId}/interviews/{interviewId}` - Get single interview
- `POST /api/applications/{appId}/interviews` - Add interview to application
- `PUT /api/applications/{appId}/interviews/{interviewId}` - Update interview
- `DELETE /api/applications/{appId}/interviews/{interviewId}` - Delete interview

### Outcomes
- `POST /api/applications/{appId}/outcome` - Record final outcome
- `GET /api/applications/{appId}/outcome` - Get outcome for application
- `PUT /api/applications/{appId}/outcome` - Update outcome

### Statistics
- `GET /api/statistics/summary` - Overall stats (total applications, interviews, success rate)
- `GET /api/statistics/by-status` - Count applications by status
- `GET /api/statistics/by-company` - Stats by company
- `GET /api/statistics/interview-rate` - Percentage of applications leading to interviews

## Technology Stack

- **Framework**: Spring Boot 3.x
- **Language**: Java 17+
- **Build Tool**: Maven or Gradle
- **Database**: PostgreSQL/MySQL (with Spring Data JPA)
- **API**: RESTful with Spring Web
- **Validation**: Spring Validation (Bean Validation)
- **Documentation**: Swagger/SpringFox
- **Testing**: JUnit 5, Mockito
- **Frontend** (Optional): React, Vue, or Angular

## Project Structure

```
job-seeker-tracker/
├── src/main/java/com/jobseeker/
│   ├── controller/
│   │   ├── ApplicationController.java
│   │   ├── InterviewController.java
│   │   └── OutcomeController.java
│   ├── service/
│   │   ├── ApplicationService.java
│   │   ├── InterviewService.java
│   │   └── OutcomeService.java
│   ├── repository/
│   │   ├── ApplicationRepository.java
│   │   ├── InterviewRepository.java
│   │   └── OutcomeRepository.java
│   ├── model/
│   │   ├── JobApplication.java
│   │   ├── Interview.java
│   │   ├── Outcome.java
│   │   └── enums/
│   ├── dto/
│   │   ├── ApplicationDTO.java
│   │   ├── InterviewDTO.java
│   │   └── OutcomeDTO.java
│   └── config/
│       └── AppConfig.java
├── src/main/resources/
│   ├── application.yml
│   └── db/
│       └── migration/ (Flyway migrations)
└── pom.xml
```

## Key Features

### Core Features
- ✅ Track job applications with company details
- ✅ Schedule and manage multiple interviews per application
- ✅ Record interview prep notes and questions
- ✅ Log impressions and feedback after interviews
- ✅ Track final outcomes (accepted, rejected, etc.)
- ✅ View timeline of each application

### Advanced Features
- 📊 Dashboard with statistics and analytics
- 🔍 Filter and search applications (by company, status, date range)
- 📈 Success rate tracking by company/industry
- 🔔 Interview reminders
- 📝 Export applications to PDF/CSV
- 📱 Mobile-friendly UI
- 🔐 User authentication and authorization

## Setup Instructions

### Prerequisites
- Java 17 or higher
- Maven 3.6+ or Gradle 7+
- PostgreSQL 12+ (or MySQL 8+)

### Steps
1. Clone repository
2. Create database: `CREATE DATABASE job_seeker_db;`
3. Update `application.yml` with DB credentials
4. Run migrations: `mvn flyway:migrate`
5. Build: `mvn clean install`
6. Run: `mvn spring-boot:run`
7. Access API: `http://localhost:8080/swagger-ui.html`

## Database Schema Considerations

- Add indexes on frequently queried columns (applicationDate, companyName, status)
- Use soft deletes for audit trails
- Add audit fields (createdAt, updatedAt, createdBy, updatedBy)
- Consider adding a User entity for multi-user support

## Testing Strategy

- Unit tests for services (80%+ coverage)
- Integration tests for repositories
- Controller tests with MockMvc
- End-to-end tests for API flows

## Future Enhancements

- Integration with job boards (LinkedIn, Indeed APIs)
- Salary negotiation tracker
- Interview question database
- Email notifications
- Calendar sync
- Team/shared tracking
- AI-powered interview prep suggestions

## Success Criteria

- ✅ CRUD operations for all entities
- ✅ RESTful API following best practices
- ✅ Proper error handling and validation
- ✅ Database persistence working
- ✅ API documentation complete
- ✅ Unit tests covering services
- ✅ Application deployable