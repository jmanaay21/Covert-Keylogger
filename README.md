# Covert-Keylogger
python based key logger that runs when you open a jpeg

# Project Goal:
Built a python script that I embedded in a jpeg such that when the jpeg is opened the script captures the targets keystrokes
for a set amount of time, saves those keystrokes in a txt file and emails the text file to me.

# Code Break Down
## Begin with imports from python libraries that will make the code possible:

 - smtplib: for sending emails using the Simple Mail Transfer Protocol (SMTP).
 - os: for interacting with the operating system, such as file and path operations.
 - time: for handling time-related functions, including delays and timestamps.
 - yaml (as yml): for loading configuration data from YAML files (e.g., email credentials).
 - pynput.keyboard: for capturing and logging keystrokes using a keyboard listener.
 - email.mime.multipart.MIMEMultipart: for constructing multipart email messages.
 - email.mime.text.MIMEText: for adding plain text content to the email body.
 - email.mime.base.MIMEBase: for handling attachments in email messages.
 - sys: for accessing system-specific parameters and functions, particularly for handling paths in executable environments.

![image](https://github.com/user-attachments/assets/b5170469-88ad-4909-99ba-21bd8ba1f437)


## Resource Path and Credential Loading from my Yml file

This section of the code handles the safe loading of credentials from an external YAML file (DO_NOT_SHARE.yml). The resource_path function ensures the correct file path is used, whether the script is run normally or as a PyInstaller executable. By dynamically setting the base_path, the code can locate resources seamlessly in both development and deployed environments. This super important for when you convert your file from py to .exe
The email credentials (sender_email, receiver_email, and password) are securely fetched from my YAML file called  (DO_NOT_SHARE.yml), allowing for easier configuration management and avoiding hardcoding sensitive information directly in the script. And the keyfile path is where all captured keystrokes will be logged for later remote extraction via email.

![image](https://github.com/user-attachments/assets/3dfce0ab-e8d3-4a86-9d83-1209bdaf51e5)


![image](https://github.com/user-attachments/assets/3c26d272-209f-4e98-bf8b-0254d14247e4)


![image](https://github.com/user-attachments/assets/ba2eed7a-0f0b-493a-ade4-ed77d15b41c5)

# Executable creation and Winrar embedding
![image](https://github.com/user-attachments/assets/10a06c19-8d3f-43d3-aafe-86a8f48f1405)

I needed to include the the YML file in the executable package I created

![image](https://github.com/user-attachments/assets/da0db9a7-65c3-4176-9ee1-615f4a9ba973)

![image](https://github.com/user-attachments/assets/caa52233-edcd-4713-b4ff-850f95fb0d30)


# Demo
![image](https://github.com/user-attachments/assets/97262ed6-e9e1-4f70-8f91-1fd1099bf67d)

![image](https://github.com/user-attachments/assets/18b9580c-5591-4213-a924-8b5495abb8a7)

![image](https://github.com/user-attachments/assets/befde4aa-fc91-4d34-94cd-e6d1d5d983ec)

![image](https://github.com/user-attachments/assets/0bf59c03-e075-4059-84fc-97fec3182680)




