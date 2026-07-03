<h1>Directory Traversal Attack Lab- Codepath CYB102</h1>

<h2>Description</h2>
Project consists of a simple PowerShell script that walks the user through "zeroing out" (wiping) any drives that are connected to the system. The utility allows you to select the target disk and choose the number of passes that are performed. The PowerShell script will configure a diskpart script file based on the user's selections and then launch Diskpart to perform the disk sanitization.
<br />


<h2>Languages and Utilities Used</h2>
 
- <b>Bash</b>
- <b>VIM</b>

<h2>Environments Used </h2>

- <b>Ubuntu Virtual Machine: connected via RDP</b> 

<h2>Walk-through:</h2>

<p align="center">
Figure 1: Navigated to the ftp_folder, which contains all the files needed for the project: <br/>
<img width="554" height="80" alt="dta_1" src="https://github.com/user-attachments/assets/21e9c575-2c9b-4551-bf6d-56210adf1bf7" />
<br />
attack.sh is an executable file that contains a bash script to attack our test ftp server.
<br />
<br />
Figure 2: Navigated to the scripts folder, which contains two js. files:  <br/>
<img width="320" height="59" alt="image" src="https://github.com/user-attachments/assets/9053d34d-0df0-4847-866b-f89667d1fd01" />
<br />
js. files are plain-text files that contain Javascript. 
<br />
<br />
Figure 3: Contents of start-server.js: <br/>
<img width="574" height="172" alt="image" src="https://github.com/user-attachments/assets/f397b6f9-ce6b-4afc-b22d-7f2f53d1c038" />
<br />
I used the command vi start-server.js to check the contents of the file. The command, var pkg = require('/usr/local/lib/node_modules/hftp');, makes sure that the hftp Node.js module from that file path is assigned to the variable pkg. Node.js allows us to run Javascript inside our terminal, which means we are able to run executables like attack.js and start-server.js. The overall purpose of this command is to ensure our test ftp server will work correctly once we run it. 
<br />
<br />
Figure 4: Starting a static file server:  <br/>
<img width="472" height="163" alt="image" src="https://github.com/user-attachments/assets/33b4fba5-2ee5-4493-a2e8-f80c317d46a5" />
<br />
For testing purposes we didn’t create a fully functioning ftp server. Instead, we spun up a lightweight static file server and configured it to behave like an ftp server. It shares files over HTTP and uses node.js to execute Javascript in our terminal.
<br />
<br />
Configuring attack.sh: <br/>
<br />
<br />
Figure 5: Configuring File Permissions: <br/>
<img width="453" height="154" alt="image" src="https://github.com/user-attachments/assets/604b662f-925f-4232-bcfe-1926beeb92a2" />
<br />
I used chmod +x attack.sh to make attack.sh executable for users, groups, and others. This allows us to execute the file after the required bash script is written. 
<br />
<br />
Figure 6: Writing bash script, in VIM, to execute a director traversal attack:  <br/>
<img width="462" height="475" alt="image" src="https://github.com/user-attachments/assets/a22eda87-9698-4b5f-9e41-798e1506ba57" />
<br />
Node /home/codepath/ftp_folder/scripts/start-server.js makes sure that our test ftp server is spun up before other commands are executed.  Each “ATTACK_PATH” variable is assigned to a .txt file from each directory we want to target. Additionally, node is used again to envoke the attack.js file to target the file path specified in the corresponding variable.  
<br />
<br />
Figure 7: Results of the bash script:  <br/>
<img width="640" height="205" alt="image" src="https://github.com/user-attachments/assets/8cef3664-f678-4bc9-8ea7-bb82feb7b864" />
<br />
<br />
Troubleshooting: <br/>
<br />
<br />
Figure 8: Incorrect output after executing attack.sh: <br/>
<img width="640" height="205" alt="image" src="https://github.com/user-attachments/assets/7d43b66f-33a4-4639-ace7-79cf290bd52c" />
<br />
I used chmod +x attack.sh to make attack.sh executable for users, groups, and others. This allows us to execute the file after the required bash script is written. 
<br />
<br />
</p>

