```
#include <bits/stdc++.h>
using namespace std;
int N,M,A,B;
vector <int> adj[32001];
vector <int> degree(32001);
priority_queue <int> pq;

int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cout.tie(0);
    cin>>N>>M;
    for(int i=0;i<M;i++)
    {
        cin>>A>>B;
        adj[A].push_back(B);
        degree[B]++;
    }
    for(int i=1;i<=N;i++){
        if(!degree[i]) pq.push(-i);
    }
    while(!pq.empty())
    {
        int p = -pq.top();
        pq.pop();
        cout<<p<<" ";
        for(int i=0;i<adj[p].size();i++)
        {
            degree[adj[p][i]]--;
            if(!degree[adj[p][i]])
                pq.push(-adj[p][i]);
        }
    }
    return 0;
}

```