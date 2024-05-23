# LAB REPORT 4

## Step 4: Log into ieng6

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/6bc547a7-228e-4c13-95da-f7bd2861154a)

- **Keys pressed:** `ssh <username>@ieng6.ucsd.edu<enter>`
- **Effect:** Logs into the ieng6 server.

## Step 5: Clone your fork of the repository from your Github account

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/d4323a29-305f-4905-bb60-07a8c481095c)

- **Keys pressed:** `git clone https://github.com/ucsd-cse15l-s24/lab7<enter>`
- **Effect:** Clones the lab7 repository from GitHub into the current directory.

## Step 6: Run the tests, demonstrating that they fail

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/19a30738-5931-4578-8c0d-b762bb2d940e)

- **Keys pressed:** `cd lab7<enter> bash Test.sh<enter>`
- **Effect:** Changes the directory to `lab7` and runs the test script, showing that the tests fail.

## Step 7: Edit the code file to fix the failing test and make additional changes

### Editing `ListExamples.java`

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/183f7db8-b6f9-473c-9293-2581dae7ea9e)

- **Keys pressed:**
  - `vim ListExamples.java<enter>`
  - `/index1<enter>`  (searches for the term `index1`)
  - `n` (navigates to the next occurrence)
  - `cwindex2<esc>` (changes `index1` to `index2`)
  - `/sc<enter>` (searches for the term `sc`)
  - `n` (navigates to the next occurrence)
  - `cwchecker<esc>` (changes `sc` to `checker`)
  - `/while<enter>` (searches for the term `while`)
  - `iSystem.out.println("index1: " + index1 + ", index2: " + index2);<esc>` (inserts print statement)
  - `:wq<enter>` (saves and exits Vim)
- **Effect:**
  - Opens `ListExamples.java` in Vim.
  - Searches for the term `index1`.
  - Navigates to the next occurrence with `n`.
  - Changes `index1` to `index2` using `cwindex2<esc>`.
  - Searches for the term `sc`.
  - Navigates to the next occurrence with `n`.
  - Changes `sc` to `checker` using `cwchecker<esc>`.
  - Adds a print statement at the top of the first `while` loop in `merge` to print the values of `index1` and `index2`.
  - Saves and exits Vim with `:wq<enter>`.

### Adding a Test for Merging Two Empty Lists in `ListExamplesTests.java`

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/2da0f329-9bea-4d0c-bc92-ff3662cd90bb)

- **Keys pressed:**
  - `vim ListExamplesTests.java<enter>`
  - `G` (moves to the end of the file)
  - `o` (opens a new line)
  - `@Test(timeout = 500) public void testMergeEmptyLists() { List<String> l1 = new ArrayList<>(); List<String> l2 = new ArrayList<>(); assertTrue("Expected empty list", ListExamples.merge(l1, l2).isEmpty()); }<esc>`
  - `:wq<enter>` (saves and exits Vim)
- **Effect:**
  - Opens `ListExamplesTests.java` in Vim.
  - Moves to the end of the file with `G`.
  - Adds a new test method for merging two empty lists.
  - Saves and exits Vim with `:wq<enter>`.

## Step 8: Run the tests, demonstrating that they now succeed

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/d577c464-0124-4993-9412-2b83d5f83e8e)

- **Keys pressed:** `./run_tests.sh<enter>`
- **Effect:** Runs the test script again to ensure the code changes work and the tests pass.

## Step 9: Commit and push the resulting change to your GitHub account

![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/1f9550f7-4f32-4cc2-a554-7a73bb79ba89)
![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/5d997b88-a13a-4688-a13f-8fd45869cd78)
![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/abf09b75-69cc-43e5-94c9-dc9831962e7c)

- **Keys pressed:**
  - `git add ListExamples.java ListExamplesTests.java<enter>`
  - `git commit -m "Fixed index1 to index2, renamed sc to checker, added print statement, and added test for merge on empty lists"<enter>`
  - `git push<enter>`
- **Effect:**
  - Adds the changes to git.
  - Commits the changes with a message.
  - Pushes the changes to the remote repository.

### Summary of Commands and Effects

1. **`ssh <username>@ieng6.ucsd.edu<enter>`**: Logs into the ieng6 server.
2. **`git clone https://github.com/ucsd-cse15l-s24/lab7<enter>`**: Clones the lab7 repository from GitHub into the current directory.
3. **`cd lab7<enter> ./run_tests.sh<enter>`**: Changes the directory to `lab7` and runs the test script, showing that the tests fail.
4. **`vim ListExamples.java<enter> /index1<enter> n cwindex2<esc> /sc<enter> n cwchecker<esc> /while<enter> iSystem.out.println("index1: " + index1 + ", index2: " + index2);<esc> :wq<enter>`**: Opens `ListExamples.java` in Vim, searches for `index1`, navigates to the next occurrence, changes `index1` to `index2`, searches for `sc`, navigates to the next occurrence, changes `sc` to `checker`, adds a print statement at the top of the first `while` loop in `merge`, and saves and exits Vim.
5. **`vim ListExamplesTests.java<enter> G o@Test(timeout = 500) public void testMergeEmptyLists() { List<String> l1 = new ArrayList<>(); List<String> l2 = new ArrayList<>(); assertTrue("Expected empty list", ListExamples.merge(l1, l2).isEmpty()); }<esc> :wq<enter>`**: Opens `ListExamplesTests.java` in Vim, moves to the end of the file, adds a new test method for merging two empty lists, and saves and exits Vim.
6. **`./run_tests.sh<enter>`**: Runs the test script again to ensure the code changes work and the tests pass.
7. **`git add ListExamples.java ListExamplesTests.java<enter> git commit -m "Fixed index1 to index2, renamed sc to checker, added print statement, and added test for merge on empty lists"<enter> git push<enter>`**: Adds the changes to git, commits the changes with a message, and pushes the changes to the remote repository.
