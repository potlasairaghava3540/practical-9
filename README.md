
#include <iostream>
using namespace std;

int main()
{
    int n = 5;

    int cost[5][5] = {
        {0, 2, 0, 6, 0},
        {2, 0, 3, 8, 5},
        {0, 3, 0, 0, 7},
        {6, 8, 0, 0, 9},
        {0, 5, 7, 9, 0}
    };

    int visited[5] = {0};
    int edges = 0;
    int minCost = 0;

    visited[0] = 1;

    cout << "Edges in Minimum Spanning Tree:\n";

    while (edges < n - 1)
    {
        int min = 999;
        int a = -1, b = -1;

        for (int i = 0; i < n; i++)
        {
            if (visited[i])
            {
                for (int j = 0; j < n; j++)
                {
                    if (!visited[j] && cost[i][j] != 0)
                    {
                        if (cost[i][j] < min)
                        {
                            min = cost[i][j];
                            a = i;
                            b = j;
                        }
                    }
                }
            }
        }

        if (a == -1)
        {
            cout << "Graph is disconnected";
            return 0;
        }

        cout << a << " - " << b
             << " : " << min << endl;

        minCost += min;
        visited[b] = 1;
        edges++;
    }

    cout << "Minimum Cost = " << minCost;

    return 0;
}
