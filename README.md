import datetime
import smtplib
from email.message import EmailMessage

def generate_report():
    """Generates a simple daily report."""
    today = datetime.date.today()
    report_content = f"Daily Report for {today}\n"
    report_content += "--------------------------\n\n"
    report_content += "Key Metrics:\n"
    report_content += "- Website traffic: 1,250 unique visitors\n"
    report_content += "- Sales: $5,000\n"
    report_content += "- Support tickets closed: 15\n\n"
    report_content += "Summary: All systems are operational.\n"
    return report_content

def save_report(report):
    """Saves the report to a file."""
    filename = f"daily_report_{datetime.date.today()}.txt"
    with open(filename, 'w') as f:
        f.write(report)
    print(f"Report saved to {filename}")

def send_email_report(report):
    """Sends the daily report via email."""
    sender_email = "your_email@example.com"
    receiver_email = "recipient_email@example.com"
    password = "your_app_password"  # Use an app password, not your main password

    msg = EmailMessage()
    msg['Subject'] = f"Daily Report - {datetime.date.today()}"
    msg['From'] = sender_email
    msg['To'] = receiver_email
    msg.set_content(report)

    try:
        with smtplib.SMTP_SSL('smtp.gmail.com', 465) as smtp:
            smtp.login(sender_email, password)
            smtp.send_message(msg)
        print("Email report sent successfully!")
    except Exception as e:
        print(f"Error sending email: {e}")

if __name__ == "__main__":
    report_text = generate_report()
    save_report(report_text)
    send_email_report(report_text)
