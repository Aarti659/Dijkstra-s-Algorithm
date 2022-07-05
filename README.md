//C++ Program to implement Dijkstra's Algorithm


#include<iostream.h>

#include<climits.h>

using namespace std;

int miniDist(int dist[], bool Tset[]) 
{
    int mini=INT_MAX,ind;
              
    for(int i=0;i<6;i++) 
    {
        if(Tset[i]==false && dist[i]<=mini)      
        {
            mini=dist[i];
            ind=i;
        }
    }
    return ind;
}

void DijkstraAlgo(int graph[6][6],int src)  
{
    int dist[6];                             
    bool Tset[6];
    
     
    for(int i = 0; i<6; i++)
    {
        dist[i] = INT_MAX;
        Tset[i] = false;    
    }
    
    dist[src] = 0;                 
    
    for(int i= 0; i<6; i++)                           
    {
        int m=miniDist(dist,Tset); 
        Tset[m]=true;
        for(int i = 0; i<6; i++)                  
        {
            
            if(!Tset[i] && graph[m][i] && dist[m]!=INT_MAX && dist[m]+graph[m][i]<dist[i])
                dist[i]=dist[m]+graph[m][i];
        }
    }
    cout<<"Vertex\t\tDistance from source vertex"<<endl;
    for(int i = 0; i<6; i++)                      
    { 
        char str=65+i; 
        cout<<str<<"\t\t\t"<<dist[i]<<endl;
    }
}

int main()
{
    int graph[6][6]={
        {0, 1, 2, 0, 0, 0},
        {1, 0, 0, 5, 1, 0},
        {2, 0, 0, 2, 3, 0},
        {0, 5, 2, 0, 2, 2},
        {0, 1, 3, 2, 0, 1},
        {0, 0, 0, 2, 1, 0}};
    DijkstraAlgo(graph,0);
    return 0;                           
}
