# 문제
## 삽입 정렬 만들기
* 내림차순이 되도록 코드 작성하기

# 예제 출력
124 112 87 55 17 9 6 5 3 1 

# 접근방식
삽입 정렬은 하나의 값은 선택하고 자신 앞에 있는 값들과 하나씩 비교해나가면서 자리를 교환하는 정렬 방법이다.  
첫 시작은 arr[1]부터 시작하는데, 먼저 arr[1]을 임시변수 temp에 저장한 후 이를 앞의 요소인 arr[0]의 값과 비교하여 더 크면 arr[0]의 원소를 arr[1]의 자리에 넣어준다. 즉, 앞의 원소를 뒤로 미뤄주게 된다.  
그리고 기존의 arr[0]자리는 temp값으로 덮어 씌워주면 된다. 이렇게가 한번의 for문이며 그 다음 arr[2]를 선택한후 다시 arr[1]과 arr[0]의 값과 비교해준다.
이는 while문을 이용해 반복 수행한다. 이 때, 선택된 원소보다 앞의 원소들은 이미 정렬되어 있는 상태이기 때문에 원소를 선택하고 바로 앞 원소를 비교해서 선택한 원소가 작다면, 더 이상 앞의 원소들을 비교할 필요가 없기 때문에 다음 원소를 선택한다.  
따라서 쓸모없는 비교를 줄일 수 있으므로 버블 정렬보다 속도가 빠르다.  

# 코드
```c
#include <stdio.h>

int main() {
  
  int arr[10] = { 9, 17, 5, 6, 124, 112, 1, 3, 87, 55 };
  int temp; // 두 값을 바꿀 때 사용할 변수
  int length = sizeof(arr) / sizeof(int);
	int j;
	
	for(int i = 1; i<length; i++){
		temp = arr[i];
		j = i-1;
		while(j>=0 && arr[j] < temp){
			arr[j+1] = arr[j];
			j = j-1;
		}
		arr[j+1] = temp;
	}
	
	for(int i=0; i<length; i++){
		printf("%d ", arr[i]);
	}

  return 0;
}
```

# 실행 결과
![insertsort_img](https://github.com/jdaun/TIL/blob/master/C/c_ex/image/c_insertsort.PNG)

# 출처
구름EDU, 한눈에 끝내는 C언어 기초 13강(http://bitly.kr/MeLINwbL9)
