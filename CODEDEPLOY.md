
# Installing the CodeDeploy agent on EC2
```
sudo yum update -y
sudo yum install -y ruby wget
wget https://aws-codedeploy-eu-west-1.s3.eu-west-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status
```


# create a bucket and enable versioning
```
aws s3 mb s3://aws-devops-matt-long --region eu-west-2 --profile personal
aws s3api put-bucket-versioning --bucket aws-devops-matt-long --versioning-configuration Status=Enabled --region eu-west-2 --profile personal
```

# deploy the files into S3 (run from inside directory containing appspec.yml)
```
aws deploy push --application-name MyWebpageDeploy --s3-location s3://aws-devops-matt-long/my-webpage-deploy/app.zip --ignore-hidden-files --region eu-west-2 --profile personal
```