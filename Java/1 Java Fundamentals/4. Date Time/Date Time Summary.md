Tags: 
- [[Java]]
### 1. **Legacy API (java.util.Date / java.util.Calendar)**

- **Date**: Represents a specific moment in time (but only down to milliseconds).
- **Calendar**: A more flexible class to manipulate dates and times (like adding days, months, etc.).
- These APIs are considered **outdated** and **prone to errors** (like handling time zones poorly).
### 2. **Modern API (java.time, since Java 8)**

- **LocalDate**: Represents a date without time (e.g., 2024-10-12).
- **LocalTime**: Represents a time without date (e.g., 14:30:15).
- **LocalDateTime**: Combines both date and time.
- **ZonedDateTime**: Includes time zone (e.g., "2024-10-12T14:30:15+02:00[Europe/Paris]").
- **Instant**: Represents an exact moment in UTC.

The **java.time** package is thread-safe, easier to use, and addresses many issues from the legacy API.

> For most new projects, **use the java.time package**.