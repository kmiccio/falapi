```
INSTALAR AMBIENTE PRUEBA EN MAC OSX
Instrucciones
http://jonathansoma.com/lede/foundations-2017/classes/more-scraping/selenium/

UBUNTU 16.06 SV

#############
Parte 1 -> INSTALL PYTHON

sudo apt update
sudo apt -y upgrade
sudo apt install -y python3 python3-pip
export LC_ALL=C
sudo pip3 install --upgrade pip
sudo pip3 install --upgrade setuptools
sudo pip3 install pandas bs4 jupyter selenium

#############
Parte 2 -> INSTALL CHROME 

sudo apt install -y libxss1 libappindicator1 libindicator7
sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome*.deb
sudo apt install -y -f

#############
Parte 3 -> INSTALL CHROME HEADLESS

sudo apt install -y unzip
curl -sS chromedriver.storage.googleapis.com/LATEST_RELEASE
	-> Ultima version, reemplazar ultima version en 2.40
sudo wget https://chromedriver.storage.googleapis.com/2.40/chromedriver_linux64.zip
sudo unzip chromedriver_linux64.zip
sudo chmod +x chromedriver
sudo mv -f chromedriver /usr/local/bin/chromedriver
sudo apt install -y xvfb
sudo pip3 install pyvirtualdisplay

#############
Parte 4 -> TEST CHROME HEADLESS

sudo nano test.py
	////////////////////////////////////////
	from pyvirtualdisplay import Display
	from selenium import webdriver

	display = Display(visible=0, size=(800, 600))
	display.start()

	options = webdriver.ChromeOptions()
	options.add_argument('--no-sandbox')

	driver = webdriver.Chrome(chrome_options=options)
	driver.get('http://nytimes.com')
	print(driver.title)
////////////////////////////////////////
python3 test.py

#############
Parte 5 -> INSTALL APACHE

sudo apt-get install apache2 -y
sudo nano /etc/apache2/ports.conf
-> Listen 8080
sudo service apache2 restart
sudo apt-get install php libapache2-mod-php
sudo systemctl restart apache2
sudo nano index.php

###########
Parte 6 -> .htacess
a2enmod rewrite
sudo nano /etc/apache2/apache2.conf
-> Agregar
<FilesMatch "\.(ht|py)$">
        Require all denied
</FilesMatch>
sudo service apache2 restart
```
