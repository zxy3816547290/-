#include<stdio.h>
int power2(int a,int b)
{
	if(b==0) return 1;
	else return a*power2(a,b-1);
}

int power1(int a,int b)
{
	int c[100000];
	int i=0,j,p=0;
	while(b>0)
	{
		c[i++]=b%2;
		b/=2;
	}
	for(j=0;j<i;j++)
	{
		p+=power2(2,j)*c[j];
	}
	return power2(a,p);
}

void main()
{
	int a,b,w=0;
	while(scanf("%d%d",&a,&b)!=EOF)
	{
		if(a==0&&b==0) break;
		else if(a>=1&&a<=10000&&b>=1&&b<=10000)
		{
			w=power1(a,b);
			printf("%d",w%1000);
		}
	}
}
