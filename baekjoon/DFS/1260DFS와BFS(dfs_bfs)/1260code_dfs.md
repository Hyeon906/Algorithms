```
#include <iostream>
#include <algorithm>
#include <string>
#include <stack>
#include <iomanip>
#include <queue>
#include <vector>
using namespace std;

int graph[1001][1001];
int N,M,V;
int visited[1001];
void dfs(int idx)
{
    if(visited[idx])
        return;
    visited[idx]=1;
    cout<<idx<<" ";
    for(int i=1;i<=N;i++)
    {
        if(graph[idx][i]&&!visited[i])
            dfs(i);
    }
}
void bfs(int idx)
{
    queue <int> q;
    q.push(idx);
    visited[idx]=1;

    while(q.size())
    {
        int cur = q.front();
        cout<<cur<<" ";
        q.pop();
        for(int i=1;i<=N;i++)
        {
            if(graph[cur][i]&&!visited[i])
            {
                q.push(i);
                visited[i]=1;
            }
        }
    }

}
int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cout.tie(0);
    cin>>N>>M>>V;
    int a,b;
    for(int i=1;i<=M;i++)
    {
        cin>>a>>b;
        graph[a][b]=1;
        graph[b][a]=1;
    }
    dfs(V);
    for(int i=1;i<=N;i++)
        visited[i]=0;
    cout<<endl;
    bfs(V);
    cout<<endl;
}

```