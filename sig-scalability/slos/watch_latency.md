## Watch latency SLI details

### User stories
- As an administrator, if Kubernetes is slow, I would like to know if the root
cause of it is slow api-machinery (slow watch) or something farther the path
(lack of network bandwidth, slow or cpu-starved controllers, ...)

### Other notes
- Pretty much all control loops in Kubernetes are watch-based. As a result
slow watch means slow system in general.
- Note that how we measure it silently assumes no clock-skew in case of
cluster with multiple masters.

### TODOs
- Longer term, we would like to provide some guarantees on watch latency
(e.g. 99th percentile of SLI per cluster-day <= Xms). However, we are not
there yet.
