# Zuma's Revenge
Zuma's Revenge appears to run acceptably on Windows 10 without any further modification to the compatibility settings, however you will not have access to "Hi-Res Mode" or 3D Acceleration if you do this. In order to get both of these things functioning, use the below instructions:
1. Install and run Zuma's Revenge normally, and create a user. Note this username for future steps
1. open the included [REG.reg](./REG.reg) file using a text editor such as notepad, and change the "LastUser" key on line 8 to the username noted in the previous step. Once saved, open this file using the registry editor to merge it with your own hive
1. go to your installation directory. Typically this will be something like the following:
    ```
    C:\Program Files(x86)\PopCap Games\Zumas Revenge
    ```
1. in this folder should be a file called ```compat.cfg```, which you can open with a text editor. look for a line that says ```function(int) GetAppDefaultRes```. Below that should be a set of braces which coitain logic for the default resolution to boot the game into:
    ```js
    function(int) GetAppDefaultRes
    {
        //bunch of code here
    }
    ```
    You will need to change this function so that it reads like below instead (remove everything between the ```{}``` beforehand). This will make the game ignore the (no longer working) check for 768MB+ of video memory:
    ```js
    function(int) GetAppDefaultRes
    {
        return 1200;
    }
    ```
    ***NOTE: The original code was not added on purpose, I don't know how painful EA is and I have no intention on finding out***
1. You should now be able to run the game using Hi-Res mode and with 3D Acceleration enabled