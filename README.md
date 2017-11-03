If your AWS account has "must MFA" access then typically you can't do
much from the CLI until you get temporary credentials.

`get-aws-creds` - This is the main script that will talk to the endpoints,
discover your account, what MFA token is assigned, request the credentials
and allow them to be exported.  Typically you would do something like

    eval $(AWS_PROFILE=myprofile get-aws-creds)

`getaws` - This is a simple function that unsets the main AWS variables
and then calls the `eval` command

    getaws myprofile

`clearaws` - Just unsets the main AWS variables


EXAMPLE

    % getaws gcsf
    You are: sweharris
    Your MFA device is: arn:aws:iam::123456789012:mfa/sweharris
    Enter your MFA code now: 299255
    Keys valid until 2017-11-04T02:12:13Z
