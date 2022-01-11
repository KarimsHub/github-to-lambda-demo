# AWS: Code Deploy from github to AWS

## Steps to follow:
1. Create lambda function AWS Console with Python 3.9
2. Create new Github Repo to host the project
3. Copy Github Repo URL open Terminal and navigate to the directory where you want to save the project.
4. In Directory: git clone + URL of Repo
5. After that cd into project and create lambda_function.py, requirements.txt (if neccessary) to import different libraries and buildspec.yml
6. In buildspec.yml file you have to change the function name to the actual name of the lambda function you´ve created
7. push everything to github using new github token
8. open codebuild in aws console, create a new project and connect to your github repo
9. change Permission of the policy attached to coldbuild with the following json and change the arn aswell:
{
    "Effect": "Allow",
    "Action": [
        "lambda:AddPermission",
        "lambda:RemovePermission",
        "lambda:CreateAlias",
        "lambda:UpdateAlias",
        "lambda:DeleteAlias",
        "lambda:UpdateFunctionCode",
        "lambda:UpdateFunctionConfiguration",
        "lambda:PutFunctionConcurrency",
        "lambda:DeleteFunctionConcurrency",
        "lambda:PublishVersion"
    ],
    "Resource": "arn:aws:lambda:us-east-1:your-aws-account-number:function:your-lambda-function-name"
}