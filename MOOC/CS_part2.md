# [MOOC - Computer Science(컴퓨터공학 입문) Ⅱ](https://pabi.smartlearn.io/courses/course-v1:POSTECH+DSC104+P2001/about)  
이 문서는 위 MOOC강의를 듣고 필기용으로 기록되었습니다.  
[Part1강좌](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part1.md)에 선행되는 과정입니다.

# 개요
컴퓨터를 활용하여 일상 생활에 주어진 문제를 해결할 수 있도록 프로그래밍 기본 원리와 개념을 이해한다.  
문제 해결을 위해 C 언어로 프로그래밍 언어의 기본 구조와 문법을 알고, 그 문법으로 해결할 수 있는 다양한 일상 생활의 문제를 예제를 통해 학습한다.  

# 목차
* [Ⅴ. 조건문](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part2.md#%E2%85%B4-%EC%A1%B0%EA%B1%B4%EB%AC%B8)
  * [조건문(if)과 문제해결 예제(성적처리)]()
  * [조건문(switch)과 문제해결 예제(윤년계산)]()
* [Ⅵ. 반복문]()
  * [반복문(for)]()
  * [반복문(while, do while)]()
* [Ⅶ. 파일 입출력]()
  * [파일 입출력과 함수]()
  * [파일 입출력과 함수 예제 실습]()
  
# Ⅴ. 조건문 
# WEEK 5-1 조건문(if)과 문제해결 예제(성적처리)
## 조건문(if)
* 조건의 결과(참 또는 거짓)에 따라 프로그램의 흐름을 제어하는 문장
* 어떠한 조건을 만족하면 그에 해당하는 일이 처리되는 문장
```c
if (expression)
   statement1;
next_statement;
```

* if에서 결과가 거짓인 경우 수행해야 할 문장이 있다면 키워드 else를 사용
```c
if (expression)
{
   statement_true;
}
else
{
   statement_false;
}
next_statement;
```

* else if
  * 조건 여러 개를 비교하여 조건에 맞는 문장을 수행
  * 중첩된 if문에서 else이후에 if문을 실행하는 구문 이용
```c
if (expression1)
{
   statement1;
}
else if(expression2)
{
   statement2;
}
else if(expression3)
{
   statement3;
}
else
{   
   statement4;
}
next_statement;
```

# WEEK 5-2 조건문(switch)과 문제해결 예제(윤년계산)
## switch
* 선택해야 할 조건이 여러 개 있을 경우 조건에 맞는 문장을 선택하여 수행
* expression, value: 정수 또는 정수 수식이어야 함
* switch case: 필수 항목
* break, default: 선택 항목
```c
switch (expression)
{
   case value1 :
      statement1;
      break;
   case value2 :
      statement1;
      break;
   default :
      statement;
      break;
}
next_statement;
```
* switch의 값을 case상수식과 차례로 비교하여 값과 일치하는 case문장을 수행하고 break문을 만나면 swtich문을 종료
* break문을 지정하지 않으면 최초로 break문이 나올 때까지 현재 실행된 문장 이후의 모든 상수식의 문장들을 실행

## 일상 생활 문제 해결: 윤년(leap year)
* 2월을 제외하고 1~12월의 마지막 날짜는 정해져 있다.
  * 31일: 1,3,5,7,8,10,12
  * 30일: 4,6,9,11
* 2월의 마지막 날이 어떤 해는 28일, 어떤 해는 29일인 경우가 있는데 년과 월을 입력했을 때 해당하는 월의 마지막 날짜를 알고 싶다면?
  * 2월 마지막 날은 윤년 계산 결과가 필요함
* 윤년을 계산하는 방법 조사하기(치윤법)
  * 기원 연수가 4로 나누어 떨어지는 해는 우선 윤년으로 하고, (year % 4 == 0)
  * 그 중에서 100으로 나누어 떨어지는 해는 평년으로 하며, (year % 100 != 0)
  * 다만 400으로 나누어 떨어지는 해는 다시 윤년으로 정한다.(year % 400 == 0)
  * => (year % 4 == 0) && (year % 100 ! = 0) || (year % 400 == 0)
```c
#include <stdio.h>

int main(void) {
int year = 0, month = 0, maxDay = 0;
printf("\n년과 월을 입력하세요: ");
scanf("%d %d", &year, &month);
switch(month){
	case 1:
	case 3:
	case 5:
	case 7:
	case 8:
	case 10:
	case 12:
		maxDay = 31;
		print("%d년 %d월 말 일은 %d일 입니다.\n", year, month, maxDay);
		break;
	case 4:
	case 6:
	case 9:
	case 11:
		maxDay = 30;
		print("%d년 %d월 말 일은 %d일 입니다.\n", year, month, maxDay);
		break;
	case 2:
		if ((year % 4 == 0) && (year % 100 != 0) || (year % 400 == 0))
		{
			maxDay = 29;
			print("%d년 %d월 말 일은 %d일 입니다.\n", year, month, maxDay);
			break;	
		}
		else
		{
			maxDay = 28;
			print("%d년 %d월 말 일은 %d일 입니다.\n", year, month, maxDay);
			break;
		}
	default:
		print("입력이 잘못 되었습니다.\n");
	}
	return 0;
}
```

# Ⅵ. 반복문
# WEEK 6-1 반복문(for)
## 프로그램의 흐름 제어: 제어문
* 순차: 위에서 아래로 한 문장씩 순차적으로 수행
* 선택: 조건에 따라 흐름 제어~조건문
* 반복: 조건에 따라 반복 수행~반복문
* 분기: 정해진 위치로 이동~분기문

## 제어문의 종류
* 조건문: 조건에 따라 프로그램의 흐름을 제어하는 명령문
  * if, if-else
  * switch-case
* 반복문: 조건에 따라 정해진 문장을 반복 수행하는 명령문
  * for
  * while, do-while
* 분기문(Jump Statements): 명령어를 만나면 정해진 곳으로 점프
  * goto, return, break, continue

## 키워드(Keyword)(1983 ANSI C)
* 약속된 의미의 단어(32개)
* 키워드는 약속된 의미로만 사용(데이터 타입, 제어 명령 등)
* 키워드는 식별자(변수명)로 사용할 수 없음
![c_keyword](https://github.com/jdaun/TIL/blob/master/MOOC/img/c_keyword.PNG)

## 반복문 종류
* for: 일정한 반복 횟수를 이용하는 반복문에 적합
```c
for(초기화; 조건검사; 증감연산){
   for문 몸체(body);
}
```
* while: 구문이 간단하며, 검사 부분이 처음에 있음
```c
while(조건검사){
   while문 몸체(body);
}
```
* do while: 반복 몸체를 1번은 실행하며, 검사 부분이 뒤에 있음
do{
   do while문 몸체(body);
}while(조건검사);

## 반복문(for)
* 1부터 777까지의 합 구하기
```c
#include <stdio.h>

int main(void) {
	int i, sum;
	sum = 0; //지역변수 초기화
	for(int i=1; i<=777; i++){
		sum+=i;
	}
	printf("1부터 777까지의 합: %d \n", sum);
	return 0;
}
```

## 일상 생활 문제: 성적처리(반복문for활용)
* 수강인원을 입력받고, 학생 각각의 학번과 점수를 입력받아 점수에 따라 학점을 산출하고 평균을 구한다.
* 입력 설계
  * 1.수강인원을 입력
  * 2.학번과 점수를 입력
* 출력 설계
  * 1.학점을 산출
  // if, else if, 학생수 만큼 반복 for  
  * 2.과목평균
  // 입력된 핛갱들의 점수 총점으로 평균 산출  
```c
#include <stdio.h>

int main(void) {
	int i, stuNum, stuID, csed101;
	char grade;
	float total = 0;
	print("*** 컴퓨터공학입문 성적 ***\n");
	print("수강인원을 입력하세요: ");
	scanf("%d", &stuNum);
	for(i=0; i<stuNum; i++){
		print("학번과 점수를 순서대로 입력하세요: ");
		scanf("%d%d", &stuID, &csed101);
		total += csed101; //total = total + csed101
		if (csed101 >= 90)
			grade = 'A';
		else if(csed101 >= 80)
			grade = 'B';
		else if(csed101 >= 70)
			grade = 'C';
		else if(csed101 >= 60)
			grade = 'D';
		else
			grade = 'F';
		print("학번: %d, 학점: %c\n", stuID, grade);
	}
	print("과목 평균: %5.2f\n", total/stuNum);
	return 0;
}
```

# WEEK 6-2 반복문(while, do while)
## while, do-while
* 조건을 만족하는 동안 특정 작업을 반복하여 처리함.
* while문의 경우 조건이 거짓인 경우 조건문을 한번도 하지 않는 경우도 있지만, do-while은 반드시 한번은 조건문을 수행한다.
## while과 for문의 관계
* while
```c
int sum = 0;
int i = 1;

while(i<=10){
   sum+=i;
   i++;
}
```

* for문
```c
int sum = 0;
int i;

for(i=1; i<=10; i++){
   sum+=i;
}
```

# Ⅶ. 파일 입출력
# WEEK 7-1 파일 입출력
## 파일(File)이란?
* 데이터의 모임으로서 보조기억장치에 저장된 것
* 텍스트(text)파일은 사람이 알아볼 수 있는 문자나 숫자 등으로 이루어진 파일
  * 텍스트파일 : 'input.txt'
* 텍스트 파일 작성: 메모장에서 확장자 txt로 저장

## 텍스트파일과 소스코드 파일
* 텍스트 파일 작성: 메모장에서 확장자 .txt로 저장
* 소스코드 작성: 확장자 .c로 저장
* 소스코드에서 파일을 입력 받을 경우, 소스코드와 입력 파일을 같은 폴더에 넣고 저장

## 파일 입출력 처리 순서
* 1.파일 연결(input.txt, ouput,txt)
  * 1.파일의 주소를 저장할 수 있는 파일 포인터 변수 선언
  * 2.FILE *inData, outData
* 2.파일 열기
  * 1.fopen()함수 사용
* 3.파일의 데이터 읽어 오기
  * 1.fscanf()함수 사용
* 4.읽어온 데이터로 성적 처리
  * 1.if,esle 등의 명령어 사용
* 5.파일 닫기
  * 1.fclose()함수 사용
  
## 구조도
* 성적처리 main()
* 데이터입력 getStu()
* 성적 계산 calcGrade
* 데이터 출력 writeStu

# WEEK 7-2 파일 입출력과 함수 예제 실습
* 성적처리 main()
intput.txt파일을 미리 생성한다.  

```c
#include <stdio.h>

int getStu(FILE* spStu, int* stuID, int* exam1, int* exam2, int* final);
void calcGrade(int exam1, int exam2, int final, int* avrg, char* grade);
void writeStu(FILE* spGrades, int stuID, int avrg, char grade);

int main(void){
	FILE* spStu; //입력파일 주소 저장 
	FILE* spGrades; //출력 파일 주소 저장 
	
	int stuID, exam1, exam2, final; //학번, 과제1, 과제2, 기말 
	int avrg; //평균 
	char grade; //학점
	
	printf("Begin Student grading\n");

	//파일 읽기 모드 열기 
	if(!(spStu = fopen("input.txt", "r"))){
		{//error 
			printf("파일 열기 error\n");
			return 100;
		}
	}
	//출력파 
	if(!(spGrades = fopen("output.txt", "w"))){
		{//error 
			printf("파일 열기 error\n");
			return 102;
		}
	}
	
	//입력 데이터 여러줄 처리 
	while(getStu(spStu, &stuID, &exam1, &exam2, &final)){
		calcGrade(exam1, exam2, final, &avrg, &grade);
		writeStu(spGrades, stuID, avrg, grade);
	}
	
	fclose(spStu);
	fclose(spGrades);
	printf("End Student grading\n");
	return 0;
}

//데이터입력 
int getStu(FILE* spStu, int* stuID, int* exam1, int* exam2, int* final){
	int ioResult;
	
	//데이터를 파일로부터 받아 main영역에 저장 
	ioResult = fscanf(spStu, "%d%d%d%d", stuID, exam1, exam2, final); //파일 연결, 입력받을 데이터 만큼(int형4개)
	
	if(ioResult == EOF) //End Of File 파일의 끝 확인 
		return 0;
	else if (ioResult != 4){
		printf("Error Reading\n");
		return 0;
	}
	else
		return 1;
}

//성적계산 
void calcGrade(int exam1, int exam2, int final, int* avrg, char* grade){
	*avrg = (exam1 + exam2 + final) / 3;
	
	if(*avrg >= 90) //평균값을 사용하여 학점 계산
		*grade = 'A';
	else if(*avrg >= 80)
		*grade = 'B';
	else if(*avrg >= 70)
		*grade = 'C';
	else if(*avrg >= 60)
		*grade = 'D';
	else
		*grade = 'F';		
}

//성적 출력
void writeStu(FILE* spGrades, int stuID, int avrg, char grade){
	//output.txt 파일로 실행 결과 출력, 모니터에는 나오지 않음
	fprintf(spGrades, "%04d %d %c\n", stuID, avrg, grade); //output.txt 주소 저장, %04d: 4개의 칸에 학점 출력  
}
```

output.txt의 실행결과   
![result_output](https://github.com/jdaun/TIL/blob/master/MOOC/img/result_output.PNG)  

여기서 output 프로그램은 실행 전 만들지 않고 프로그램 실행 후 자동 생성됨을 알 수 있다.  



