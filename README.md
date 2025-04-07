# LearnDash CSV Importer

![LearnDash CSV Importer](https://img.shields.io/badge/Version-1.0-brightgreen) ![WordPress](https://img.shields.io/badge/WordPress-Compatible-blue) ![License](https://img.shields.io/badge/License-GPL-orange)

## Overview

The **LearnDash CSV Importer** is a powerful WordPress plugin designed to streamline the process of importing LearnDash modules, lessons, topics, and quizzes using a CSV file. This plugin provides extensive functionality, including validation, custom logging, dynamic course creation, and advanced CSV processing, making course creation faster and more efficient.

Donate link: <a href="https://www.paypal.com/donate?hosted_button_id=7EL8K7ELFWHSY">Buy Me a Coffee?</a>

## Features

### 1. **CSV Import Capabilities**
- Import Courses (`sfwd-courses`), Lessons (`sfwd-lessons`), Topics (`sfwd-topic`), and Quizzes (`sfwd-quiz`).
- Process CSV files containing structured data with custom fields such as `course_id`, `lesson_title`, and more.

### 2. **Validation Before Processing**
- Ensures all required fields (`course_id`, `lesson_title`,`topic_title`, `lesson_order`,`topic_order`, `type`) are present.
- Checks for missing values or inconsistent column counts in the CSV file.
- Logs validation errors for easy debugging.

### 3. **Dynamic Course Handling**
- Checks if a course already exists based on its title.
- Dynamically maps dummy `course_id` values to real `course_id` values.
- Automatically creates new courses if they do not exist.

### 4. **Logging System**
- Comprehensive logging to track imports and issues.
- Real-time logs displayed directly in the WordPress admin interface.
- Log file stored in the WordPress upload directory for persistence.

### 5. **Customizable Workflow**
- Upload any CSV file with customizable column names.
- Supports comma-separated values, including fields with escaped commas.

### 6. **Error Handling**
- Detects and reports missing lessons or invalid lesson IDs during topic/quiz creation.
- Provides feedback on existing lessons, topics, or quizzes to avoid duplicates.

## Installation

1. **Upload the Plugin**:
   - Copy the `learndash_csv_importer` directory into the `/wp-content/plugins/` directory of your WordPress installation.
2. **Activate the Plugin**:
   - Log in to your WordPress admin panel and activate the plugin under `Plugins > Installed Plugins`.
3. **Navigate to the Importer**:
   - Go to `LearnDash Upload Importer` in the WordPress admin menu.

## How to Use

### Step 1: Prepare Your CSV File
- Ensure your CSV file has the following required columns:
  - `course_id`: The ID of the LearnDash course (or a dummy ID for new courses).
  - `lesson_title`: The title of the lesson or topic.
  - `lesson_order`: Order number for lessons within a course.
  - `type`: The type of content (`sfwd-courses`, `sfwd-lessons`, `sfwd-topic`, or `sfwd-quiz`).

#### Example CSV Format
```csv
course_id,lesson_title,lesson_order,topic_title,topic_order,type
1001,Introduction to LearnDash,1,,1,sfwd-courses
1001,Modul 1: Introduction,1,,1,sfwd-lessons
1001,Lektion 1: Overview,1,What is a Blockchain?,1,sfwd-topic
1001,Test: Basic Quiz,2,,2,sfwd-quiz
```

### Step 2: Upload the CSV File
1. Navigate to the **LearnDash Upload Importer** page in the WordPress admin panel.
2. Use the `CSV-Datei hochladen` option to upload your file.
3. Click `Datei hochladen`.

### Step 3: Validate and Import
1. Click `CSV importieren` to validate and process the uploaded file.
2. Validation errors, if any, will be displayed in the log.

### Step 4: Review Logs
- Logs are displayed in the `Protokoll` section.
- You can delete the log file using the `Log-Datei löschen` button.

## Advanced Features

### File Validation
The plugin ensures:
- The CSV header includes required columns.
- Each row contains the same number of fields as the header.
- Mandatory fields are filled in every row.

### Support for Escaped Values
- Handles commas inside fields when properly escaped with double quotes (`"value, with, commas"`).

### Dynamic Course Creation
- Checks if a course already exists by title.
- Automatically creates a course if it does not exist and maps related content.

### Custom Post Management
- Automatically checks if lessons, topics, or quizzes already exist to avoid duplicates.

## Development

### Functions Included

#### CSV Processing
- **`learndash_csv_importer_process_file($file_path)`**
  Processes the CSV file and creates posts for courses, lessons, topics, or quizzes.

#### Validation
- **`learndash_csv_importer_validate_file($file_path)`**
  Validates the structure and content of the CSV file before processing.

#### Logging
- **`learndash_csv_importer_log_message($message)`**
  Writes messages to the log file and displays them in real-time.

#### Dynamic Content Creation
- **`learndash_csv_importer_create_course($course_title)`**
- **`learndash_csv_importer_create_lesson($course_id, $lesson_title, $lesson_order)`**
- **`learndash_csv_importer_create_topic($course_id, $lesson_title, $topic_title, $topic_order)`**
- **`learndash_csv_importer_create_quiz($course_id, $lesson_title, $quiz_title, $quiz_order)`**

## FAQ

### 1. What happens if a course, lesson, topic, or quiz already exists?
The plugin checks for existing posts by title and skips duplicates.

### 2. What if my CSV contains errors?
Validation errors are logged and displayed in the admin panel. Processing will stop for rows with errors.

### 3. Can I use custom column names?
No, the plugin requires specific column names (`course_id`, `lesson_title`, etc.).

### 4. Where are the logs stored?
Logs are saved in the `wp-content/uploads/` directory as `learndash_import_log.txt`.

## License

This project is licensed under the GPL License. See the LICENSE file for details.

## Contributing

I welcome contributions to improve this plugin! Please submit a pull request or open an issue on the GitHub repository.

## Support
Your issues: https://github.com/markusbegerow/learndash-csv-importer/issues
