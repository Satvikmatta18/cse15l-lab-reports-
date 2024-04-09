# Lab Report 1


## `Cd`
## Command with no arguements
 ![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/20fb4c5e-226b-4af6-a899-dd1954ea196a) 
- **Command:** `cd`
- **Working Directory:** `/home`
- **Explanation:** Running `cd` with no arguments does not change the current working directory, so it remains as `/home`.
   
## Command with a path to a directory as an argument.

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/86f5510f-ab3f-426f-966d-b125bceb99b2)

- **Command:** `cd lecture1`
- **Working Directory:** The command was run in the `/home` directory after it changed to `/home/lecture1`.
- **Explanation:** This command changes the current working directory to `lecture1`. The `cd` command will return to the home directory without any arguments. For example, if `cd` is run in another directory without any argument, it will move back to home.
   
## Command with a path to a file as an argument

 ![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/b801b828-b1a6-4c29-877c-a019c372178b)
- **Command:** `cd lecture1/messages/en-us.txt`
- **Working Directory:** The command was run in the `/home/lecture` directory then it was changed to `/home/lecture1/messages`.
- **Explanation:** This is an error because `cd` is used to change directories, not open files. It’s not possible to change the working directory to a file.


## `ls` 
## Command with no arguements

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/cd70f0f5-ca27-471b-b338-cdf5659d6b92)
- **Command:** `ls`
- **Working Directory:** `/home`
- **Explanation:** This command lists the files and directories in the current working directory `/home`.
  
## Command with a path to a directory as an argument.

 ![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/764ac6c6-4c3b-4a25-8340-6a412d15b86f)

- **Command:** `ls lecture1`
- **Working Directory:** The command was run in the `/home` directory.
- **Explanation:** This command lists the files and directories in the specified directory `lecture1`.
     
## Command with a path to a file as an argument

 ![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/e98bfba1-0902-4a2e-ae0b-4b52d683336c)
 
- **Command:** `ls messages/en-us.txt`
- **Working Directory:** The command was run in the `/home` directory.
- **Explanation:** This command lists the location that the file is in, as it displays `lecture1/messages/en-us.txt`.

## `Cat` 


## Command with no arguements

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/f0f573fb-84e5-44b2-9710-d462f62ab3fc)

- **Command:** `cat`
- **Working Directory:** `/home`
- **Explanation:** This command waits for user input from the keyboard. It does not display any file content until you start typing or provide input. If I print anything it will be printed out again.


    
## Command with a path to a directory as an argument.

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/392831b8-6ee6-4057-a973-3301a9a4cacd)
- **Command:** `cat Lecture1`
- **Working Directory:** `/home`
- **Explanation:** This is an error because `cat` is used to display the contents of files, not directories. You cannot use `cat` to display the contents of a directory.

   
## Command with a path to a file as an argument

 ![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/b35c5abc-e2d8-49ec-85ec-90f7521a629d)
- **Command:** `cat messages/en-us.txt`
- **Working Directory:** `/home`
- **Explanation:** This command displays the contents of the file `en-us.txt`. "Hello World!" is displaued.
