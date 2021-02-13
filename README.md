# web-application-on-AWS
Deploying the Go Web APP to EC2 Instance:

Installation Of Linux And Go :

Here, I have installed Ubuntu 16.04 LTS. Go here After installing Ubuntu, open terminal by pressing Ctrl+T and enter a command
$sudo apt-get update
$sudo apt-get -y upgrade
Then, download the latest version of Go by
$sudo curl -o https://storage.googleapis.com/golang/go1.8.3.linux-amd64.tar.gz
Next I used tar to unpack the package and then moved it to /usr/local
$sudo tar -xvf go1.8.3.linux-amd64.tar.gz
$sudo mv go /usr/local

Now , Go package is in /usr/local folder and it is now in $PATH for Linux.
I changed the .profile for Go Set up 
export GOROOT=/usr/local/go [Installation path]
export GOPATH=$HOME/GoDemo [Workspace path]
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH [bin directory of both]
$sudo nano ~/.profile

Deploying the Binary :

As I have already installed Go on the system. 
I’ve created go application in my workspace at below path
S3UploaderApp/main.go
Now we’ll build a binary.
So in order to build the binary using Linux environment, 
$go env
$GOOS=linux GOARCH=amd64 go build -o main main.go

The specifications of the command are as given below.
$scp(secure copy) -i ~/.ssh/go.pem(PEM file path) S3DownloaderApp ec2-user@publicDNS:
So, the command will be like this for me,
$scp -i ~/.ssh/go.pem GoDemoProject ec2-user@XXXX:

ec2-user@ip-XXXX:sudo chmod 700 S3UploaderApp

the application can be run by specifying a name
ec2-user@ip-XXXX:$sudo ./ S3UploaderApp


The application should be allowing to upload the file content and then provide the response object with presigned url.
The idea of presigned url is to maintain the auth automatically for a particular time duration.
We can also make it alive for n number of days.






