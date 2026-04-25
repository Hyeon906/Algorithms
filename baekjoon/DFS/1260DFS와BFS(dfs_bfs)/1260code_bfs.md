```
#include <iostream>
#include <algorithm>
#include <string>
#include <stack>
#include <iomanip>
#include <queue>
#include <vector>
using namespace std;

int arr[1001][1001];
int N,M,V;
int chk[1001];
void dfs(int start)
{
    if(chk[start])
        return;
    chk[start] = 1;
    cout<<start<<" ";
    for(int i=1; i<=N; i++)
    {
        if(arr[start][i]&&!chk[i])
            dfs(i);
    }
}
void bfs(int start)
{
    queue <int> q;
    q.push(start);
    chk[start]=1;
    while(q.size())
    {
        int sv = q.front();
        cout<<sv<<" ";
        q.pop();
        for(int i=1; i<=N; i++)
        {
            if(arr[sv][i]&&!chk[i])
            {
                q.push(i);
                chk[i]=1;
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
    for(int i=0; i<M; i++)
    {
        cin>>a>>b;
        arr[a][b]=1;
        arr[b][a]=1;
    }
    dfs(V);
    for(int i=1; i<=N; i++)
        chk[i]=0;
    cout<<endl;
    bfs(V);
    cout<<endl;
}

```