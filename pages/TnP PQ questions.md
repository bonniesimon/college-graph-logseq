- Q1
  collapsed:: true
	- World of Kraft is an online multiplayer that simulates the real world war. Your character in the game is Das. Das is assigned the mission to sneak into the enemy camp of the evil antagonist of the game. The enemy camp is deep in the hills. The only way is through the hill tops and assume that the hill path towards the goal can be represented in a plain of x, y. The power of the enemy's defence has a height of "H" and is at a position (xh, yh) is set to detect anything around it unless its vission is blocked by the hill peaks ie if a straight line can't be drawn to the terrain without any intersection (and asssuming the characters height is negligible). He is given the points of terrain change ie, places of transition of slopes and the point of location of the defense mechanism. Help him to find the distance where he has to put his guard high so as to not be detected by the terrorist defense system.
	- Input
		- The first line of the input contains two integers n and h => the number of points of terrain change(including the point where the tower is located) and the tower height.
		- The next n lines contain two integers xi,yi each => the coordinates of the vertices of terrain change. It is guaranteed that xi is less than xi+1 for 1≤i≤n−1.
	- Output
		- The output is a real number containing the total distance your character has to be on high alert. The number displayed in the end should have only 4 floating points.
	- Sample Input
		- 6 10
		      10 40
		      20 10
		      25 30
		      30 15
		      50 15
		      65 30
	- Sample Output
		- 70.4035
	- Explanation
		- Let's start with the general idea of the solution. To solve the problem, we need to iterate over all relief segments and understand, which part the hill range is seen by the defense tower. A hill range point can be hidden from the defense tower by several hills, but it is enough to track only the highest hill. Generally speaking, the relief segments can be processed in any order, bit it would be more convenient to iterate on them backwards — i.e. in the order from the defense tower to the start point. Processing the segments in reversed order will allow to recalculate the highest hill easier. 
		  Let's now discuss implementation details. Formally speaking, there are n
		  relief points pi=(xi,yi) (1≤i≤n) and the defense tower point E=(xn,yn+H). Each relief point defines its own angle αi, which is measured counter-clockwise between positive direction of the OX axis and the (E,pi) vector. Now, having two relief points pi and pj (i<j), it can be said that pi is hidden from the defense tower if αi>αj. When this check is implemented in the solution, to avoid the precision loss, it is recommended to use vector product and analyse its sign to understand the relation of the angles. This check is done in O(1)time. 
		  Being able to understand when a point is hidden from the defense tower by another point, it is possible to calculate, which part of a hill range(pi,pi+1)is seen by the defense tower. First of all let's note, that if the hill rangeleft point pi is hidden by its right point pi+1, then the entire hill rangeis hidden from the defense tower. Now, we have the situation when left hill rangepoint is not hidden from the defense tower by its right point. But the hill rangeor its part can still be hidden by the highest hill (point M), which is a point with minimal angle from all relief points, located to the right of our segment. Here three cases are possible:
		  both pi and pi+1 are hidden by M in this case the entire hill rangeis hidden and we switch to the next segment;
		   
		   both pi and pi+1 are visible by the defense tower (not hidden by the highest hill M) — in this case the entire hill rangeis visible and we should add its length to the answer; 
		   
		   left hill rangepoint pi is visible by the defense tower, but right hill rangepoint pi+1 is hidden by M — in this case we need to find intersection point I of the hill range(pi,pi+1) and the ray (E,M). What is left - add length of (pi,I) hill range to the answer. 
		  It is very convenient to implement hill range and ray intersection in a parametric way, when intersection point I is represented as I=pi+t1∗(pi+1−pi)=E+t2∗(M−E) and then parameters t1 and t2 are found as solutions of linear equation system. 
		  Now, let's conclude the final algorithm: 
		  Iterate over all relief segments from right to left, keeping the highest hill point M 
		  Analyze how left and right points of the current hill rangeare located relatively to each other and point M 
		  Recalculate M taking points of the current segments as candidates for the highest hill. 
		  Total algorithm complexity is O(N).
	- Solution
		-
		  ```
		  #define _USE_MATH_DEFINES
		  #include<cstdio>
		  #include<cmath>
		  using namespace std;
		  int N,H;
		  int x[2<<17],y[2<<17];
		  long long cross(int i,int j)
		  {
		      long long xi=x[i]-x[N-1];
		      long long yi=y[i]-y[N-1]-H;
		      long long xj=x[j]-x[N-1];
		      long long yj=y[j]-y[N-1]-H;
		      return xi*yj-xj*yi;
		  }
		  main()
		  {
		      scanf("%d%d",&N,&H);
		      for(int i=0;i<N;i++)
		      {
		          scanf("%d%d",&x[i],&y[i]);
		      }
		      int mn=N-1;
		      double ans=0;
		      for(int i=N-2;i>=0;i--)
		      {
		          long long t=cross(mn,i);
		          if(t==0)
		          {
		              if(mn==i+1)
		              {
		                  ans+=hypot(x[i]-x[i+1],y[i]-y[i+1]);
		              }
		              mn=i;
		          }
		          else if(t<0)
		          {
		              double theta=atan2(y[N-1]+H-y[mn],x[N-1]-x[mn])-atan2(y[N-1]+H-y[i],x[N-1]-x[i]);
		              double l=hypot(y[N-1]+H-y[i],x[N-1]-x[i]);
		              double alpha=atan2(y[N-1]+H-y[i],x[N-1]-x[i])-atan2(y[i+1]-y[i],x[i+1]-x[i]);
		              ans+=l*sin(theta)/sin(theta+alpha);
		              mn=i;
		          }
		      }
		      printf("%.4lf\n",ans);
		  }
		  ```
- Q2
	- Problem Statement
		- Adam has embarked on a journey to find the origin of the infinite loop of time he is in. Along with his apprendice Noah. They wandered in various realities and timelines.Their journey began in the Winden Caves five days prior to the apocalypse. In the course of their journey their path caused death of numerous people. But they failed as Eva didn't want the origin to be destroyed. To the surprise of Eva, Adam lives in a different reality where he is not killed and with the help of Claudia he makes the bunker wall his travellogue. They wants Jonas to destroy the origin in the next cycle. But Jonas wants a cycle with less death and abomination. Show Jonas the cycle as the apocalypse is just one hour away in both the worlds. Each path causes numerous deaths. The cycle should be such that the end is the begining and the begining is the end. Also tell Jonas the number of unique realities and help him find timelines in the cycle, number of deaths and the reality closest to the begining.
	- Input Format
		- Number of realities Adjacency matrix of the weighted map. N
	- Constraints
		- 0<N<1000
	- Output Format
		- Shortest path from starting reality.(it should end up in starting reality itself). Number of deaths. Reality closest to the beginning.
	- Sample Input
		- 4
		  0
		  1
		  2
		  3
		  4
		  0
		  5
		  6
		  7
		  8
		  0
		  9
		  1
		  2
		  3
		  0
	- Sample Output
		- 1 4 2 3 1
		  17
		  4
	- Explanation
		- Input
		  4- Number of sites.
		  Rest of the input -Adjacency Matrix
		- Output
		  Way of the travel.(Note start with 1 and end with 1) - Number of deaths - Closest reality.
	- Solution
		-
		  ```
		  #include<iostream>
		   
		  using namespace std;
		   
		  int ary[20][20],completed[10],n,cost=0,count=0,m;
		   
		  void takeInput()
		  {
		      int i,j;
		   
		      cin>>n;
		   
		      
		   
		      for(i=0;i < n;i++)
		      {
		          
		          for( j=0;j < n;j++)
		              cin>>ary[i][j];
		   
		          completed[i]=0;
		      }
		   
		  
		  }
		   
		  int least(int c)
		  {
		      int i,nc=999;
		      int min=999,kmin;
		   
		      for(i=0;i < n;i++)
		      {
		          if((ary[c][i]!=0)&&(completed[i]==0))
		              if(ary[c][i]+ary[i][c] < min)
		              {
		                  min=ary[i][0]+ary[c][i];
		                  kmin=ary[c][i];
		                  nc=i;
		              }
		      }
		   
		      if(min!=999)
		          cost+=kmin;
		   
		      return nc;
		  }
		   
		  void mincost(int city)
		  {
		      int ncity;
		   
		      completed[city]=1;
		       count++;
		      cout<<city+1<<" ";
		      ncity=least(city);
		      if(count==2)
		      m=city+1;
		   
		      if(ncity==999)
		      {
		          ncity=0;
		          cout<<ncity+1;
		          cost+=ary[city][ncity];
		   
		          return;
		      }
		   
		      mincost(ncity);
		  }
		   
		  int main()
		  {
		      takeInput();
		   
		      
		      mincost(0); //passing 0 because starting vertex
		   
		      cout<<"\n"<<cost;
		      cout<<"\n"<<m;
		   
		      return 0;
		  }
		  ```
	- Test Cases
		- Input 1
			- 3
			  0
			  3
			  6
			  2
			  0
			  4
			  6
			  9
			  0
		- Output 1
			- 1 2 3 1
			  13
			  2
		- Input 2
			- 2
			  0
			  1
			  1
			  0
		- Output 2
			- 1 2 1
			  2
			  2
		- Input 3
			- 3
			  1
			  2
			  3
			  4
			  5
			  6
			  7
			  8
			  9
		- Output 3
			- 1 2 3 1
			  15
			  2