# Assignment1
#include <sys/types.h>#include <stdio.h>#include <unistd.h>#include <sys/wait.h>
int main (){    int pid;    int sum1=0,sum2=0,sum3=0,sum4=0;     int array[100],i;    for(i=0;i<100;i++)          array[i]=i+1;    pid = fork ();
    if (pid < 0)    {        printf ("Fork Failed\n");        return -1;    }    else if (pid == 0)    {      int cpid2; cpid2=fork(); if(cpid2<0) { printf ("Fork Failed\n"); }    else if(cpid2==0) {  int cpid3;  cpid3=fork();  if(cpid3<0)  {   printf ("Fork Failed\n");          }  else if(cpid3==0)  {    int i;       for(i=0;i<25;i++)       sum4+=array[i];  }  else  {    int i;   for(i=25;i<50;i++)       sum4+=array[i];  }
 } else {   int i;  for(i=50;i<75;i++)       sum4+=array[i]; }     }    else     {        //printf("I'm the parent\n");        int i; for(i=75;i<100;i++)     sum4+=array[i];     }
    printf("I'm pid %d\n",sum1+sum2+sum3+sum4);
    return 0;}
