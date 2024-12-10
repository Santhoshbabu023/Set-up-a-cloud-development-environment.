# Set-up-a-cloud-development-environment.

This project provides a step-by-step guide to setting up and working with a cloud development environment using AWS services. It demonstrates how to use **Amazon SageMaker Studio**, **Cloud9**, **GitLab**, **S3**, and **EC2** to manage and push Python code. The lab includes debugging code, setting up repositories, working with S3 for file storage, and pushing changes to a GitLab self-managed server on Amazon EC2.

## Tools and Services Used

- **Amazon SageMaker Studio**: An integrated development environment (IDE) for data science and machine learning workflows.
- **AWS Cloud9**: A cloud-based IDE for writing, running, and debugging code.
- **GitLab**: A self-managed Git repository to store and version control code.
- **Amazon S3**: Object storage service to store files.
- **Amazon EC2**: Virtual machines to host GitLab and other services.
- **AWS CLI**: Command-line interface to interact with AWS services.

## Prerequisites

Before starting, ensure you have access to the following AWS services:
- **Amazon SageMaker**
- **AWS CloudFormation**
- **AWS CLI**
- **GitLab (Self-managed) on EC2**
- **S3 Bucket** for file storage

### Steps to Set Up and Complete the Lab

1. **Launch CloudFormation Stack**:
   - In the AWS Management Console, search for **CloudFormation** and find the stack named `LabStack-*`.
   - Copy the `GitLabInstancePassword` and `GitLabInstanceURL` values from the **Outputs** tab.

2. **Set Up GitLab**:
   - Open a browser tab, paste the `GitLabInstanceURL`, and log in using the `root` username and the copied `GitLabInstancePassword`.
   - Create a new GitLab project named `dev_app`.

3. **Clone GitLab Repository**:
   - In your GitLab project, copy the repository URL.
   - Clone the repository to your local development environment using the `git clone` command.

4. **Set Up Amazon SageMaker Studio**:
   - Navigate to **Amazon SageMaker Studio** in the AWS Management Console.
   - Open the **Code Editor** in SageMaker Studio.

5. **Create and Run Python Code**:
   - In SageMaker Studio, create a new Python file named `first.py`.
   - Add the code `print('First code in Code Editor')` and save it.
   - Run the code and review the output in the terminal.

6. **Debug Python Code**:
   - Open the `hello.py` file, set a breakpoint, and use the **Run and Debug** feature to step through the code.
   - Inspect the variables and execution flow during the debugging process.

7. **Create an S3 Bucket**:
   - Use AWS CLI to create an S3 bucket using the command:
     ```bash
     aws s3 mb s3://your-bucket-name
     ```
   - Update the `hello.py` file to use this S3 bucket for storing files.

8. **Upload Files to S3**:
   - Run the following command in the terminal to copy the Python file to your S3 bucket:
     ```bash
     aws s3 cp first.py s3://your-bucket-name
     ```
   - List the objects in the bucket to confirm the file upload.

9. **Set Up Git and Commit Changes**:
   - Initialize a Git repository and commit your code changes:
     ```bash
     git init
     git add hello.py
     git commit -m "Improved upload message"
     ```

10. **Push Code to GitLab**:
    - Add the GitLab repository URL as a remote and push the changes:
      ```bash
      git remote add origin <GIT_REPO_URL>
      git push --set-upstream origin main
      ```
    - Provide the GitLab credentials when prompted.

11. **Validate Solution**:
    - Go back to the GitLab repository page, refresh it, and verify that the `hello.py` file has been pushed successfully.

## DIY: Add Missing Code to Upload File Function

1. Check the **S3 uploading files** tutorial URL to get the missing code for the `upload_file()` function.
2. Copy the code and replace the existing `upload_file()` function in `hello.py`.
3. Save and run the updated code.
4. Confirm successful file upload by listing the contents of the S3 bucket.
5. Commit and push the changes to GitLab.

## Conclusion

This lab demonstrates how to:
- Set up a cloud development environment using AWS SageMaker Studio, Cloud9, and GitLab.
- Debug Python code in an IDE.
- Use AWS CLI to interact with S3 and EC2.
- Version control code using GitLab and push changes to a remote repository.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
