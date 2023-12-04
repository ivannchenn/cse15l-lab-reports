**Lab Report 4**
---

Step 4: Log into ieng6  
`<up><up><enter>`  
<img width="486" alt="Screenshot 2023-11-19 at 5 45 55 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/0235a4f5-0d48-4040-b274-9a492c2ce5d2">  
The command `ssh cs15lfa23hq@ieng6.ucsd.edu` was 2 commands up in the history, so I used the up arrows twice and entered to log in

Step 5: Clone your fork of the repository from your Github account (using the SSH URL)  
`<up><up><up><up><enter>`  
<img width="548" alt="Screenshot 2023-11-19 at 5 49 49 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/668806cc-cdc7-47a1-9dc6-5e34bf738864">  
The command was 4 commands up in my command history so I used the up arrows four times to clone the forked repository using the SSH URL. 

Step 6: Run the tests, demonstrating that they fail  
`<c><d><space><lab7><up><up><up><up><up><up><up><enter>`  
<img width="608" alt="Screenshot 2023-11-19 at 5 54 21 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/28aeabf1-3f08-4f4b-ad91-668ee7dcb637">  
I first had to change the directory into `lab7`. Then the `bash test.sh` command was 7 commands up frm the history.

Step 7: Edit the code file to fix the failing test  
`<up><up><up><up><up><up><up><up><up><up><up><up><up><up><enter>` open vim  
`/index1 <enter><N><e><x><i><2> <esc> <:><w><q>`  
<img width="711" alt="Screenshot 2023-11-19 at 6 03 42 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/99052bae-87d8-4b78-87a9-691be0507135">  
The the command to get into vim was 14 commands up in the history, so I had to press the up arrow 14 times to open vim. Then instead of pressing the down arrow, searching for `/index1` was
a quicker way. After changing the `1` to a `2` by pressing `i`, `delete`, `2`, and then `esc` to exit out of INSERT mode, `:wq` saves the file and exits vim
  
Step 8: Run the tests, demonstrating that they now succeed  
`<up><up><enter>`  
<img width="404" alt="Screenshot 2023-11-19 at 6 04 45 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/7633e4e2-1ed9-4086-b33d-986a57f7049c">  
The command `bash test.sh` was only 2 commands up, so I only had to press the up arrow twice and enter  
  
Step 9: Commit and push the resulting change to your Github account (you can pick any commit message!)  
```
git add ListExamples.java  <enter>
git commit -m "commit"  <enter>
git push origin main  <enter>
```
<img width="602" alt="Screenshot 2023-12-03 at 4 04 27 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/5b71b436-46c5-41bb-a9b5-e1e5550ba034">

These commands didn't show up in my history so I had to type them out. Took 70 key presses all together.

