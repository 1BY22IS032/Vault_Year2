<!--markdownlint-disable MD033-->
<!--markdownlint-disable MD025-->

# Greedy Method

## Dijkstra's Algorithm

### Algorithm

```algo
function Dijkstra(G,S){
    for each node in G
        distance[node] <- INTMAX
        previous[node] <- NULL
    distance[S] <- 0
    Q <- set of all nodes in G

    While Q is not empty
        u <- node in Q with min distance[u]
        remove u from Q

        if distance[u] := INTMAX
            break

        for each neighbor v of u
            alt <- distance[u] + length(u,v)
            if alt < distance[v]
                distance[v] <- alt
                previous[v] <- u

    return distance , previous
}
```
