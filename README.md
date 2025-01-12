# Assignment 0

## Purpose
The purpose of this assignment is to ensure you have the foundational skills required for this course. These include basic familiarity with version control, programming, and containerization. Please make sure that you complete this assignment before the add/drop date or you might struggle to keep up with the class.

## Overview
In this assignment, you will:
1. Clone a repository to your local machine.
2. Install and set up Docker (which is required for all subsequent assignments).
3. Edit a simple C program.
4. Use a Docker container to compile and run the C program.
5. Push a signed commit with your updates to GitHub.

---

## Instructions

### Step 1: Clone the Repository
1. Clone the homework repository to your local machine:
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```
2. Navigate to the `HW0` directory:
   ```bash
   cd HW0
   ```

### Step 2: Install Docker
1. Install Docker by following the instructions for your operating system:
   - [Docker Desktop for Windows/Mac](https://www.docker.com/products/docker-desktop)
   - [Docker Engine for Linux](https://docs.docker.com/engine/install/)
2. Verify the installation:
   ```bash
   docker --version
   ```
   You should see the Docker version printed to the terminal.

### Step 3: Edit the C Program
1. Open `homework0.c` in your preferred text editor.
2. Replace the placeholder email address in the program with your actual email:
   ```c
   const char EMAIL_ADDRESS[] = "your_email@domain.com";
   ```
3. Save your changes.

---

### Step 4: Run the Program in Docker
1. Build the Docker image:
   ```bash
   docker build -t hw0_image .
   ```
   This will compile your program inside a Docker container.
   Error "failed to read dockerfile": Make sure you are in your repository root directory, not '/HW0'!

2. Run the Docker container to execute your program:
   ```bash
   docker run --rm hw0_image
   ```
   You should see the output displaying your email address and a "flag" generated by hashing your email with a salt.

3. If you need to rebuild or destroy a Docker image (for example, after making significant code changes), use the following commands:
   - To remove the Docker image:
     ```bash
     docker rmi hw0_image
     ```
   - To rebuild the image:
     ```bash
     docker build -t hw0_image .
     ```

---

### Step 5: Push a Signed Commit to GitHub
1. Configure Git to sign commits if you haven’t already:
   - Generate a GPG key if you don’t have one, follow the [guide](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key):
     ```bash
     gpg --full-generate-key
     ```
   - Add the key to your GitHub account by following the [GitHub GPG guide](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account).
   - Configure Git to use your key:
     ```bash
     git config --global user.signingkey <your-gpg-key-id>
     git config --global commit.gpgsign true
     ```

2. Stage and commit your changes:
   ```bash
   git add HW0/homework0.c
   git commit -S -m "Updated email address for Homework 0"
   ```

3. Push your changes to GitHub:
   ```bash
   git push origin main
   ```

---

## Salt File and Grading
- **Salt File (`assignment_salt.txt`)**:
  - For testing locally, a `assignment_salt.txt` file is provided with a dummy salt value. You do not need to modify or worry about this file.
  - During grading, a separate salt file will be used to ensure your program works correctly in a different environment.

---

## Validation
1. Verify that your repository on GitHub reflects the updated `homework0.c` file.
2. Confirm that your commit is signed and verified on GitHub (look for the "Verified" badge next to your commit).

---

## Troubleshooting
- **Docker Installation Issues**:
  Refer to the official Docker documentation for troubleshooting installation problems.
- **GPG Signing Issues**:
  Ensure your GPG key is correctly configured and added to GitHub.
- **Compilation Errors**:
  Double-check your syntax in `homework0.c`. Ensure you’ve replaced the placeholder email with your actual email address.
- **Rebuilding Docker Images**:
  If your code changes are not reflected, rebuild the Docker image using:
  ```bash
  docker build -t hw0_image .
  ```

---

## Submission
Your instructor will pull your repository to verify the following:
1. The updated `homework0.c` file with your email address.
2. A signed commit pushed to GitHub.

Make sure everything is correct before the due date. If you encounter issues, reach out to the course staff for assistance.
