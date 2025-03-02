# Covert-Keylogger
python based key logger that runs when you open a jpeg

# Project Goal:
Built a python script that I embedded in a jpeg such that when the jpeg is opened the script captures the targets keystrokes
for a set amount of time, saves those keystrokes in a txt file and emails the text file to me.

# Code Break Down
**Begin with imports from python libraries that will make the code possible:**

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


**Resource Path and Credential Loading from my Yml file**

This section of the code handles the safe loading of credentials from an external YAML file (DO_NOT_SHARE.yml). The resource_path function ensures the correct file path is used, whether the script is run normally or as a PyInstaller executable. By dynamically setting the base_path, the code can locate resources seamlessly in both development and deployed environments. This super important for when you convert your file from py to .exe

The email credentials (sender_email, receiver_email, and password) are securely fetched from my YAML file called  (DO_NOT_SHARE.yml), allowing for easier configuration management and avoiding hardcoding sensitive information directly in the script. And the keyfile path is where all captured keystrokes will be logged for later remote extraction via email.

![image](https://github.com/user-attachments/assets/3dfce0ab-e8d3-4a86-9d83-1209bdaf51e5)

### Keylogger Deployment and Execution  

This section is where I deploy the keylogger, which captures all of the targerts key strokes for 20 seconds. The "keyPressed" function is the core of the keylogger, recording each keystroke to the "Keyfile.txt". Regular characters are logged directly, while special inputs like the spacebar are logged in a bracketed format ([key.enter]),making it easier to analyze later on.

The pynput library creates a keyboard listener that runs asynchronously, allowing the program to continue executing while keystrokes are captured. After 20 seconds, the listener automatically stops, and the program validates whether the log file exists before proceeding to send the data via email. Note that ensuring the log file exits is important to ensuring that the extract data is ready for extraction.
![image](https://github.com/user-attachments/assets/3c26d272-209f-4e98-bf8b-0254d14247e4)

### Email Creation and Transmission  

This section is where the email is generated and sent, containing the logged keystroke data as an attachment. The MIMEMultipart object is used to construct the email, with the sender and receiver information assigned dynamically from the stored credentials. This is important to remember because this means that I will need to store yml file with my login credentials in the file path when create an excutable. 

The body of the email is kept minimal, serving only as a placeholder, while the keylogger.txt generate before is attached to the message. The file is opened in **binary mode, and its contents are loaded as an octet-stream, ensuring compatibility with different email clients. The content-Disposition header is added to specify that the file should be treated as an attachment, using its original filename.  

Once the email is fully composed, an **SMTP session** is established using Gmail’s SMTP server (`smtp.gmail.com`). The connection is **secured with TLS**, and the script logs into the sender's email account using the extracted credentials. The email is then sent to the recipient, ensuring remote access to the captured keystroke data.  

The script includes a **try-except block** to handle potential errors, such as incorrect login credentials or network issues. If the email is sent successfully, a confirmation message is displayed. Otherwise, any encountered error is printed for debugging purposes.

![image](https://github.com/user-attachments/assets/ba2eed7a-0f0b-493a-ade4-ed77d15b41c5)

# Executable creation and Winrar embedding
![image](https://github.com/user-attachments/assets/10a06c19-8d3f-43d3-aafe-86a8f48f1405)

I needed to include the the YML file in the executable package I created as previously mentioned

![image](https://github.com/user-attachments/assets/da0db9a7-65c3-4176-9ee1-615f4a9ba973)

![image](https://github.com/user-attachments/assets/caa52233-edcd-4713-b4ff-850f95fb0d30)


# Demo

![image](https://github.com/user-attachments/assets/633d9869-7f3a-4f27-ada2-046db6b28f17)


![image](https://github.com/user-attachments/assets/59e8c358-75d1-48d8-8aae-36d161087cb7)


![image](https://github.com/user-attachments/assets/0bf59c03-e075-4059-84fc-97fec3182680)




