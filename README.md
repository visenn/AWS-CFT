# AWS-CFT
Amazon Web Services - Cloud Formation Templates

The puerpose of this repository is to provide the set of example AWS Cloud Formation templates which allows to build simple secure configurations.

<ol>
  <li><b>IAM-role-assumed-by-user-only-from-allowed-IPaddress</b><br>
    This particular template creates programmatic AWS user Report and AWS role Report. This configuration allows to restrict the access to the role only to the specific IP# (or list of subnets). As soon as AWS account administrator will generate access keys to the Report AWS user created by this profile, he can create profile in the ~/.aws/credentials file for that user like this:
    <pre>
    [Report-profile-MasterAccount]
    aws_access_key_id = <generated AWS user key>
    aws_secret_access_key = <generated AWS user secret key>
    source_profile = Report-profile
    role_arn = arn:aws:iam::MasterAccountID:role/Report
    </pre>
    What is important, the configuration of the Report AWS user created by this template allows him to be also the central AWS user for communication with the similar roles in the other accounts, with the same IP access restrictions.
  </li>
  <li><b>IAM-role-assumed-by-master-account-user</b><br>
  In opposite to the previous template, this template creates only Report role. This template shouldn't be used alone. It should be used only in the AWS multi-account organization where to one AWS account there is deployed template described in the previous point and in all other AWS accounts there will be deployed this template. <br>
  The profile in the credentials file should look like follows:<br>
  <pre>
    [Report-profile-ChildAccount1]
    aws_access_key_id = <generated AWS user key>
    aws_secret_access_key = <generated AWS user secret key>
    source_profile = Report-profile
    role_arn = arn:aws:iam::ChildAccount1ID:role/Report
  </pre>
  What is worth to remember - while ARN of the role required to define this profile is the ARN of the role created by this template, then access_key_id and secret_access_key has to be copied from the MasterAccount environment where user Report was created. 
  </li>
</ol>
