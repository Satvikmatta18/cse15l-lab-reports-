# LAB REPORT 4

## Step 4: Log into ieng6
- **Screenshot:**
  ![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/60e3f600-2db5-42e8-8afc-45451ec93aba)
- **Keys pressed:** `ssh <username>@ieng6.ucsd.edu<enter>`

## Step 5: Run vimtutor
- **Screenshot:**
  ![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/6159fbc7-9903-4810-8767-74a7ad1ea7a0)
- **Keys pressed:** `vimtutor<enter>`

## Step 6: Clone the repository
- **Screenshot:**
  ![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/0674f517-0e64-4539-ae34-c335d8963420)
- **Keys pressed:** `git clone https://github.com/ucsd-cse15l-s24/lab7<enter>`

## Step 7: Open the file in Vim and make the edit
- **Screenshot:**
  ![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/19d8c4e6-9802-4d2c-981a-4de73c5f498d)
- **Keys pressed:** 
  - `cd lab7<enter>`
  - `vim ListExamples.java<enter>`
  - `/index1<enter>`
  - `n` (to navigate to the next occurrence if needed)
  - `cwindex2<esc>`
  - `:wq<enter>`
  
  **Explanation:**
  - First, I used the Vim command to access `ListExamples.java`. 
  - Then, I used the `/index1<enter>` command to search for `index1`.
  - Navigated to the next occurrence with `n`.
  - Changed `index1` to `index2` using `cwindex2<esc>`.
  - Finally, I saved and exited Vim with `:wq<enter>`.

## Step 8: Run the tests to ensure the fix works
- **Screenshot:**
  ![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/9000ff1b-74bd-4ae5-ae62-d87c950ebc00)
- **Keys pressed:** `./run_tests.sh<enter>`

## Step 9: Commit and push the changes
- **Screenshot:**
  ![image](https://github.com/Satvikmatta18/cse15l-lab-reports/assets/106504471/71a931b2-3561-477a-a9ef-1ce5aa4ae856)
- **Keys pressed:**
  - `git add ListExamples.java<enter>`
  - `git commit -m "Fixed index1 to index2"<enter>`
  - `git push<enter>`
