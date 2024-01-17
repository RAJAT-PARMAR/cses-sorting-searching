# cses-sorting-searching
CSES three sum solution
//better time complexity than usaco guide solution
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    int n,x;
    cin>>n>>x;
    vector<pair<int,int>>v;
    for(int i=0;i<n;i++)
    {
        int temp;
        cin>>temp;
        v.push_back(make_pair(temp,i+1));
    }
    sort(v.begin(),v.end());
    for(int i=0;i<n;i++)
    {
        int s=i+1;
        int e=n-1;
        while(s<e)
        {
            int target=x-v.at(i).first;
            if(s!=i&&e!=i&&v.at(s).first+v.at(e).first==target)
            {
                cout<<v.at(s).second<<" "<<v.at(e).second<<" "<<v.at(i).second<<endl;
                return 0;
            }
            if(v.at(s).first+v.at(e).first<target)s++;
            else e--;
        }
    }
    cout<<"IMPOSSIBLE"<<endl;
    return 0;
}
