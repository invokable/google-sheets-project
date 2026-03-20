# Onboarding Guide: Google Sheets Laravel Demo Project

## Overview

The **Google Sheets Laravel Demo Project** is a demonstration application that showcases real-time integration between Laravel and Google Sheets using service account authentication. This project serves as a practical example of how to build applications that can read from and write to Google Sheets using modern Laravel features.

**Target Users**: Laravel developers learning Google Sheets integration, particularly those working with Livewire and modern Laravel stack.

**Key Features**:
- **Laravel 13 Framework**: Latest Laravel features with modern PHP 8.2+ support
- **Livewire 4 Integration**: Real-time UI updates using standard Livewire components (not Volt)
- **Google Sheets API**: Service account authentication for server-to-server communication
- **Flux UI Components**: Modern, reactive user interface with Livewire Starter Kit
- **Real-time Data Sync**: Form submissions instantly appear in both Google Sheets and the application

**Primary Use Cases**:
- Learning Google Sheets API integration patterns
- Understanding service account authentication workflows
- Building data collection applications with Google Sheets as backend
- Creating real-time dashboards that sync with spreadsheet data

## Project Structure

This Laravel 13 demo application uses a clean, modern architecture with the following key components:

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

## About fakerphp/faker in Production

The package `fakerphp/faker` is installed using `require` (not `require-dev`) because it is needed by `app/Console/Commands/ResetCommand.php` to generate random names and sentences when resetting the spreadsheet.  
Although `fakerphp/faker` is typically used for development and testing, its use here is limited to generating dummy data via an artisan command.  
There are no security or performance issues with using it in production for this scenario.
