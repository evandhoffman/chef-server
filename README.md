# chef-server

Used Chef server 11.1.6-1_amd64 on an Ubuntu Trusty 14.04 LTS.

This is a fork of: [c-buisson/chef-server](https://github.com/c-buisson/chef-server) but I took run_chef_server.sh from [tmc/dockerfiles](https://github.com/tmc/dockerfiles/tree/master/chef-server) available on docker registry [base/chef-server](https://registry.hub.docker.com/u/base/chef-server/).

I forked it in order to avoid chef reconfiguring on each container restart. For me it kept reconfiguring endlessly and was temporarily unavailable through web browser. 


## Usage
Use the `--privileged` option or else the shared memory max cannot be set and some of chef server components may not start (rabbitmq server and/or postgresql).  
```
$ docker run --privileged -dti --name chef_server -p 443:443 xmik/chef_server:0.0.2
```

## Build
Build an image using the tag from script/image_metadata.txt. Use rake task:
```ruby
rake chef_server:build
```

Size for chef_server:0.0.2 is 1.003 GB.


