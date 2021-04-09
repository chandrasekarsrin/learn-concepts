# Storage drivers
overlay
overlay2

- Storage drivers are used by the container to write data into the writable layer.
- these are dependant on host file system.
- by default a overlay storage will be used and data will be written here.

## DOCKER VOLUMES
- preffered way for the container to write data.
- docker manages this storage and user can manage these with docker CLI/API.
