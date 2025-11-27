# sabnzbd-with-pipelining
SABnzbd with pipelining: more speed, less resources

Just using the work of https://github.com/mnightingale/sabnzbd/tree/feature/pipelining


Based on https://github.com/sabnzbd/sabnzbd/pull/3199#issuecomment-3557452806

# Build

```
docker build --no-cache -t sanderjo/sabnzbd-pipelining .
```

# Run

```
docker run -p 8080:8080 sanderjo/sabnzbd-pipelining
```

or, with config saving:

```
mkdir  ~/config-sabnzbd-pipelining

docker run -p 8080:8080 -v ~/config-sabnzbd-pipelining/:/config/ sanderjo/sabnzbd-pipelining
```