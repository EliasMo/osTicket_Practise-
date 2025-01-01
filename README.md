# osTicket

### Using OsTicket 

The tutorial outlines the use of ticketing systems in an Enterprise Enviroment. Check out Hybrid AD to set up your Windows Server 2022 and Active Directory.

### Tech Used 
- Windows Server 2022
- Internet Information Services (IIS)

### Setting up osTicket 

## Downloading PHP
![image](https://github.com/user-attachments/assets/0ec9333f-39a9-4a8c-a2e2-2cfa1c4bd2dd)

## Download components for IIS
These IIS components are essential prerequisites because they're required for osTicket to function properly.
- Go to Common HTTP Features
    - Default Document
    - Directory Browsing
    - HTTP Errors
    - Static Content

![image](https://github.com/user-attachments/assets/f0fb35dd-39b9-483e-8d48-e06671e54e0c)

- Application Developement
    - CGI
    - ISAPI Extensions
    - ISAPI Filters

![image](https://github.com/user-attachments/assets/d7ce9365-31ae-409e-925b-c5b6b0111b3b)

- Security
  - Basic Authentication
  - Request Filtering
 
![image](https://github.com/user-attachments/assets/6a4aa52f-8831-4d25-96ee-dd10433259ba)

- Performance
    - Static Content Compression
 
![image](https://github.com/user-attachments/assets/628cfd89-895d-4b2e-b8b8-9a09ba893a24)


## Configure PHP on IIS

Open system Properties, Click on Enviroment Variables , under system variables - click path and edit then new
![image](https://github.com/user-attachments/assets/7ba6ae22-36d3-4303-a738-07630a751a7c)

Head to handler mappings 
![image](https://github.com/user-attachments/assets/cf632dd5-4203-4aa9-9daf-e5f008c12265)

go to 'Add Module Mappings' and enter in this

![image](https://github.com/user-attachments/assets/106c39f1-40fe-44d0-9c5e-c3dffbb73111)

This will add PHP handling capability to the IIS. Click Yes to allow IIS to process PHP files.

![image](https://github.com/user-attachments/assets/602e2189-bd8a-467f-8cd3-3a94832f1d80)


## Test 
Go to C: > inetpub > wwwroot 
Create a file and name it info.php. and write

```php
<?php phpinfo(); ?>
```

Make sure you save it as all files 
![image](https://github.com/user-attachments/assets/1feb23f4-50e8-493b-8991-6e51134ddfed)

# Ensure you delete this file after testing for security.


- Note that you may have to update Microsoft Visual C++ for the 2022 version to make this work. Download it from here, i got the X64 version. (https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)

![image](https://github.com/user-attachments/assets/999397fb-c2f2-4d61-932f-3d4974469e06)

This is how info.php look like: 
![image](https://github.com/user-attachments/assets/b00cdbee-f30e-4c05-9cec-76193e18830d)


## osTicket  and MySQL Installation 

### Download and File Setup 
1. Download osTicket
Go to osTicket.(https://osticket.com/download/)
![image](https://github.com/user-attachments/assets/18ad3035-9ca4-4aac-b10c-d760532126df)

For the enterprise implemetation, Select these key plugins:
  - Authentication::LDAP and AD
      - Enables integration with AD
      - Allows domain user login

  - Audit:: Audit Log
      - Tracks system changes
      - Security moniotoring
      - User activity logs

  - Authentication:: Password Policy
      - Enforce password policy
        

  - Storage :: Attachments on the Filesystem
      - Local file storage
        
![image](https://github.com/user-attachments/assets/056499a5-bb61-48be-bc69-1e8f85c07642)

3. Extract to a temp location
![image](https://github.com/user-attachments/assets/9b326f9d-812c-4711-9d3d-90c76b038e62)




4. copy upload folder to C:\inetpub\wwwroot
![image](https://github.com/user-attachments/assets/eca70e37-1bea-47e8-8708-cc1b32e48b8a)


5. rename folder to 'osTicket'
![image](https://github.com/user-attachments/assets/7b463091-b3c8-4d30-a6e6-7990ec6a553d)


## osTicket Setup 

### File Configuration 

1. Rename config file to ost-config.php in 'osTicket\include' 
![image](https://github.com/user-attachments/assets/d9f78980-d3d3-4444-b3b7-e7af0fbf3bb0)


2. Configure file permissions

Go to propeties -> Security tab -> Advanced button -> and diable inheritance. 

![image](https://github.com/user-attachments/assets/4272dacf-f980-4d2a-903a-3e9c2fe37d81)

Click Remove all inherited permissions.
![image](https://github.com/user-attachments/assets/4e06cccd-9aad-480e-bb7a-1b5b9bc873fd)

Click add and write everyone. After installation we can change the permissions to better settings for security.
![image](https://github.com/user-attachments/assets/c8ee5f47-6f5c-47c4-8d90-ea77be764026)

In the permissions window - check 'Full Control'.

![image](https://github.com/user-attachments/assets/9c96282c-2e25-4fd0-ac2a-8192a1ee9d52)

To make osTicket work we need to create PHP.ini configuration file - this tells PHP how to behave. It controls:
1) Which extensions are loaded
2) Memory limits
3) File upload sizes
4) Error reporting
4) Session handling

To make it: got to C:\PHP and find php.ini-development.

![image](https://github.com/user-attachments/assets/30e5246b-2fae-4249-849f-488af957d655)

Copy it and rename it to php.ini. There we can edit to enable the needed extensions. 
![image](https://github.com/user-attachments/assets/41522e6a-2e22-45aa-b3cf-43b5b3bd71dc)

------------------
Downlaod MySQL 
![image](https://github.com/user-attachments/assets/d93556af-5f16-4527-8a88-4b64c8d958fc)

Create Root password 
![image](https://github.com/user-attachments/assets/f0fa2947-1fb0-40bd-87dc-88c68ce24316)

Test Mysql is working 
![image](https://github.com/user-attachments/assets/c754bb11-b846-4162-a4cb-d53d1615b6e3)




