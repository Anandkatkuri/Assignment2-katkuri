# Assignment2-katkuri
# Anand Katkuri
## Warangal
it is my most **loved** city i like it because of it's **historical** significance.

---

### Directions

1. Go to the MCI, kansas city airport   
2. Board a airbus to RGIA, Hyderabad       
    1. Book a cab to the Warangal city
    2. Visit the historical monuments

* DSLR
* Food
* Power bank

[AboutMe link](AboutMe.md)

---

### Recommended drinks/food

The below table shows the recommended drinks/food, their available location and their purchase value.

| Food Items  |  Location |   Amt(INR) |
|  ---        |   ---     |   ---      |
|  Biryani    | Hyderabad |     200    |   
|             |           |            |
| Coca-cola   |   Hyd     |    35      |
|             |           |            |
| Lassi       |   Kolkata |   25       |
|             |           |            |
| Dosa        |   Banglore|    45      |


---

#### Motivational Quotes
> The best way to predict the future is to invent it - *Einstein*   
> If you want to lift yourself up, lift up someone else - *Hastings*

---

### Graphs Spanning

> A tree is a connected undirected graph with no cycles. It is a spanning tree of a graph G if it spans G (that is, it includes every vertex of G) and is a subgraph of G (every edge in the tree belongs to G). A spanning tree of a connected graph G can also be defined as a maximal set of edges of G that contains no cycle, or as a minimal set of edges that connect all vertices.(<https://en.wikipedia.org/wiki/Spanning_tree>)

```
struct Edge {
    int a, b, cost;
};

int n, m;
vector<Edge> edges;
const int INF = 1000000000;

void solve()
{
    vector<int> d(n);
    vector<int> p(n, -1);
    int x;
    for (int i = 0; i < n; ++i) {
        x = -1;
        for (Edge e : edges) {
            if (d[e.a] + e.cost < d[e.b]) {
                d[e.b] = d[e.a] + e.cost;
                p[e.b] = e.a;
                x = e.b;
            }
        }
    }

    if (x == -1) {
        cout << "No negative cycle found.";
    } else {
        for (int i = 0; i < n; ++i)
            x = p[x];

        vector<int> cycle;
        for (int v = x;; v = p[v]) {
            cycle.push_back(v);
            if (v == x && cycle.size() > 1)
                break;
        }
        reverse(cycle.begin(), cycle.end());

        cout << "Negative cycle: ";
        for (int v : cycle)
            cout << v << ' ';
        cout << endl;
    }
}

```
Link : https://cp-algorithms.com/index.html