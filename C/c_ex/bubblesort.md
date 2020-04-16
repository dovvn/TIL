# 문제
## 포인터로 버블 정렬 함수 만들기
* 10개의 값을 입력받아 오름차순으로 정렬하는 함수를 만든다.
* 포인터를 이용해 main에 있는 원래 배열의 값을 바꾸어야 한다.
* 바꾼 후 정렬된 배열을 출력한다.

# 예제 입력1
10 5 8 2 9 1 4 6 11 15

# 예제 출력2
1 2 4 5 6 8 9 10 11 15 

# 접근방식
BubbleSort()은 매개변수로 받은 배열을 오름차순으로 정렬해 줄 함수이다.  
여기서 배열을 매개변수로 받아오는 경우 배열은 포인터 * 를 사용하지 않아도 주소에 참조할 수 있음에 유의한다.    
배열의 오름차순 정렬 시 for문을 돌려서 인접한 order[i]와 order[i+1]의 크기 비교를 반복한다.  
이때, order[i] > order[i+1]이면 오름차순이 아니므로 두 값을 교환한다.(임시변수 temp사용)  
이를 반복하면 가장 큰 수가 맨 마지막 인덱스에 위치하게 되고 이때, order[i+1]의 값은 존재하지 않기 때문에 한번의 순회에서 총 length-1번의 비교를 하게된다.  
이 과정을 반복하면 그 다음 큰 수가 뒤로 가게되고, 이를 length-1번만 반복하게 되면 최종적으로 오름차순으로 정렬된 배열을 구할 수 있다.  

# 코드
```c
#include <stdio.h>

void BubbleSort(int order[], int length);

int main() {
	int arr[10];
	int length = sizeof(arr)/sizeof(int);

	for(int i=0; i<length; i++){
		scanf("%d", &arr[i]);
	}
	
	BubbleSort(arr, length);
	
	for(int i=0; i<10; i++){
		printf("%d ", arr[i]);
	}
	
	return 0;
}

void BubbleSort(int order[], int length){
	int temp;
	
	for(int i=0; i < length-1; i++){
		for(int j=0; j < length-1; j++){
			if(order[j] > order[j+1]){
				temp = order[j];
				order[j] = order[j+1];
				order[j+1] = temp;
			}
		}
	}
}
```

# 실행 결과
![bubblesort_img](https://github.com/jdaun/TIL/blob/master/C/c_ex/image/c_bubblesort_Ex.PNG)

# 출처
구름EDU, 한눈에 끝내는 C언어 기초 15강(http://bitly.kr/MeLINwbL9)
