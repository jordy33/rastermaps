
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

### Know how:


First I learned how standard tiling for EPSG:3857 works. It's nicely explained on http://www.maptiler.org/google-maps-coordinates-tile-bounds-projection/. Key thing is zoom factor (z). At zoom level 0 whole world is one 256x256 tile. Coordinate origin is at the center of the tile (Greenwich at equator), vertical coordinates (y) going up to 20037508.342789244 and down to -20037508.342789244, horizontal coordinates (x) going left to -20037508.342789244 and right to 20037508.342789244. At zoom level 1 there are 4 equal tiles (2x2), at zoom level 2 there are 16 equal tiles (4x4) and so on. Tiles are numbered from upper left corner right and down. Upper left is (0,0), first right is (1,0), first down is (0,1) and so on. Generally at zoom level z there are 2z rows and columns of tiles, tile (2z/2, 2z/2 - 1) has upper left corner at coordinates (0,0). Another nice tutorial on map tiling systems:


```

Zoom 1:  0,0

Zoom2:

  (0,0)           (1,0)

  (0,1)           (1,1)


Zoom3:

(0,0) (1,0) (2,0) (3,0)

(0,1) (1,1) (2,1) (3,1)

(0,2) (1,2) (2,2) (3,2)

(0,3) (1,3) (2,3) (3,3)

```
