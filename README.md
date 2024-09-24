
# termux-live-server
Learn how to create your own [live-server](https://github.com/tapio/live-server)
using termux, which reloads whenever the file is changed


### Install
    pkg update && pkg upgrade
    pkg install nodejs
    npm i -g live-server


### Test
    pkg install git
    git clone https://github.com/Idontknowbro9194/termux-live-server.git
    cd termux-live-server/localhost/


### Run
    live-server


> To view remotely on another device, instead of `127.0.0.1:8000`
> use your `IP:8000` that can be seen with `ifcongfig` command on `wlan0`
