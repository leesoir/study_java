# Question
https://www.acmicpc.net/problem/4344

첫째 줄에는 테스트 케이스의 개수 C가 주어진다.
	둘째 줄부터 각 테스트 케이스마다 학생의 수 N(1 ≤ N ≤ 1000, N은 정수)이 첫 수로 주어지고, 이어서 N명의 점수가 주어진다. 
	점수는 0보다 크거나 같고, 100보다 작거나 같은 정수이다.
	각 케이스마다 한 줄씩 평균을 넘는 학생들의 비율을 반올림하여 소수점 셋째 자리까지 출력한다.

```java
import java.util.Scanner;
import java.util.Random;

public class quiz03 {
	public static void main(String[] args) {
		
		Random r = new Random();
		Scanner sc = new Scanner(System.in);
		
		System.out.print("테스트 케이스를 입력하세요 > ");
		int count = sc.nextInt();
		
		for(int i=0; i<count; i++) {
			// 1000은 너무 많아서 임의로 10으로 함..
			int sum = 0;
			int stus = r.nextInt(10)+1;
			for(int j=0; j<stus; j++) {
				int[] total = new int[stus];
				int score = r.nextInt(101); // 0~100점 사이의 점수를 j번 출력
				total[j] = score; // 점수를 배열에 넣는다. 
				sum += score;
				System.out.print(score + " "); 
				
				if(j == stus-1) {
					// 마지막 점수가 출력되면 
					int num = 0; // 비율을 계산하기 위해 필요한 변수 num
					for(int element:total) { // enhanced for
						if(element >= sum/stus) {
							// depth 너무 깊다
							num++; // total을 돌면서 평균보다 점수가 높은 학생의 수를 count한다.
						}
					}
					double per = (double)num/(double)stus * 100.0;
					System.out.println("\n평균 이상(평균:" + sum/stus + ") : " + per + "% \n");
					// check : 소수점 셋째 자리까지 나타내야 한다.
				}
			}
		}
		
		sc.close();
	}
	
}
```

# 실행결과
더 수정해야 한다.

![b4344console](https://user-images.githubusercontent.com/69781566/98334899-45c16080-2047-11eb-94d1-f2092f65a0e3.png)
