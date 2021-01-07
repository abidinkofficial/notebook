# Docker: template, preparing...
## Why did the Docker appear?

Let's assume that we need to run two applications in isolation from each other.

#### Bare-metal

```server = linux + libraries + app #1```

```server = linux + libraries + app #2```

#### Virtualization
  
```server = hypervisor + [ linux + libraries + app #1 ] + [ linux + libraries + app #2 ]```

#### Container (thanks to namespaces and control groups)
  
```server = linux + [ libraries + app #1 ] + [ libraries + app #2 ]```
  
*The containers looks good but they are very difficult to manage.*

#### Docker
  
```server = linux + docker + [ libraries + app #1 ] + [ libraries + app #2 ]```

*The docker layer makes things easier*

## Docker Engine
```Docker Engine``` = ```Docker CLI``` + ```Docker REST API``` + ```Docker Daemon```

## Image and Container
**Image:** Application template

**Container:** Running application instance from the image

```Application Image``` -> ```Running Application Container #1```, ```Running Application Container #2```, ```...```
