
all: build run

build:
  nvidia-docker build --rm -t base $$(readlink -f $$(dirname $$0))
  
run:
  image=base:latest; \
  docker images $image; \
  nvidia-docker run -it --rm --privileged \
	  -h undisclosed-$(hostname|sed -e 's/ubuntu-//') \
	  -v /tmp/.X11-unix:/tmp/.X11-unix \
	  -e DISPLAY=$DISPLAY \
	  -e "PASSWORD=none" \
	  -e "USER_HTTP=1" $image "$@" 
## [ "$sshx" = "true" ] && kill %1 # kill backgrounded socat
