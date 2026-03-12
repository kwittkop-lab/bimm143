## basic Unix 

some important file system command 

pwd :   Print working directory 
ls :    list files and folders in current directory 
cs :    change directory 
mkdir : make directory 
rm :    remove directory 
nano :  a very basic text editor that is always avalibe 

my AWS instance 
ssh -i ~/Downloads/bimm143_kw.pem ubuntu@ec2-54-200-100-52.us-west-2.compute.amazonaws.com

To copy from my AWS instance 
scp -i ~/Downloads/bimm143_kw.pem ubuntu@ec2-54-200-100-52.us-west-2.compute.amazonaws.com:~/work/results.tsv .