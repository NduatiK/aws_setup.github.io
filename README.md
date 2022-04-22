# A Notebook on Quickly getting a deep learning base AMI running

# TODO
- [ ] Look into using a environment file for all of this 
```yaml
# ./environment.yml
# To use:
#   $ conda env create -f environment.yml
#   $ conda activate d2l
name: d2l
dependencies:
  - python=3.9
  - pip
  - pip:
    - d2l==0.17.0
    - torch==1.8.1
    - torchvision==0.9.1

```

## First of all, getting miniconda installed

~~~shell
ssh -i '.path/to/key' ubuntu@<ip>
~~~

~~~shell
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && chmod u+x Miniconda3-latest-Linux-x86_64.sh && ./Miniconda3-latest-Linux-x86_64.sh  && source .bashrc
~~~

~~~shell
conda install -y pytorch torchvision torchaudio cudatoolkit pandas scikit-learn matplotlib tqdm seaborn tensorboard -c pytorch 
~~~

~~~python
conda install -c conda-forge jupyterlab
~~~
~~~python
conda clean -a
~~~


server-configurations:

~~~python
touch .jupyter/jupyter_server_config.py
~~~

~~~python
nano .jupyter/jupyter_server_config.py
~~~

then inside you can add this
~~~python
c.ServerApp.open_browser = False
c.ServerApp.port = 8888 # or any other ports you'd like
c.ServerApp.ip = '*' # bind to any network interface
c.ServerApp.password = 
~~~
then to get the password we 

~~~python
jupyter server password

nohup jupyter lab --no-browser &
~~~

then 
~~~python
cat .jupyter/jupyter_server_config.json
~~~
copy the hashed password into the .py file you created above

## Getting the lab launched

~~~
tmux new-session
tmux new -s mysession
> jupyter lab

Ctrl + b w
Session and Window Preview

Ctrl + b d
Detach from session

tmux ls
Ctrl + b s
Show all sessions

tmux a
Attach to last session

tmux a -t mysession
Attach to a session with the name mysession
~~~

go here 
~~~
:8888/lab
~~~

# Running Tensorboard on aws and access through localhost

You would have installed tensorboardX and tensorboard

~~~
pip install tensorboard
~~~

~~~
pip install tensorboardX
~~~

Then in a local terminal run 

~~~
ssh -i '.\Documents\Other docs\Key\Moayad.pem' -NL 6006:localhost:6006 ubuntu@
~~~
replace the key file if needed and add the public IP address. Then on a browser navigate to 

~~~
http://localhost:6006/
~~~
