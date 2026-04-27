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
        for(auto i:adj[p]){
            degree[i]--;
            if(!degree[i])pq.push(-i);
        }
    }
    return 0;
}

```