# k-means evaluate

This repository implements the computation to evaluate k-means clustering based on *distance* and *flow*.

## Setting

- Given travel requests
- k-means task
    - build k zones of pick-up/drop-off locations
        - input: d-dimensional geo-locations {xi}
        - output: k-zones {Zi}
    - select the best result in terms of the below 4 metrics
        - select results of minimizing min-intra and maximizing max-inter metrics

## Metrics

- distance-based
    - intra-cluster distance d^{intra}: $\sum_{i=1}^{k} \sum_{x\in Z_i} d(x, c_i)$
    - inter-cluster distance d^{inter}: $\sum_{i=1}^{k} \sum_{j=1}^{k} d(c_i, c_j)$
- flow-based
    - flow $q(x, y, t, tau)$
        - flow from x to y at time t for a given day tau
    - total flow between zones Q(i,j): $\sum_{x\in Z_i, y\in Z_j}\sum_{t=1}^{T}\sum_{\tau=1}^D q(x, y, t, \tau)$
    - intra-flow q^{intra}: $\frac{\sum_{i=1}^k Q(i, i)}{\sum_{i, j} Q(i, j)}$
    - inter-flow q^{inter}: $\frac{\sum_{i\neq j}^k Q(i, j)}{\sum_{i, j} Q(i, j)}$


# Reference

- T.L.K. Liu, P. Krishnakumari, and O. Cats: Exploring Demand Patterns of a Ride-Sourcing Service using Spatial and Temporal Clustering, IEEE Proc. of MT-ITS 2019