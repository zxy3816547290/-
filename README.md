# -#include<stdio.h>
#include<string.h>
bool s=false;
void main()
{
	int i,m=0,n=0,max=0,j=0,k=0;
	char str[100000];
	while(scanf("%s",str)!=EOF)
	{
		for(i=0;str[i]!='\0';i++)
		{
			for(j=i;str[j]!='\0';j++)
			{
	    		if(str[j]=='1')
				{
	     			m++;
				}
	    		if(str[j]=='0')
				{
	      			n++;
				}
	    		if(m==n)
				{
	     			if(max<m)
					{
	    				max=m;
						s=true;
					}
				}
			}
			if(s==true) k=i;
			m=0;n=0;s=false;
		}
		for(i=k;i<k+2*max;i++)
		{
			printf("%c",str[i]);
		}
	}
}
