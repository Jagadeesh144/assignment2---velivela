# assignment2---velivela
# Jagadeesh Velivela 
#### tirupati
Tirupati, an ancient town at the southern end of Andhra Pradesh, is a pilgrim’s paradise. The place is famous for its many Hindu shrines; the most people are called as  **Sri Venkateswara Swamy** or Tirupati Balaji temple. Devotees from different parts of India and abroad visit this temple **Sri Govindaraja Swamy Temple** and near to **Sri Kapliswaraswamy Temple**
the other names of Tirupati is **Kaliyuga Vaikuntha**

---

#### The closest one is SWAGATH HOTEL from Airport
1. Take a free right to the bezz circle
2. Exit Outer Ring Road to NH5 highway 
3. After 20 Kilometers You will enter NH5
4. You can contiue upto 170 Kilometers on NH5
5. When you are approching renuguntla you will be able to see direction to enter mg Outer Ring Road
6. Take the free left when see the directions on the highway to mg Outer ring road.
7. exit the Outer Ring Road on to exit no 20, this will take you to the Airport.

#### Food recommendations for others
 * Gongora biryani
 * Guntur gongora 
   * Guntur Chicken 
     * vijayawada biryani
 * bheemavaram fish   


 ---

 #### Sports Recommendations


The below table indicates the sports activity that I would like to recommend others to participate and which is the best place to try and how much it would cost to by the equipment for the sport activity

|Sport|Location|Equipment Cost|
|:-----:|:--------:|:-----------:|
|Cricket|Chinna Swamy Stadium|$10|
|Volleyball|firozshah Stadium|$30|
|Kabadi|Gachibowli|$40|
|Football|Mumbai Stadium|$50|

---

### Quotes


“You have to grow from the inside out. None can teach you,
none can make you spiritual.
There is no other teacher but your own soul.”
                 -Swami Vivekananda

The function of education is to teach one to think intensively and to think critically. Intelligence plus character - that is the goal of true education.
                -Martin Luther King Jr.


 Life is like riding a bicycle. To keep your balance, you must keep moving.

                    -Albert Einstein

 Kindness in words creates confidence. Kindness in thinking creates profoundness. Kindness in giving creates love.

                    -Lao Tzu

---

### Cycles Code 

we are discussing Finding a Negative cycle in the graphs 
You are given a directed weighted graph  with  vertices and  edges. Find any cycle of negative weight in it, if such a cycle exists.
In another formulation of the problem you have to find all pairs of vertices which have a path of arbitrarily small weight between them.

[Algorithm code description](https://cp-algorithms.com/index.html)

Using Bellman-Ford algorithm
Bellman-Ford algorithm allows you to check whether there exists a cycle of negative weight in the graph, and if it does, find one of these cycles.

The details of the algorithm are described in the article on the Bellman-Ford algorithm. Here we'll describe only its application to this problem.

[Click here to find the algorithm full discription](https://cp-algorithms.com/graph/finding-negative-cycle-in-graph.html)


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



