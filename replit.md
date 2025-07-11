# Video Downloader Application

## Overview

This is a Flask-based web application that allows users to download videos from various platforms including YouTube, Instagram, Facebook, Twitter, and TikTok. The application provides a user-friendly interface for analyzing video URLs, selecting download formats, and downloading content with real-time progress tracking.

## System Architecture

The application follows a simple three-tier architecture:

1. **Frontend**: HTML templates with Bootstrap UI framework and vanilla JavaScript
2. **Backend**: Flask web server with REST API endpoints
3. **Core Service**: yt-dlp library for video processing and downloading

The architecture prioritizes simplicity and maintainability, using minimal dependencies to reduce complexity while providing robust video downloading capabilities.

## Key Components

### Backend Components

1. **Flask Application (`app.py`)**
   - Main web server handling HTTP requests
   - RESTful API endpoints for video analysis and downloading
   - Session management with flash messaging
   - Global progress tracking dictionary

2. **Video Downloader Service (`video_downloader.py`)**
   - Wrapper around yt-dlp library
   - Video metadata extraction
   - Format processing and filtering
   - Temporary file management

3. **Application Entry Point (`main.py`)**
   - Simple application launcher
   - Development server configuration

### Frontend Components

1. **Base Template (`templates/base.html`)**
   - Bootstrap dark theme integration
   - Font Awesome icons
   - Responsive navigation and layout structure

2. **Main Interface (`templates/index.html`)**
   - URL input form with validation
   - Loading states and error handling
   - Video information display (incomplete in current files)

3. **Static Assets**
   - Custom CSS (`static/css/style.css`) for enhanced styling
   - JavaScript (`static/js/main.js`) for interactive functionality

## Data Flow

1. **Video Analysis Flow**:
   - User submits video URL through web form
   - Frontend sends POST request to `/get_video_info` endpoint
   - Backend uses VideoDownloader to extract metadata via yt-dlp
   - Video information and available formats returned to frontend

2. **Download Flow**:
   - User selects desired format and initiates download
   - POST request sent to `/download_video` endpoint (implementation incomplete)
   - Backend processes download with progress tracking
   - File served to user or download link provided

3. **Progress Tracking**:
   - Global `download_progress` dictionary stores download states
   - Threading used for background download processing
   - Real-time progress updates (implementation in progress)

## External Dependencies

### Python Libraries
- **Flask**: Web framework for HTTP handling and templating
- **yt-dlp**: Core video downloading and metadata extraction
- **tempfile**: Temporary file management for downloads
- **logging**: Application logging and debugging

### Frontend Libraries
- **Bootstrap**: UI framework with dark theme variant
- **Font Awesome**: Icon library for enhanced visual elements
- **Vanilla JavaScript**: Client-side interactivity without framework dependencies

### Platform Support
- YouTube, Instagram, Facebook, Twitter, TikTok
- Extensible to any platform supported by yt-dlp

## Deployment Strategy

The application is configured for Replit deployment:

- **Host**: `0.0.0.0` for external access
- **Port**: `5000` (standard Flask development port)
- **Debug Mode**: Enabled for development
- **Environment Variables**: Session secret key configuration
- **Static File Serving**: Flask's built-in static file handling

The simple architecture makes it suitable for containerization or traditional server deployment with minimal configuration changes.

## Technical Decisions

### Why Flask over FastAPI/Django
- **Problem**: Need lightweight web framework for video downloading service
- **Solution**: Flask chosen for simplicity and minimal overhead
- **Rationale**: Straightforward request handling without complex ORM or async requirements

### Why yt-dlp over youtube-dl
- **Problem**: Reliable video downloading from multiple platforms
- **Solution**: yt-dlp as actively maintained fork with broader platform support
- **Benefits**: Regular updates, better error handling, extensive format options

### Why Vanilla JavaScript over Framework
- **Problem**: Interactive frontend without complexity overhead
- **Solution**: Plain JavaScript with Bootstrap for styling
- **Rationale**: Minimal bundle size, no build process, easier maintenance

### Temporary File Management
- **Problem**: Handle downloaded files without persistent storage
- **Solution**: Python's tempfile module for automatic cleanup
- **Benefits**: Automatic cleanup, system-appropriate temp directories

## User Preferences

Preferred communication style: Simple, everyday language.

## Recent Changes

### July 06, 2025 - Vercel Deployment & YouTube Bot Detection Fixes
- **Made project fully compatible with Vercel hosting platform**
- Created vercel.json configuration for serverless deployment
- Added vercel_requirements.txt with essential dependencies
- Created WSGI entry point and deployment documentation
- Added .vercelignore file to optimize deployment
- **Enhanced YouTube bot detection handling for cloud platforms**
- Added multiple user agent rotation to avoid detection patterns
- Implemented exponential backoff with jitter for retry attempts
- Added Android mobile client fallback for better server compatibility
- Enhanced HTTP headers to mimic legitimate browser requests
- Added specific error handling for different YouTube restriction types
- Implemented multiple extraction strategies (enhanced → basic → fallback)
- **Design improvements for balanced visual appeal**
- Added animated black and blue gradient background
- Reduced navbar height and made it more compact
- Brought back visual elements with balanced approach (not too minimal)
- Enhanced navigation tabs with gradients and hover effects
- Improved button styling with gradients and transforms
- Made footer more compact while retaining full functionality

### July 01, 2025 - Quality Selection & Download Fixes
- Fixed quality selection click handlers in JavaScript
- Installed FFmpeg for video processing capabilities  
- Added automatic browser download when processing completes
- Improved file finding logic to handle special characters in filenames
- Enhanced format selection to avoid unnecessary conversions
- Added intelligent format fallbacks for better compatibility
- **MAJOR FIX**: Resolved quality selection issue where all downloads defaulted to 360p
- Updated format selection logic to use raw yt-dlp format data for accurate quality matching
- Added specific format ID selection based on available video formats
- Improved format sorting by height and bitrate for better quality control
- Added "Playlist coming soon" badge next to YTdown heading

### Current Status
- Video analysis working for YouTube, Instagram, Facebook
- Quality selection interface fully functional and now respects user-selected quality
- Download process working with MP4, WebM, MKV, AVI formats
- Automatic file download to user's device implemented
- Format conversion working for multiple output formats
- Quality selection now properly downloads 480p, 720p, 1080p as selected
- **NEW**: Clean, minimal design with reduced visual complexity

## User Preferences

Preferred communication style: Simple, everyday language.
Preferred design style: Minimal, clean, not heavy or cluttered.

## Changelog

Changelog:
- July 06, 2025. Minimal design overhaul for cleaner interface
- July 01, 2025. Initial setup and quality selection fixes