# AWS-CFT
Amazon Web Services - Cloud Formation Templates

The puerpose of this repository is to provide the set of example AWS Cloud Formation templates which allows to build simple secure configurations.

<ol>
  <li><b>IAM-role-assumed-by-user-only-from-allowed-IPaddress</b><br>
    This particular template creates programmatic AWS user Report and AWS role Report. This configuration allows to restrict the access to the role only to the specific IP# (or list of subnets). As soon as AWS account administrator will generate access keys to the Report AWS user created by this profile, he can create profile in the ~/.aws/credentials file for that user like this:
    <pre>
    [Report-profile]
    aws_access_key_id = <generated key>
    aws_secret_access_key = <generated secret key>
    source_profile = Report-profile
    role_arn = arn:aws:iam::<youAccountID>:role/Report
    </pre>
  </li>
</ol>
