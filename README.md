# A Notebook on Quickly getting a deep learning base AMI running

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
~~~

then 
~~~python
cat .jupyter/jupyter_server_config.json
~~~
copy the hashed password into the .py file you created above

## Getting the lab launched

~~~
jupyter lab
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
