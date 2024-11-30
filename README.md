# paperStream

## Overview

`paperStream` is a GitHub Actions workflow designed to automatically download Newspaper PDFs from The Hindu's ePaper service. It can be triggered manually or scheduled to run daily. The workflow downloads the specified newspaper as a PDF and sends it to a designated Telegram chat.

## Workflow Configuration

### Triggers

- **Manual Trigger**: Allows the workflow to be executed from the GitHub Actions interface.
- **Scheduled Trigger**: Runs daily at 5:30 AM UTC.

### Jobs

#### `archive_newspaper`

- **Environment**: Windows
- **Permissions**: Write permissions to the repository

#### Steps

1. **Checkout Repository**
   - Uses `actions/checkout@v4` to fetch the repository content.

2. **Download Newspaper**
   - Determines the query date (either from input or today's date).
   - Fetches newspaper data from The Hindu's API.
   - Downloads the newspaper PDF using a provided cookie for authentication.
   - Saves the PDF in the repository workspace.

3. **Telegram Newspaper**
   - Sends the downloaded PDF document to a specified Telegram chat using the Telegram Bot API.
   - Utilizes secrets for authentication and chat identification.

## Secrets Required

- **COOKIE**: Required for authentication to download the newspaper.
- **TELEGRAM_FROM**: Your Telegram bot token for sending notifications.
- **TELEGRAM_TO**: The chat ID where notifications will be sent.

## Usage

1. **Manual Execution**: 
   - Go to the "Actions" tab in your GitHub repository.
   - Select `paperStream` and click on "Run workflow."

2. **Automatic Execution**:
   - The workflow runs automatically every day at 5:30 AM UTC.

## Error Handling

- The workflow includes error handling for API calls, file downloads, and other critical steps. If any step fails, an error message will be logged, and the workflow will exit with a non-zero status.

## Contributions

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

For any questions or feedback, please open an issue in the repository!
