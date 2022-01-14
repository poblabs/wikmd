## Installation
! It's tested on windows and linux based systems.
! Runs on flask server

Clone te repository
```
git clone https://github.com/Linbreux/wikmd.git
```
cd in wikmd
```
cd wikmd
```

Create a virtual env and activate it(optional)
```
virtualenv venv
source venv/bin/activate
```
Install requirements
```
pip install -r requirements.txt
```
Run the wiki
```
export FLASK_APP=wiki.py
flask run --host=0.0.0.0
```

Now visit localhost:5000 and you will see the wiki. With the 0.0.0.0. option it will show up everywhere on the network.

If there are problems feel free to open an github issue you could post the output of wikmd.log to it.

### Linux

Maybe you need to install pandoc on your system before this works.
```
sudo apt-get update && sudo apt-get install pandoc
```

### Windows

You should install [pandoc](https://pandoc.org/installing.html) on your windows system. Now you should be able to start
the server.
```
python wiki.py
```
If the content of the markdown files are not visible you should add the `pandoc-xnos` location to your path variable. Info about [Environment variables](https://www.computerhope.com/issues/ch000549.htm).
```
pip show --files pandoc-xnos
# look for "location" in the output
# example: C:\users\<user>\appdata\local\packages\pythonsoftwarefoundation.python.3.x\localcache\local-packages\python38\site-packages
# change "site-packages" to "Scripts"
# example: C:\Users\<user>\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.x\LocalCache\local-packages\Python38\Scripts
# open your Environment variables and add the changed line to the path
SET PATH=%PATH%;C:\Users\<user>\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.x\LocalCache\local-packages\Python38\Scripts
```


## Docker install

### Build docker
```
docker build -t wiki-md:latest .
```
### Run Docker

You may need to create wiki/data in your homefolder or you can change it if you want another place.

```
sudo docker run -d -p 5000:5000 -v ~/wiki/data:/app/wiki wiki-md
```
If you would like to have the default files inside your instance, you should copy the wiki files to ~/wiki/data in this case.
Also highly recommended is to create a folder 'img' inside 'wiki/'

```
cp wikmd/wiki/* ~/wiki/data/
mkdir ~/wiki/img
```
