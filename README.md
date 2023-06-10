# 🕹️ TicTacToe_App

### React로 X or O가 한줄로 나열되면 이기는 애플리케이션 만들기

👉🏻 [TicTacToe_App 바로가기](https://ji-yoon98.github.io/TicTacToe_App)

# 🕹️ 사용기술 & 개발환경

<img src="https://img.shields.io/badge/html-E34F26?style=for-the-badge&logo=html5&logoColor=white">&nbsp;
<img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white">&nbsp;
<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">&nbsp;
<img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=React&logoColor=black"/><br>
<img src="https://img.shields.io/badge/Visual Studio Code-0769AD?style=for-the-badge&logo=Visual Studio Code IDEA&logoColor=white">

# 🕹️ 화면구성 및 기능

Square 컴포넌트는 button, Board는 사각형 9개, App 컴포넌트는 게임판을 렌더링

1. `npx create-react-app`으로 설치
2. components 안에 Square.js, Board.js 생성
3. 각자 css 생성

```js
const [value, setValue] = useState("");
```
- value = 변수이름
- setValue = State를 정하는 함수 setter
- useState = value, setValue 리턴 / 초기 State 값을 정하는 Hook

4. 순서를 만들어서 O를 추가
- 첫 번째 시작 = X
- 두 번째 = O

```js
const status = 'Next player: X';
const [squares, setSquares] = useState(Array(9).fill(null));
const [xIsNext, setXIsNext] = useState(true);
const status = `Next player: ${xIsNext ? 'X' : 'O'}`;
```

5. Board의 handleClick 함수를 이용하여 xIsNext 값을 뒤집는다.

```js
const handleClick = (i) => {
  const newSquares = squares.slice();
  // 누군가 승리하거나 Square가 이미 채워졌다면 handleClick 함수가 클릭 무시
  if(calculateWinner(newSquares) || newSquares[i]) {
    return;
  }
  newSquares[i] = xIsNext ? 'X' : 'O';
  setSquares(newSquares);
  setXIsNext(current => !current);
}
```

6. 승자 결정하는 함수 만들고 표시하기
- 경우의 수를 나열해 둔 후 for문으로 한 줄로 같은 줄이 나오는 X or O를 return

```js
const winner = calculateWinner(squares);
let status;
if(winner){
  status = 'Winner: ' + winner;
} else {
  status = `Next player: ${xIsNext ? 'X' : 'O'}`;
}
```

7. 동작에 대한 기록 저장 (history)
- State를 App 컴포넌트로 이동
- Winner 관련 함수도 App 컴포넌트로 이동

8. 과거의 이동 표시(Map)
- map()함수 이용 history배열에 있는 것들 하나씩 나열하기
- jumpTo 함수 작성


