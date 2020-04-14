# Operating-System-Project
OS-PROJECT-SEC. K18UW-UJJWAL DUBEY-ROLL NO 6-QUESTION NO.-6
Design a scheduling program that is capable of scheduling many processes that comes in at some time interval and are allocated the CPU not more that 10 time units. CPU must schedule processes having short execution time first. CPU is idle for 3 time units and does not entertain any process prior this time. Scheduler must maintain a queue that keeps the order of execution of all the processes. Compute average waiting and turnaround time.


#include<stdio.h>
#include<conio.h>


int main()
{

  int count,i,j,m=0,n,y=0,time,remain=0,min,flag=0;
  int wait_time=0,turn_a_time=0,a_time[10],b_time[10],p[10],z[10];
  float k=0,x=0;
  printf("OPERATING SYSTEM");
  printf("\n\n\t\t** Enter number of Process:  ");
  scanf("%d",&n);
  printf("\n\n\t\t** NOTE : ");
  printf("\n\n\t\t- Arrival time > 2\n");
  printf("\t\t- Burst time < 10.\n\n");
  for(count=0;count<n;count++)
  {
    printf("\n\n\t\t> Enter Details of Process %d ",count+1);
    printf("\n\n\t\tArrival time : ");
    scanf( "%d",&a_time[count]);
    printf("\t\tBurst time : ");
    scanf(" %d",&b_time[count]);
  }

for(i=0;i<n;i++)
{
	if(b_time[i]>10)
	{
		printf("\n\n\t\t-> INVALID Burst TIME it should be less than 10\n");
		getch();
		exit(1);
	}
}
for(i=0;i<n;i++)
{
	if(a_time[i]<3)
	{
		printf("\n\n\t\t-> INVALID Arrival Time it should be greater than 3\n");
		getch();
		exit(1);
	}
}
  printf("\n\n\n\n\t\t Process   Turnaround Time    Waiting Time\n");
  printf("--------------------------------------------\n");
for(i=0;i<n;i++)
{
	m=m+b_time[i];
}
min=m;
time=m;
for(i=0;i<n;i++)
{
	if(a_time[i]<time)
	{
		time=a_time[i];
	}
}
for(i=time;i<=m;i=i+b_time[j])
{
	min=m;
	remain=0;
	flag=0;

	for(count=0;count<n;count++)
	{

		if(a_time[count]<=i)
		{

			if(b_time[count]<min)
			{

				min = b_time[count];
				j=count;
				flag=1;
			}
			remain=1;
		}
	}
	if(flag==1&&remain==1)
	{
		wait_time=i-a_time[j];
		turn_a_time=wait_time+b_time[j];
		printf("  P[%d]     %8d     %12d\n",j+1,turn_a_time,wait_time);
		k=k+wait_time;
		x=x+turn_a_time;

		a_time[j]=m+1;
		p[y]=j+1;
		z[y]=i;
		y++;
	}
}
printf("--------------------------------------------\n");
printf("\n\n\t\t> Average Waiting Time= %.2f\n",k/n);
printf("\t\t> Avg Turnaround Time = %.2f",x/n);
printf("\n\n\n\n\n\t\t**Total time taken by processor to complete all the jobs : %d",m);
printf("\n\n\t\t>> Queue  for order of execution:\n");
printf("\n\t\t- Process		");

for(i=0;i<n;i++)
{
	printf(" P[%d]   ",p[i]);
	if(i==(n-1))
	{
		printf("\n\n\n\n\t\t** End **\n");
	}
}


  return 0;
}


