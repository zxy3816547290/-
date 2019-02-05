#include<stdio.h>
#include<string.h>
struct biginteger{
	int digit[1000];
	int size;
	void init()
	{
		int i;
		for(i=0;i<1000;i++)
		{
			digit[i]=0;
		}
		size=0;
	}
	void set(char str[])
	{
		init();
		int i,c,t,j=0;
		int l=strlen(str);
		int carry=0;
		for(i=l-1,c=1,t=0;i>=0;i--)
		{
			t+=(str[i]-'0')*c;
			c*=10;
			j++;
			if(j==4||i==0)
			{
				digit[size++]=t;
				t=0;
				c=1;
				j=0;
			}
		}
	}
	void output()
	{
		int i;
		for(i=size-1;i>=0;i--)
		{
			if(i!=size-1) printf("%4d",digit[i]);
			else printf("%d",digit[i]);
		}
	}
	biginteger operator +(const biginteger &a) const
	{
		biginteger r;
		r.init();
		int i,tmp=0;
		int carry=0;
		for(i=0;i<a.size||i<size;i++)
		{
			tmp=digit[i]+a.digit[i]+carry;
			carry=tmp/10000;
			tmp%=10000;
			r.digit[r.size++]=tmp;
		}
		if(carry!=0)
		{
			r.digit[r.size++]=carry;
		}
		return r;
	}
}a,b,c;
char str[1000],str1[1000];
void main()
{
	while(scanf("%s%s",str,str1)!=EOF)
	{
		a.set(str);b.set(str1);
		c=a+b;
		c.output();
	}
}
