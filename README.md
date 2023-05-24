# Migrating from Dagger to Hilt in your Android app

This folder contains the source code for the "Migrating from Dagger to Hilt in your Android app" codelab.

The codelab is built in multiple GitHub branches:
* `master` is the codelab's starting point.
* `interop` is an intermediate step in which Dagger and Hilt coexist.
* `solution` contains the solution to this codelab.

## Clean Architecture 학습하기

이 프로젝트는 안드로이드에서 제공한 Hilt 예제를 바탕으로 클린아키텍처 권장 사항들을 공부하고 적용해보기 위한 프로젝트입니다.

계획
1. LiveData -> Flow 로 바꾸기
2. Jetpack Compose 적용해보기
3. Testing

---

## LiveData -> Flow 적용하기

목표
- 최소한의 코드로 변경한다
- Data 레이어를 유지하며 동작이 가능하도록 한다

적용 포인트
- MutableStateFlow update 함수를 사용하기 위해 build gradle update를 진행
- LoginView 의 LoginViewState, userName 를 묶어서 새로운 UI State 생성
- Flow 의 경우 초기값이 필수적이므로 초기화 중임을 나타낼 수 있는 Loading State, InitSuccess State가 필요했음.

개선 필요한 부분
- SharedPreference 가 Main Thread 가 아닌 IO Thread에서 동작할 수 있도록 ViewModelScope 와 Dispatcher.IO 활용이 필요함 
- testing 파일도 livedata -> flow 적용해야함 
