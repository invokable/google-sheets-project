# Onboarding Guide: Google Sheets Laravel Demo Project

## Overview

The **Google Sheets Laravel Demo Project** is a demonstration application that showcases real-time integration between Laravel and Google Sheets using service account authentication. This project serves as a practical example of how to build applications that can read from and write to Google Sheets using modern Laravel features.

**Target Users**: Laravel developers learning Google Sheets integration, particularly those working with Livewire and modern Laravel stack.

**Key Features**:
- **Laravel 12 Framework**: Latest Laravel features with modern PHP 8.2+ support
- **Livewire 3 Integration**: Real-time UI updates using standard Livewire components (not Volt)
- **Google Sheets API**: Service account authentication for server-to-server communication
- **Flux UI Components**: Modern, reactive user interface with Livewire Starter Kit
- **Real-time Data Sync**: Form submissions instantly appear in both Google Sheets and the application

**Primary Use Cases**:
- Learning Google Sheets API integration patterns
- Understanding service account authentication workflows
- Building data collection applications with Google Sheets as backend
- Creating real-time dashboards that sync with spreadsheet data

## Project Structure

This Laravel 12 demo application uses a clean, modern architecture with the following key components:

### Main Application Components

- **`app/Livewire/Sheets/Form.php`** - Handles the form for adding entries to Google Sheets
  - Validates user input (name and message fields)
  - Appends data to the configured Google Sheet
  - Dispatches events for real-time UI updates

- **`app/Livewire/Sheets/Posts.php`** - Displays recent entries from Google Sheets
  - Retrieves and transforms spreadsheet data
  - Shows the latest 10 entries in reverse chronological order
  - Updates automatically when new posts are added

### Configuration Files

- **`config/sheets.php`** - Project-specific Google Sheets configuration
  - `POST_SPREADSHEET_ID` - Target spreadsheet identifier
  - `POST_SHEET_ID` - Specific sheet/tab within the spreadsheet

- **`config/google.php`** - Google API client configuration
  - Service account authentication settings
  - API credentials and access scopes

### Frontend & UI

- **Livewire Starter Kit** - Modern Laravel frontend scaffolding
- **Flux UI Components** - Reactive UI components for forms and data display
- **Tailwind CSS** - Utility-first CSS framework for styling

### Testing Infrastructure

- **PHPUnit** - Unit and feature testing
- **Mockery** - API mocking for Google Sheets interactions
- **Laravel Pint** - Code style enforcement

## Setup Instructions

### 1. Environment Configuration

Copy the environment template and configure your local settings:

```bash
cp .env.example .env
```

### 2. Google API Credentials Setup

**Note**: This step cannot be fully tested in Copilot due to API restrictions.

1. Create a Google Cloud Project at [Google Cloud Console](https://console.cloud.google.com/)
2. Enable the Google Sheets API and Google Drive API
3. Create a Service Account and download the JSON credentials file
4. Place the JSON file in `storage/sheets-service-account.json`
5. Configure the following environment variables:

```env
GOOGLE_SERVICE_ENABLED=true
GOOGLE_SERVICE_ACCOUNT_JSON_LOCATION="storage/sheets-service-account.json"
```

### 3. Google Sheets Configuration

1. Create a new Google Spreadsheet
2. Share it with your service account email (found in the JSON credentials)
3. Copy the spreadsheet ID from the URL
4. Configure environment variables:

```env
POST_SPREADSHEET_ID=your_spreadsheet_id_here
POST_SHEET_ID=Sheet1
```

## About fakerphp/faker in Production

The package `fakerphp/faker` is installed using `require` (not `require-dev`) because it is needed by `app/Console/Commands/ResetCommand.php` to generate random names and sentences when resetting the spreadsheet.  
Although `fakerphp/faker` is typically used for development and testing, its use here is limited to generating dummy data via an artisan command.  
There are no security or performance issues with using it in production for this scenario.
