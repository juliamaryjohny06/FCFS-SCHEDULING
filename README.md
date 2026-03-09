#include <stdio.h>

int main() {
    int n, i;
    
    scanf("%d",&n);

    char pid[n][10];
    int at[n], bt[n], wt[n], tat[n];
    int start[n], finish[n];

    for(i=0;i<n;i++)
        scanf("%s %d %d",pid[i],&at[i],&bt[i]);

    for(i=0;i<n;i++){
        if(i==0)
            start[i]=at[i];
        else{
            if(finish[i-1]>at[i])
                start[i]=finish[i-1];
            else
                start[i]=at[i];
        }

        wt[i]=start[i]-at[i];
        finish[i]=start[i]+bt[i];
        tat[i]=finish[i]-at[i];
    }

    float total_wt=0,total_tat=0;

    printf("Waiting Time:\n");
    for(i=0;i<n;i++){
        printf("%s %d\n",pid[i],wt[i]);
        total_wt+=wt[i];
    }

    printf("Turnaround Time:\n");
    for(i=0;i<n;i++){
        printf("%s %d\n",pid[i],tat[i]);
        total_tat+=tat[i];
    }

    printf("Average Waiting Time: %.2f\n",total_wt/n);
    printf("Average Turnaround Time: %.2f\n",total_tat/n);

    return 0;
}
