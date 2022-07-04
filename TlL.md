### 6월 3일
#### 알고리즘
- 시분할 알고리즘에 대해 공부함
- 정보처리기사 공부하고 있을 적 잘쓰지 않아 까먹었던 쓰레드에 대해
다시 공부하는 시간을 가짐(알고리즘 짠 걸 변경)
#### 개념공부
- 전자정부프레임워크에 관한 공부시작
#### 느낀 점
- 아직 경험 부족인 건지, 배웠던 언어 별로 사용할 수 있는 게 있고,
없는 게 있는데, 잊고 제작하는 경우가 있다. 예를 들어, 내장 함수를
사용한다면, 사용자 정의 함수를 남발하는 것보다 코드가 짧아질 텐데,
그 부분이 아쉬운 듯하다.

### 6월 4일
#### 알고리즘
- 프로그래머스 배달 문제를 풀었다(디익스트라 알고리즘과 프로이드와샬 알고리즘의 차이)

### 6월 5일
#### 알고리즘
- 프로그래머스 3단계 문제 돌입(1~2단계 전부다 품)

### 6월 6일
#### 알고리즘
- 프로그래머스 3단계 문제를 풀었다.
- 풍선 터트리기 문제
https://programmers.co.kr/learn/courses/30/lessons/68646
````java

class Solution 
{
    public static int solution(int[] a) 
    {
	int answer = 0;

	int l = 1000000000, r = 1000000000;

	for (int i = 0; i < a.length; i++) 
	{
		if (a[i] < l) 
        	{
			answer++;
			l = a[i];
		}
		if (a[a.length - 1 - i] < r) 
        	{
			answer++;
			r = a[a.length - 1 - i];
		}
	}
        
        if (l == r)
        {
            answer -= 1;
        }
			
	return answer;
     }
}

``````

- 조건에 따라 풍선을 터트리는 문제니까. 양쪽에서 터트리돼 조건에서 작은 녀석이 터지도록하면 된다.
- 만약 같을 경우엔 중복 카운트되므로, 하나를 뺴면 완성이다.

#### 2022 - 06 - 08

`````java

class Solution
{
    public int solution(String s)
    {
        char[] chr = s.toCharArray();
        
        // 가장 긴 문자열부터 팰린드롬 검사
        for (int end = s.length(); end > 1; end--) {
            
            // 시작 인덱스
            for (int start = 0; start <= s.length() - end; start++) {
                boolean chk = true;
                
                // 처음부터 문자열 길이의 반틈만큼 문자가 같은지 비교
                for (int i = 0; i < end/2; i++) {
                    if (chr[start + i] != chr[start + end  - i - 1]) {
                        chk = false;
                        break;
                    }
                }
                
                if (chk) return end;
            }
        }
        
        return 1;
    }
}

`````

/// 가장 긴것부터, 양쪽으로 줄여가며 검사하다가, 펠린드롭이 성립되지 않는 시점ㄹ에서 break 문을 이용해 빠져나온다.
/// for문에 사용하는 변수는 for문 내부에선 가져다 쓸 수 있음.
/// boolean 변수를 활용하여. 펠린드롭이 성립되지 않는 시점이 곧, 펠린드롭이 성립되는 문장이 되므로 return문을 활용해 반환하면 끝이다.


---------
### 6월 9일
- 영어 회화 공부를 했다.
- 전자정부프레임워크의 의의에 대해 배움.

### 6월 10일
= 집이 공사 중이라, 오랫만에 카폐에서 공부함.

Protocol
- 컴퓨터와 컴퓨4터 간의 통신규약
- http : 서버가 인터넷 상에서 정보를 주고받기 위한 프로토콜(패킷)
- https : http에서 보안이 들어간 프로토콜
- mysql : 데이터베이스 프로토콜 
- ssh : 네트워크 상에서 다른 컴퓨터에 로그인해서 사용하기 위한 프로토콜.
- ftp ; 파일전송 프로토콜
- sftp : 네트워크 상에서 파일을 전송하기 위한 프로토콜

- IP : 컴퓨터 상의 주소(사람이 이해하기 힘듬)
- 도메인 : 사람들이 이해하기 쉽도록 정함.
- Port : 컴퓨터 상에 열려있는가? 닫혀있는가?

### 각각의 프로토콜은 포트번호가 정해져있음
1. http : 80
2. https : 443
3. ssh : 22
4. ftp : 21
5. sftp : 22
6. mysql : 3306

### ssh와 sftp의 포트번호가 같은 이유?
- sftp는 ssh에 있는 부가적인 기능
- sftp는 ssh의 파일전송 번호임.

##### 이러한 포트번호는 디폴트로 다 정해져있음

1. Request하기 위해선
- 어떤 프로토콜을 선택할지를 알아야한다.
- 어떤 Ip 주소로 보낼지를 택해야한다.
- 포트번호도 알아야한다.

2. Port Forwarding
- 외부에서 들어온 자료를 어느 기기로 보낼지를 결정하는 것.
- 네트워크 주소(공유기에 ip가 할당되어 있음)


#### 6월 12일
- 오늘은 프로그래머스 선입 선출 프로토콜을 풀어봤다.
- 처음에는 전부 나눠서 풀었는데, 효율성 검사를 통과하지 못해 아쉬웠다.
- 이진검색으로 풀어야 될 꺼 같았는데, 쉽사리 로직이 떠오르지 않았다.
- 참, 아쉬운 결과다.


#### 6월13일
- 디스크 컨트롤러 문제를 풀어봤다.
- 이번엔 오랫만에 1시간 20분 내에 푼 거 같다.


### 6월 16일

```java


import java.util.*;

class Solution 
{
    boolean [] visited;
    boolean [][] relation;
    public int solution(int n, int[][] edge) {
        int answer = 0;
        visited = new boolean[n+1];
        relation = new boolean[n+1][n+1];
        answer = bfs(edge);
        
        return answer;
    }
    public int bfs(int [][] edge)
    {
        Queue <Integer> queue = new LinkedList<>();
        queue.offer(1);
        visited[1] = true;
        
        for(int i = 0; i < edge.length; i++)
        {
            int x = edge[i][0];
            int y = edge[i][1];ㅅ
            
            relation[x][y] = true;
            relation[y][x] = true;
        }
        int size = 0;
        
        while(!queue.isEmpty())
        {
            size = queue.size();
            for(int i = 0; i < size; i++)
            {
                int current =  queue.poll();
                for(int j = 1; j < visited.length; j++)
                {
                    if(!visited[j]&& relation[current][j])
                    {
                        visited[j] = true;
                        queue.add(j);
                    }
                }
            }
        }
        
        return size;
    }
}

```
### 문제 풀이방법
- 연결되지 않은 노드 중에 방문하지 않는 노드만 찾는다.
- while  처리하긴 했지만 사실상 몇번만 돌고 끝남.


### 6월 17일
- 금과 은 운반하기 문제를 C++로 풀어보았다(자바가 익숙한 편이긴 한데, 면접이 C++ 회사라.)

### 6월 18일
- 면접 전 토요일이라 개념공부

### 6월 19일
- 휴식일이지만, 코딩 문제 C++로 재점검

### 7월 4일

````java

import java.util.Scanner;
import java.util.StringTokenizer;
 
public class Main 
{
 
	public static void main(String[] args) 
    {
        Scanner in = new Scanner(System.in);
        String s = in.nextLine();
        in.close();
        
        StringTokenizer st = new StringTokenizer(s, " ");
        
        // countTokens() 는 토큰의 개수를 반환한다
		System.out.println(st.countTokens());	
    }
}

````

-  StringTokenizer : 토큰으로 줄여서 반환함
-  countTokens() : 토큰의 개수를 반환함


![image](https://user-images.githubusercontent.com/72552897/177064822-80dbae9f-e555-4dff-8390-3a6419ef15bb.png)


https://koohee.tistory.com/14 : 여기서 첨부함

```` java


import java.util.Scanner;
 
public class Main {
 
	public static void main(String[] args) {
 
		Scanner in = new Scanner(System.in);
        
		int A = in.nextInt();
		int B = in.nextInt();
        
        in.close();
        
		A = Integer.parseInt(new StringBuilder().append(A).reverse().toString());
		B = Integer.parseInt(new StringBuilder().append(B).reverse().toString());
		
		System.out.print(A > B ? A : B);
	
	}
}

`````
2. 두번째 방법

````java


import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;
 
public class Main {
	public static void main(String[] args) throws IOException {
 
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		StringTokenizer st = new StringTokenizer(br.readLine()," ");
        
		int A = Integer.parseInt(new StringBuilder(st.nextToken()).reverse().toString());
		int B = Integer.parseInt(new StringBuilder(st.nextToken()).reverse().toString());
		
		System.out.print(A > B ? A:B);
		
	}
}


`````

- StringBuilder().append(A).reverse().toString()
- StringBuilder(st.nextToken()).reverse().toString()
- Scanner와 BufferedReader의 차이.

