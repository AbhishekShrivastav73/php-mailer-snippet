
# PHP Mailer Code-Snippet

This repository demonstrates how to send emails using the PHPMailer library in PHP. The provided function sends an HTML email via SMTP, using the PHPMailer files downloaded manually.

## Prerequisites

Before using this script, ensure that you have the following:

- [PHP](https://www.php.net/downloads) installed on your system.
- PHPMailer files downloaded manually. You should have the `src` folder from the PHPMailer repository included in your project.

You can download the PHPMailer repository directly from [PHPMailer's GitHub](https://github.com/PHPMailer/PHPMailer).

## Setup

1. Download the PHPMailer source files from [PHPMailer's GitHub](https://github.com/PHPMailer/PHPMailer).
2. Extract the files and copy the `src` folder into your project directory.
3. Include the required PHPMailer files in your script as shown below.

## Usage

To use this script, simply include the PHPMailer files and call the `sendEmail` function with the recipient's email, subject, and body of the email.

### Code Snippet

```php
<?php
// Include PHPMailer files
require '../phpmailer/src/PHPMailer.php';
require '../phpmailer/src/SMTP.php';
require '../phpmailer/src/Exception.php';

// Function to send email
function sendEmail($toEmail, $subject, $body) {
    $mail = new PHPMailer(true);

    try {
        // Server settings
        $mail->isSMTP();
        $mail->Host = 'smtp.gmail.com'; // Replace with your SMTP server
        $mail->SMTPAuth = true;
        $mail->Username = 'your-email@example.com'; // Replace with your email
        $mail->Password = 'your-email-password'; // Replace with your email password
        $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
        $mail->Port = 587;

        // Recipients
        $mail->setFrom('your-email@example.com', 'Your Name'); // Replace with your email and name
        $mail->addAddress($toEmail);

        // Content
        $mail->isHTML(true);
        $mail->Subject = $subject;
        $mail->Body    = $body;

        $mail->send();
        return true;
    } catch (Exception $e) {
        error_log("Mailer Error: {$mail->ErrorInfo}");
        return false;
    }
}
?>
```

### How to Use

1. Download and extract the PHPMailer source files and place them in your project directory.
2. Include the necessary files by adding the `require` statements to your PHP script (as shown in the code snippet).
3. Replace `'your-email@example.com'` and `'your-email-password'` with your actual email credentials.
4. Call the `sendEmail` function with the recipient's email, subject, and body.

## Important Notes

- Always use **app-specific passwords** for Gmail when using Gmail's SMTP.
- If you're using Gmail's SMTP server, you may need to enable **Less Secure Apps** or use **OAuth 2.0** for improved security.
- Make sure to securely handle your credentials and avoid hardcoding sensitive information in the source code.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---


