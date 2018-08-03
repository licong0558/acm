# 欧拉图

```cpp
//7 20
#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
const ll MAXN=1e5+100;
const ll MOD=1e9+7;
const ll INF=1e18;

const ll MAXE=MAXN*10;
struct Edge{
    int from,to,nxt;
}edge[MAXE];
int eidx;
int head[MAXN];
void addedge(int from,int to)
{
    edge[eidx].from=from; edge[eidx].to=to;
    edge[eidx].nxt=head[from]; head[from]=eidx++;
}
void einit()
{
    eidx=0;
    memset(head,-1,sizeof head);
}
int degree[MAXN];
vector<int> ans[MAXN];
int n,m,idxa;
bool vis[MAXE];
bool visp[MAXN];
void init(/* arguments */) {
    einit();
    idxa=0;
    for(int i=0;i<=n;++i)
        ans[i].clear(),visp[i]=0;
    for(int i=0;i<=n;++i)
        degree[i]=0;
    for(int i=0;i<MAXE;++i)
        vis[i]=0;

}
std::vector<int> odd;
void dfso(ll u) {
    visp[u]=1;
    if(degree[u]%2) odd.push_back(u);
    for(ll i=head[u];i!=-1;i=edge[i].nxt){
        ll v=edge[i].to;
        if(visp[v]) continue;
        dfso(v);
    }
}
void dfs(int u) {
    // if(!(deep%1000))
    // printf("de %d\n",deep);
    for(int i=head[u];i!=-1;i=edge[i].nxt){
        int v=edge[i].to;
        if(vis[i/2]) continue;
        vis[i/2]=1;
        dfs(v);
        if(i>=2*m)
            idxa++;
        else {
            // printf("push %lld\n",i/2+1);
            ans[idxa].push_back((i%2?-1:1)*(i/2+1));
        }
    }
}
int main(int argc, char const *argv[]) {
    // freopen("1003.in","r",stdin);
    // freopen("input.txt","r",stdin);
    // freopen("out1.txt","w",stdout);
    while (cin>>n>>m) {
        init();
        for(int i=0;i<m;++i)
        {
            int p1,p2;
            scanf("%d",&p1); scanf("%d",&p2);
            addedge(p1,p2);
            addedge(p2,p1);
            degree[p1]++; degree[p2]++;
        }
        for(ll i=1;i<=n;++i)
        {
            if(!visp[i]&&degree[i])
            {
                odd.clear();
                dfso(i);
                for(ll j=2;j<odd.size();j+=2)
                {
                    addedge(odd[j],odd[j+1]);
                    addedge(odd[j+1],odd[j]);
                }
                dfs(odd.size()?odd[0]:i);
                idxa++;
            }
        }
        printf("%d\n",idxa);
        for(int i=0;i<idxa;++i)
        {
            printf("%d ",ans[i].size());
            for(int j=ans[i].size()-1;j>=0;--j)
                printf(" %d",ans[i][j]);
            puts("");
        }
    }
    return 0;
}
```

