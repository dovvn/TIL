# [MOOC - Python 프로그래밍 Ⅰ](https://pabi.smartlearn.io/courses/course-v1:POSTECH+DSC105+P2001/course/)  
이 문서는 위 MOOC강의를 듣고 필기용으로 기록되었습니다.  
[Part1강좌](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part1.md)에 선행되는 과정입니다.

# 개요
컴퓨터를 활용하여 일상 생활에 주어진 문제를 해결할 수 있도록 프로그래밍 기본 원리와 개념을 이해한다.  
문제 해결을 위해 C 언어로 프로그래밍 언어의 기본 구조와 문법을 알고, 그 문법으로 해결할 수 있는 다양한 일상 생활의 문제를 예제를 통해 학습한다.  

# 목차
* [Ⅰ. 문제 해결](#ⅰ-문제-해결)
  * [컴퓨팅 사고력과 문제해결](#week-1-1-컴퓨팅-사고력과-문제해결)
  * [파이썬 개발환경](#week-1-2-파이썬-개발환경)
  
# Ⅰ. 문제 해결  
# WEEK 1-1 컴퓨팅 사고력과 문제해결
이전에 학습한 CT1과 내용이 비슷하므로 생략. [CT1 문서](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part1.md#week-1-1-%EB%AC%B8%EC%A0%9C-%ED%95%B4%EA%B2%B0problem-solving)에서 확인할 것.

# WEEK 1-2 파이썬 개발환경
## 파이썬 설치
먼저, 최신 버전 파이썬을 [다운로드](https://www.python.org/downloads/) 받는다.

## 파이썬 실행 환경
* 파이썬 IDLE(Integrated Development and Learning Environment)
  * 파이썬을 개발 하기 위한 통합 개발 환경 의미
* IDLE는 두 가지 모드로 사용 가능
  * 대화형 파이썬 쉘(Python Shell)과 편집기 모드로 사용 가능
  * 1. 짧고 간단한 예제 코드는 파이썬 쉘을 이용
  * 2. 길고 복잡한 예제 코드는 코드 편집기를 이용
## 1. 파이썬 쉘로 코딩하기  
* IDLE에서 "hello world"를 출력한 모습  

![helloworld](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_helloworld.PNG)  

## 2. 코드 편집기로 코딩하기  
* IDLE창에서 File-New File을 클릭하여 코드 편집기 실행한다. 여기서 바로 코딩 가능하다.  
* 코드 입력후 ctrl+s 파일 저장
* 코드 편집기가 활성화 된 상태에서 F5 버튼 클릭
![코드편집기](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_shell.PNG)

## 다양한 운영체제에서 실행 가능
애플, 윈도우, 라즈페리 파이, 리눅스 등등...  

# Ⅱ. 파이썬 개요  
# WEEK 2-1 파이썬 개요
## 파이선 특징
* 1991년 귀도 반 로섬(Gudi Van Rossum) 발표
  * 플랫폼 독립적
  * 인터프리터 언어
  * 객체 지향
  * 동적 타이핑 언어
  * AI 프로그래밍을 위한 많은 라이브러리 제공
  * 처음 C언어로 구현되었음
