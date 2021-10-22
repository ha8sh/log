sudo sysctl -w vm.max_map_count=262144
or
nano /etc/sysctl.conf
vm.max_map_count = 262144
sysctl -p

For development mode, you can use below settings as well -

    environment:
      - discovery.type=single-node
