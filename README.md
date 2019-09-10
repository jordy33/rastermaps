
# Installation

* Launch a powerful AWS EC2 instance. I am using `m4.4xlarge`.
* `ssh` into the instance.
* Install GhostScript and Imagemagick

```
sudo apt-get install ghostscript 
sudo apt-get install imagemagick
```

* Install Git

```
sudo apt-get install git
```

* Check out the project

```
git clone https://github.com/jordy33/rastermaps.git
cd rastermaps
```

# Generating the tiles

* Download the data

Edit Download-data and change the wget with the new pdf

```
./download-data.sh 
```

* Generate the main images


```
./generate-main-images.sh 
```

There are 6 zooming levels

After generating the main files move this files to GPSGate Server

Use the GPStool to generate a map for every zoom level that you wish

Make sure you create a Virtual Directory named Maps that points to the Maps folder.
 
or refresh the Virtual Directory inside IIS.



* Generate the tiles

```
generate-tiles.sh 
```
