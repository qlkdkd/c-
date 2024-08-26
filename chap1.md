# 1. C언어 기반의 C++1
## 1-1. printf와 scanf를 대신하는 입출력 방식
### 문자열 "Hello World!"의 출력
```c++
#include<iostream>

int main() {
	int num = 20;
	std::cout << "Hello World!" << std::endl;
	std::cout << "Hello " << "World!" << std::endl;
	std::cout << num << ' ' << 'A';
	std::cout << ' ' << 3.14 << std::endl;
	return 0;
}
```
![image](https://github.com/user-attachments/assets/7000c642-a585-4901-9cd3-bd4fd88942c1)

* 헤더파일 선언문 `#include<iostream>`
* `std::cout`과`<<`을 이용한 출력
* `std::endl`을 이용한 개행


### scanf()를 대신하는 데이터의 입력
```c++
#include<iostream>
using namespace std;

int main() {
	int val1;
	std::cout << "첫 번째 숫자 입력: ";
	std::cin >> val1;

	int val2;
	cout << "두 번째 숫자 입력: ";
	cin >> val2;
	
	int result = val1 + val2;
	cout << "덧셈 결과: " << result << endl;

	return 0;
}
```
![image](https://github.com/user-attachments/assets/7bc1faf7-4944-4473-b328-caef93f65463)

```c++
#include<iostream>
using namespace std;

int main() {
	int val1, val2;
	int result = 0;
	cout << " 두 개의 숫자 입력: ";
	cin >> val1 >> val2;

	if (val1 < val2) {
		for (int i = val1 + 1; i < val2; i++) {
			result += i;
		}
	}
	else {
		for (int i = val2 + 1; i < val1; i++) {
			result += i;
		}
	}

	cout << "두 수 사이의 정수의 합: " << result << endl;
	return 0;
}
```
![image](https://github.com/user-attachments/assets/ee55e933-c546-4172-9be6-fe21cc8ea30c)


### 배열 기반의 문자열 입출력
```c++
#include<iostream>
using namespace std;

int main() {
	char name[100];
	char lang[200];

	cout << "이름: ";
	cin >> name;

	cout << "좋아하는 프로그래밍 언어: ";
	cin >> lang;

	cout << "이름: " << name << endl;
	cout << "좋아하는 프로그래밍 언어: " << lang << endl;
}
```
![image](https://github.com/user-attachments/assets/7b2ce092-e3d5-4f7e-b735-77efd0ec6747)


### 문제
1. 사용자로부터 총 5개의 정수를 입력받아서, 그 합을 출력하는 프로그램을 작성해보자. 단, 프로그램의 실행은 다음과 같이 이루어져야 한다.
```c++
#include<iostream>
using namespace std;

int main() {
	int n, sum = 0;
	for (int i = 0; i < 5; i++) {
		cout << i + 1 << "번째 정수 입력: ";
		cin >> n;
		sum += n;
	}
	cout << "합계: " << sum << endl;
	return 0;
}
```
![image](https://github.com/user-attachments/assets/38abaaab-45e7-417a-a947-599849efd062)

2. 프로그램 사용자로부터 이름과 전화번호를 문자열의 형태로 입력받아서, 입력 받은 데이터를 그대로 출력하는 프로그램을 작성해보자.
```c++
#include<iostream>
using namespace std;

int main() {
	char name[100], tel[100];
	cout << "이름: ";
	cin >> name;
	cout << "전번: ";
	cin >> tel;

	cout << "이름: " << name << "\n" << "전번: " << tel << "\n";
	return 0;
}
```
![image](https://github.com/user-attachments/assets/22853e58-bf14-47f4-bc7e-0ff5daf3bc02)


3. 숫자 하나를 입력받아서 그 숫자에 해당하는 구구단을 출력하는 프로그램을 작성해보자. 예를 들어 사용자가 5를 입력한다면 구구단에서 5단을 출력해야 한다.
```c++
#include<iostream>
using namespace std;

int main() {
	int gugu[9][9];
	for (int i = 1; i <= 9; i++) {
		for (int j = 1; j <= 9; j++) {
			gugu[i - 1][j - 1] = i;
		}
	}

	int n;
	cout << "정수 입력: ";
	cin >> n;

	for (int i = 1; i <= 9; i++) {
		cout << gugu[n - 1][i - 1] << "*" << i << "=" << gugu[n - 1][i - 1] * i << endl;
	}

	return 0;
}
```
![image](https://github.com/user-attachments/assets/ea030da2-ea22-4adb-8846-93742068232b)


4. 판매원들의 급여 계산 프로그램을 작성해 보자. 이 회사는 모든 판매원에게 매달 50만원의 기본 급여와 물품 판매 가격의 12%에 해당하는 돈을 지급한다. 예를 들어 민수라는 친구의 이번 달 물품 판매 금액이 100만원이라면 50+100*0.12=62, 따라서 62만원을 급여로 지급받는다. 단, 아래의 실행의 예에서 보이듯이 이러한 급여의 계산은 -1이 입력될때까지 계속 되어야 한다.
> 판매 금액을 만원 단위로 입력(-1 to end): 100
> 이번 달 급여: 62만원
> 판매 금액을 만원 단위루 입력(-1 to end): 200
> 이번 달 급여: 74만원
> 판매 금액을 만원 단위로 입력(-1 to end): -1
> 프로그램을 종료합니다.
