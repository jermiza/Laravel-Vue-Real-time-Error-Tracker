#Project is Ongoing


# Vue-Laravel Real-time Error Tracker

## Idea
A tool that integrates Vue.js with Laravel to provide real-time error tracking and debugging information.

## Description
Vue-Laravel Real-time Error Tracker streamlines the debugging process by displaying real-time errors and stack traces in the Vue.js frontend while leveraging Laravel's backend for error logging and management.

## Features
- **Real-time Error Notification:** Instant notifications in Vue.js frontend on errors from Laravel backend.
- **Detailed Error Information:** Display comprehensive error messages and stack traces.
- **Error Dashboard:** Vue.js component for managing recent errors with filtering and sorting.
- **Error Resolution Workflow:** Manage error statuses (resolved, in-progress, ignored) directly from the dashboard.
- **User Context Tracking:** Include user session details and actions leading to errors.
- **Configurable Notifications:** Customize error triggers and notification display.
- **Logging Options:** Log errors to file or database for persistence and analysis.

## Technical Implementation

### Backend (Laravel)
- Middleware to catch exceptions and send them via WebSocket to the frontend.
- Logging mechanism for storing errors (file or database).
- API endpoints for error management and user context retrieval.

### Frontend (Vue.js)
- WebSocket client for real-time error notifications.
- Notification system for immediate developer alerts.
- Error dashboard component for error management.
- Error detail component showing stack traces and additional details.
- Integration with Vue Router to capture user actions leading to errors.




# Laravel Backend Setup
### Install the Laravel WebSockets package to enable real-time communication.

```
composer require beyondcode/laravel-websockets
```

### Configure WebSockets

#### Configure your WebSocket settings in config/websockets.php.

### Set Up Broadcasting

#### Enable Pusher broadcasting in config/broadcasting.php.

```
'connections' => [
    'pusher' => [
        'driver' => 'pusher',
        'key' => env('PUSHER_APP_KEY'),
        'secret' => env('PUSHER_APP_SECRET'),
        'app_id' => env('PUSHER_APP_ID'),
        'options' => [
            'cluster' => env('PUSHER_APP_CLUSTER'),
            'useTLS' => true,
        ],
    ], 
],
```


### Create ErrorEvent

#### Generate an event for broadcasting errors.

```
php artisan make:event ErrorOccurred
```
