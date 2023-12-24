# Using
SMTP protocol
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

def send_email(subject, body, to_email):
    from_email = 'your_email@gmail.com'
    password = 'your_email_password'

    message = MIMEMultipart()
    message['From'] = from_email
    message['To'] = to_email
    message['Subject'] = subject
    message.attach(MIMEText(body, 'plain'))

    with smtplib.SMTP('smtp.gmail.com', 587) as server:
        server.starttls()
        server.login(from_email, password)
        server.sendmail(from_email, to_email, message.as_string())

email_subject = input("Enter email subject: ")
email_body = input("Enter email body: ")
recipient_email = input("Enter recipient email: ")
send_email(email_subject, email_body, recipient_email)
