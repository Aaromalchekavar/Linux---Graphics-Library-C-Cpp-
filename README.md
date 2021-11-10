# Linux---Graphics-Library-C-Cpp

[download libgraph]('download.savannah.gnu.org/releases/libgraph/libgraph-1.0.2.tar.gz')




    First add the Universe repository (since some required packages are not available in main repository):

    sudo add-apt-repository universe
    sudo apt-get update

    Second install build-essential and some additional packages:

        For versions prior to 18.04:

        sudo apt-get install libsdl-image1.2 libsdl-image1.2-dev guile-1.8 \
        guile-1.8-dev libsdl1.2debian libart-2.0-dev libaudiofile-dev \
        libesd0-dev libdirectfb-dev libdirectfb-extra libfreetype6-dev \
        libxext-dev x11proto-xext-dev libfreetype6 libaa1 libaa1-dev \
        libslang2-dev libasound2 libasound2-dev build-essential

        For 18.04: From Ubuntu 18.04 guile-2.0 works and libesd0-dev is deprecated. For this you need to add repositories of xenial in sources.list.

        sudo nano /etc/apt/sources.list

        Add these lines:

        deb http://us.archive.ubuntu.com/ubuntu/ xenial main universe
        deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main universe

        Run sudo apt-get update. Then install packages using:

        sudo apt-get install libsdl-image1.2 libsdl-image1.2-dev guile-2.0 \
        guile-2.0-dev libsdl1.2debian libart-2.0-dev libaudiofile-dev \
        libesd0-dev libdirectfb-dev libdirectfb-extra libfreetype6-dev \
        libxext-dev x11proto-xext-dev libfreetype6 libaa1 libaa1-dev \
        libslang2-dev libasound2 libasound2-dev

    Now extract the downloaded libgraph-1.0.2.tar.gz file.

    Go to the extracted folder and run the following command:

    ./configure
    make
    sudo make install
    sudo cp /usr/local/lib/libgraph.* /usr/lib

    Now you can use #include<graphics.h> on Ubuntu and the following line in your program:

    int gd=DETECT,gm; 
    initgraph(&gd,&gm,NULL);

Here is a sample program using graphics.h:

```
/*  demo.c */
#include <graphics.h>

int main()
{
   int gd = DETECT,gm,left=100,top=100,right=200,bottom=200,x= 300,y=150,radius=50;
   initgraph(&gd,&gm,NULL);
   rectangle(left, top, right, bottom);
   circle(x, y, radius);
   bar(left + 300, top, right + 300, bottom);
   line(left - 10, top + 150, left + 410, top + 150);
   ellipse(x, y + 200, 0, 360, 100, 50);
   outtextxy(left + 100, top + 325, "C Graphics Program");

   delay(5000);
   closegraph();
   return 0;
}
```
    To compile it use

    gcc demo.c -o demo -lgraph

    To run type

    ./demo

#

## In Case of GUILE error

```
./configure --disable-guile
sudo make
sudo make install
sudo cp /usr/local/lib/libgraph.* /usr/lib
```
```
sudo mv /usr/include/guile/2.0/* /usr/include/
```
