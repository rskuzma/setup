Credit to @ieshaw for this template. Some personal tweaks



# Lightsail_Utils
Notes and utilities for spinning up AWS Lightsail instances. 
These are written for a fresh Lightsail linux instance.

## SSH in to your instance

```
ssh -i KEY_LOCATION ec2-user@PUBLIC_IP
```

## Git

Ensure git is installed

```
sudo yum install git -y
```

Then clone this repo

```
git clone https://github.com/rskuzma/setup.git
```

If you want to store your credentials (be careful, stroed as plain text) run this command

```
git config --global credential.helper store
git push 
```

The push command will ask for your credentials, but now they will be stored.

To pull down a local copy of a remote non-master branch to work on

```
git checkout --track origin/branch_name
```

## Python

To install Python 3.6 (needed for fastai)

```
sudo yum install -y python36u python36u-libs python36u-devel python36u-pipsudo pip install --upgrade pip
``` 

## Requirements

Typical installs (note to self -- make bash script)
Also, re-check this works for fastai

```
python36 -m venv env
source env/bin/activate
sudo yum install -y gcc
pip install git+https://github.com/fastai/fastai.git
pip install numpy sklearn pandas seaborn jupyter torch
pip install fastai
```




## Jupyter Notebook

Praise goes to @rskuzma for figuring this out

1. Ssh into lightsail instance using light sail privatekey 

2. `$ jupyter notebook --no-browser --port=8888 `

3. Open a new terminal 

4. `ssh -i /PATH/TO/KEY/thisIsmyKey.pem -L 8000:localhost:8888 ec2-user@PUBLIC_IP_HERE` 

5. If you get a “ WARNING: UNPROTECTED PRIVATE KEY FILE!” Then run this command `chmod 400 path_to_private_key.pem` 

6. Go to localhost:8000 in browser 

7. You’ll be at a jupyter notebook page requesting a token/login 

8. In your ssh window that’s now on your lights tail instance 

9. type `$ jupyter notebook list `

10. Copy the part behind `token=` 

11. Paste that token into the jupyter notebook login page 

12. Make a password and save it to your password manager 
