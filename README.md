#include<stdio.h> 
 
int main() 
{ 
 
  int i,j,n,time,remain,flag=0,tq; 
  int wt=0,tat=0,at[10],bt[10],rt[10]; 
  printf("Enter Total p1:\t "); 
  scanf("%d",&n); 
  remain=n; 
  for(i=0;i<n;i++) 
  { 
    printf("Enter Arrival Time and Burst Time for p1 p1 Number %d :",i+1); 
    scanf("%d",&at[i]); 
    scanf("%d",&bt[i]); 
    rt[i]=bt[i]; 
  } 
  printf("Enter Time Quantum:\t"); 
  scanf("%d",&tq); 
  printf("\n\np1\t|Turnaround Time|Waiting Time\n\n"); 
  for(time=0,i=0;remain!=0;) 
  { 
    if(rt[i]<=tq && rt[i]>0) 
    { 
      time+=rt[i]; 
      rt[i]=0; 
      flag=1; 
    } 
    else if(rt[i]>0) 
    { 
      rt[i]-=tq; 
      time+=tq; 
    } 
    if(rt[i]==0 && flag==1) 
    { 
      remain--; 
      printf("P[%d]\t|\t%d\t|\t%d\n",i+1,time-at[i],time-at[i]-bt[i]); 
      wt+=time-at[i]-bt[i]; 
      tat+=time-at[i]; 
      flag=0; 
    } 
    if(i==n-1) 
      i=0; 
    else if(at[i+1]<=time) 
      i++; 
    else 
      i=0; 
  } 
  printf("\nAverage Waiting Time= %f\n",wt*1.0/n); 
  printf("Average Turnaround Time = %f",tat*1.0/n); 
  
  return 0; 
}

