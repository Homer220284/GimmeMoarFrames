This project is closed now.
Reason: lack of support by BI



GimmeMoarFrames
===============

a simple, but powerful registry tweak

simple, because it is based on only one registry key and one additional privilege 

powerful, because from now on arma3.exe is mapped in large page memory regions



The **easiest way** to use this advantage is the following (using a tool):

- find out the name of user account, that is used to run arma (start arma, 'taskmanager'->'processes'->'User Name')

- download a little command line tool from here (use 'RAW' button for dl):     
[https://github.com/fred41/GimmeMoarFrames/blob/master/GimmeMoarFrames/LPManager.exe](https://github.com/fred41/GimmeMoarFrames/blob/master/GimmeMoarFrames/LPManager.exe)      

- execute LPManager.exe via 'Run as administrator' and type your useraccountname in the little box (on the right from 'Privilege' button)     

- click 'Privilege' button    

- check 'LP ImageFileMapping Client' (CheckBox)    

- restart your system     

- enjoy     



For more **experienced** users (the manual way):

1. use secpol.msc to set the '**Lock pages in memory**' privileg for the windows useraccount, used to run arma   
('secpol.msc'->'Local Policies'->'User Right Assignment'->'Lock pages in memory' add related user, don't forget to restart once)   

2. use regedit to create/set DWORD value 'UseLargePages' = 1, for key:     
**[HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\arma3.exe]**    
(to simplify switching this tweak on and of, you could use GMF_On.reg and GMF_On.reg from this repository)
 


Additional hint for **real hardliners** (support for server too):

This tweak normally don't work with arma3server.exe (crashes at start).   
If you want to make it work here too, currently the only way is to patch a value in arma3server.exe image file header.   
Install 'Explorer Suite', open CFF explorer with arma3server.exe (right click on binary, 'open with CFF').   
Navigate to 'NT Headers'->'Optional Header'->'DllCharacteristics' and change the value from 8140 to 8100 (or uncheck 'DLL can move').   
Bar in mind, you have to repeat this step with each update, except BIS will fix it in future.   
(obviously, you have to set the related registry value for arma3server.exe too)    

