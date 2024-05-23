# LAB REPORT 4

## Step 4: Log into ieng6

![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/60e3f600-2db5-42e8-8afc-45451ec93aba)

- **Keys pressed:** `ssh <username>@ieng6.ucsd.edu<enter>`
- **Effect:** Logs into the ieng6 server.

## Step 5: Clone your fork of the repository from your Github account

![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/6159fbc7-9903-4810-8767-74a7ad1ea7a0)

- **Keys pressed:** `git clone https://github.com/ucsd-cse15l-s24/lab7<enter>`
- **Effect:** Clones the lab7 repository from GitHub into the current directory.

## Step 6: Run the tests, demonstrating that they fail

![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/0674f517-0e64-4539-ae34-c335d8963420)

- **Keys pressed:** `cd lab7<enter> ./run_tests.sh<enter>`
- **Effect:** Changes the directory to `lab7` and runs the test script, showing that the tests fail.

## Step 7: Edit the code file to fix the failing test

![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/19d8c4e6-9802-4d2c-981a-4de73c5f498d)

- **Keys pressed:**
  - `vim ListExamples.java<enter>`
  - `/index1<enter>`
  - `n`
  - `cwindex2<esc>`
  - `:wq<enter>`
- **Effect:**
  - Opens `ListExamples.java` in Vim.
  - Searches for the term `index1`.
  - Navigates to the next occurrence with `n`.
  - Changes `index1` to `index2` using `cwindex2<esc>`.
  - Saves and exits Vim with `:wq<enter>`.

## Step 8: Run the tests, demonstrating that they now succeed

![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/9000ff1b-74bd-4ae5-ae62-d87c950ebc00)

- **Keys pressed:** `./run_tests.sh<enter>`
- **Effect:** Runs the test script again to ensure the code changes work and the tests pass.

## Step 9: Commit and push the resulting change to your Github account

![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/71a931b2-3561-477a-a9ef-1ce5aa4ae856)

- **Keys pressed:**
  - `git add ListExamples.java<enter>`
  - `git commit -m "Fixed index1 to index2"<enter>`
  - `git push<enter>`
- **Effect:**
  - Adds the changes to git.
  - Commits the changes with a message.
  - Pushes the changes to the remote repository.

### Summary of Commands and Effects

1. **`ssh <username>@ieng6.ucsd.edu<enter>`**: Logs into the ieng6 server.
2. **`git clone https://github.com/ucsd-cse15l-s24/lab7<enter>`**: Clones the lab7 repository from GitHub into the current directory.
3. **`cd lab7<enter> ./run_tests.sh<enter>`**: Changes the directory to `lab7` and runs the test script, showing that the tests fail.
4. **`vim ListExamples.java<enter> /index1<enter> n cwindex2<esc> :wq<enter>`**: Opens `ListExamples.java` in Vim, searches for `index1`, navigates to the next occurrence, changes `index1` to `index2`, and saves and exits Vim.
5. **`./run_tests.sh<enter>`**: Runs the test script again to ensure the code changes work and the tests pass.
6. **`git add ListExamples.java<enter> git commit -m "Fixed index1 to index2"<enter> git push<enter>`**: Adds the changes to git, commits the changes with a message, and pushes the changes to the remote repository.
