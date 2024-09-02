import re
import uuid
from datetime import datetime
import random

# Simulated Database
users_db = {}
jobs_db = {}
applications_db = {}
interviews_db = {}
reports_db = {}

# Utility Functions
def generate_id():
    return str(uuid.uuid4())

def validate_email(email):
    return re.match(r"[^@]+@[^@]+\.[^@]+", email)

# AI Function: Simple Resume Parser (Simulated)
def parse_resume(resume_text):
    keywords = ['Python', 'Django', 'Machine Learning', 'Data Science', 'AI']
    matched_skills = [kw for kw in keywords if kw.lower() in resume_text.lower()]
    return matched_skills

# User Management
def register_user(full_name, email, password):
    if not validate_email(email):
        return "Invalid email format."
    user_id = generate_id()
    users_db[user_id] = {'full_name': full_name, 'email': email, 'password': password}
    return f"User {full_name} registered successfully."

def login_user(email, password):
    for user_id, details in users_db.items():
        if details['email'] == email and details['password'] == password:
            return f"Login successful. Welcome {details['full_name']}!"
    return "Invalid email or password."

# Job Posting and Management
def create_job(title, description, department, location, employment_type, salary_range, deadline):
    job_id = generate_id()
    jobs_db[job_id] = {
        'title': title,
        'description': description,
        'department': department,
        'location': location,
        'employment_type': employment_type,
        'salary_range': salary_range,
        'deadline': deadline,
        'posted_on': datetime.now(),
    }
    return f"Job '{title}' created successfully."

def list_jobs():
    return jobs_db

# Application Tracking System (ATS)
def submit_application(job_id, applicant_name, applicant_email, resume_text):
    if not validate_email(applicant_email):
        return "Invalid email format."
    
    application_id = generate_id()
    matched_skills = parse_resume(resume_text)
    applications_db[application_id] = {
        'job_id': job_id,
        'applicant_name': applicant_name,
        'applicant_email': applicant_email,
        'resume_text': resume_text,
        'matched_skills': matched_skills,
        'status': 'Applied',
        'submitted_on': datetime.now(),
    }
    return f"Application submitted for job ID {job_id}."

def track_application(application_id):
    return applications_db.get(application_id, "Application not found.")

# Interview Scheduling (Basic Simulation)
def schedule_interview(application_id, interview_date, interview_mode):
    interview_id = generate_id()
    interviews_db[interview_id] = {
        'application_id': application_id,
        'interview_date': interview_date,
        'interview_mode': interview_mode,
        'status': 'Scheduled',
    }
    return f"Interview scheduled for application ID {application_id} on {interview_date} via {interview_mode}."

# Reporting and Analytics
def generate_report():
    report_id = generate_id()
    total_applications = len(applications_db)
    total_jobs = len(jobs_db)
    total_users = len(users_db)
    
    report = {
        'total_applications': total_applications,
        'total_jobs': total_jobs,
        'total_users': total_users,
        'generated_on': datetime.now(),
    }
    reports_db[report_id] = report
    return report

# Console Interface (Simulated interaction)
def main():
    print("Welcome to the Smart Recruiting Platform")
    print("1. Register User")
    print("2. Login User")
    print("3. Create Job")
    print("4. List Jobs")
    print("5. Submit Application")
    print("6. Track Application")
    print("7. Schedule Interview")
    print("8. Generate Report")
    
    choice = int(input("Select an option: "))
    
    if choice == 1:
        full_name = input("Enter Full Name: ")
        email = input("Enter Email: ")
        password = input("Enter Password: ")
        print(register_user(full_name, email, password))
    elif choice == 2:
        email = input("Enter Email: ")
        password = input("Enter Password: ")
        print(login_user(email, password))
    elif choice == 3:
        title = input("Enter Job Title: ")
        description = input("Enter Job Description: ")
        department = input("Enter Department: ")
        location = input("Enter Location: ")
        employment_type = input("Enter Employment Type (Full-time, Part-time): ")
        salary_range = input("Enter Salary Range: ")
        deadline = input("Enter Application Deadline: ")
        print(create_job(title, description, department, location, employment_type, salary_range, deadline))
    elif choice == 4:
        jobs = list_jobs()
        for job_id, details in jobs.items():
            print(f"Job ID: {job_id}, Title: {details['title']}, Department: {details['department']}")
    elif choice == 5:
        job_id = input("Enter Job ID: ")
        applicant_name = input("Enter Applicant Name: ")
        applicant_email = input("Enter Applicant Email: ")
        resume_text = input("Paste Resume Text: ")
        print(submit_application(job_id, applicant_name, applicant_email, resume_text))
    elif choice == 6:
        application_id = input("Enter Application ID: ")
        print(track_application(application_id))
    elif choice == 7:
        application_id = input("Enter Application ID: ")
        interview_date = input("Enter Interview Date (YYYY-MM-DD): ")
        interview_mode = input("Enter Interview Mode (In-Person, Video Call): ")
        print(schedule_interview(application_id, interview_date, interview_mode))
    elif choice == 8:
        report = generate_report()
        print(f"Report generated on {report['generated_on']}")
        print(f"Total Applications: {report['total_applications']}")
        print(f"Total Jobs: {report['total_jobs']}")
        print(f"Total Users: {report['total_users']}")

if __name__ == "__main__":
    main()
