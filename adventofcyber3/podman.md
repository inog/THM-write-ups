# Podman is the new docker

The main different is docker needs a deamon and podman not.

## Install   
`sudo apt install podman`

- nearly the same commands like  
``
podman pull <image>
podman ps
podman ps -a
...
``

save the image to a tar.
`podman save -o aoc.tar public.ecr.aws/h0w1j9u3/grinch-aoc` 

unpack the tar  
`tar xvf aoc.tar`


installing the tool jq. for pretty print jason files
`sudo apt install jq -y`

take a look for the manifest.json file 
`cat manifest.json | jq`


