# CSE15l-lab1-report-Terry
## 1.Command cd
### **Using cd without arguments**
![Image](cd_no_args.jpg)
The working directory when the command was run is `home` directory.<br>
When you using command `cd` without arguments, it defaults to changing the current working directory to `home` directory.<br>
*It is not an error* <br>

### **Using cd with a path to a directory as an argument**
![Image](WechatIMG1141.jpg)
The working directory when the command was run is `home`.<br>
The output means that you have successfully using command `cd` to change directory to directory `lecture1`.<br>
*It is not an error*<br>

### **Using cd with a path to a file as an argument**
![Image](WechatIMG1166.jpg)
The workign directoty when the command was run is `~/lecture1/message`.<br>
The output means that we were trying to change directory to a file which we can not. The terminal was telling us that `en-us.txt` was a file.<br>
*It is an error*

## 2.Command ls
### Using ls without argumnets
![Image](ls_no_args.jpg)
The working directory when the command was run is `home` directory.<br>
The ouptut means that we used command ls to list all the contents of our `home` directory.<br>
*It is not an error*

### Using ls with a path to a directory as an argument
![Image](ls_di.jpg)
The working directory when the command was run is `home` directory.<br>
The output means that we used command ls to list all the contents of directory `lecture1`.<br>
*It is not an error*

### Using ls with a path to a file as an argument
![Image](ls_file.jpg)
The working directory when the command was run is `~/lecture1/message`.<br>
When we using ls with a path to a file as an argument, the command is used to check wether the file is in the current directory. Because the file was actually in the directory, the terminal printed its name. <br>
*It is not an error*

## 3.Command cat
### Using cat without arguments
![Image](cat_no_args.jpg)
The output is telling us that `lecture1` is a 
The working directory when the command was run is `home` directory.<br>
When we run cat with no arguments, the command does not terminate; instead, it waits for us to enter something.<br>
*It is not an error*

### Using cat with a path to a directory as an argument
![Image](cat_di.jpg)
The working directory when the command was run is `home` directory.<br>
The output is telling us that `lecture1` is a directory, as we can not concatenate a directory.<br>
*It is an error*

### Using cat with a path to a file as an argument
![Image](cat_flie.jpg)
The workign directory when the command was run is `~/lecture1/message`.<br>
When we use the `cat` command with a path to a file as an argument, it reads the contents of the file and displays them to the terminal.<br>
*It is not an error*
