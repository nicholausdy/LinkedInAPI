# LinkedInAPI
API to grab account data (name, profession, region), education data (degree and last education institution), and workplace data (current and last workplace) from LinkedIn

A. Architecture in a nutshell:

Server module queries the database to find user id. If it is not found, the server launches the web scraping module using Selenium. If the user id is found by Selenium, then the data will be stored in a local database (PostgreSQL).

B. How to Use:
1. Find user ID from LinkedIn URL (ex:https://www.linkedin.com/in/nicholaus-yosodipuro-08222a18b/?originalSubdomain=id -> 08222a18b is the user ID 
2. There are three endpoints (you can change the domain name and port number on the source code)
    
    a. http://localhost:8000/users/accounts/general/<user id> -> used to grab account data
        
        Ex output:
          {"AccountID": "08222a18b", "AccountName": "Nicholaus Yosodipuro", "AccountTitle": "Information System and Technology Undergraduate Student at Bandung Institute of Technology (ITB)", "AccountRegion": "Greater Jakarta Area, Indonesia"}
    
    b. http://localhost:8000/users/accounts/education/<user id> -> used to grab education data
        
        Ex output:
          {"AccountID": "08222a18b", "EducationInstitution": "Institut Teknologi Bandung (ITB)", "EducationTitle": "Bachelor's degree"}
    
    c. http://localhost:8000/users/accounts/workplace/<user id> -> used to grab workplace data
        
        Ex output:
          {"AccountID": "805965120", "Workplace1": "Packet Systems Indonesia", "Workplace2": "Telkom University"}
 
 3. Type the endpoints on browser or HTTP GET from command line

C. How to Install:

1. Prerequisite: OS based on Linux kernel (preferred OS) or Windows (might need some configuration and source code change)

2. Install required dependencies:

  a. Mozilla Firefox (make sure you've got the headless version to reduce overhead)
  
  b. Geckodriver to run Mozilla Firefox
  
  c. Python 3.x.x 
  
  d. PostgreSQL (v 10.10) as the database back-end (note: configure /path/to/pg_hba.conf file to change user authentication method for both IPv4 and IPv6 from ident to md5)
  
  e. These Python 3 packages (pip install):
    
    e.1. selenium for web browser automation 
    
    e.2. parsel for web scraping
    
    e.3. subprocess to kill some system processes
    
    e.4. psycopg2 for interface to PostgreSQL
    
    e.5. urllib.parse for parsing URL
    
    e.6. http.server for web server
    
    d.7. json for generating JSON format

3. git clone <repo_URL>

4. Launch the server! 
      
      python3 server.py
  
