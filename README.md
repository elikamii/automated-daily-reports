import datetime

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

if __name__ == "__main__":
    report_text = generate_report()
    save_report(report_text)
