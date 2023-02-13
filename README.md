//dynamic programming
#include<stdio.h>
#include<limits.h>

int minCoins(int coins[],int m,int V)
{
    if(V==0)
    
        return 0;
    
    int result =INT_MAX;
    
    for(int i=0;i<m;i++)
    {
        if(coins[i]<=V)
        {
            int sub_result=minCoins(coins,m,V-coins[i]);
            if(sub_result != INT_MAX && sub_result+1<result)
            {
                result=sub_result+1;
            }
        }
    }
    return result;

}


int main()
{
    int D[50], n, denom;
    printf("enter number of denom you want ");
    scanf("%d", &n);//number of denominations
    printf(" Enter denomination");
    for(denom=0; denom<n; denom++)
        scanf("%d", &D[denom]);
   
   int w;//amount
        printf("enter amount to make coins change:");
        scanf("%d",&w);
    printf("the minimal no. of coin denomination for n is %d",minCoins(D,n, w));
    return 0;
}
