# 미니 삼목 대결

Vercel 배포용 React + Vite + Firebase 실시간 대결 프로젝트입니다.

## 실행

```bash
npm install
npm run dev
```

## Vercel 배포

- Framework Preset: Vite
- Build Command: `npm run build`
- Output Directory: `dist`

## Firebase 사용량 최소화

- Firebase SDK는 앱 시작 때가 아니라 `방 만들기` 또는 `참가하기`를 누른 뒤에만 로드합니다.
- Firestore 문서는 방 1개당 1개만 만듭니다.
- 컬렉션 이름은 `r`, 필드는 `b/t/w/d/x/o`처럼 짧게 저장합니다.
- 게임판은 배열 대신 문자열 9글자만 저장합니다. 예: `X-O---X--`
- 승리 기록, 채팅, 점수판처럼 계속 쌓이는 데이터는 저장하지 않습니다.
- 게임 중에는 방 문서 하나만 실시간 구독합니다.

## Firestore 데이터 형태

```js
{
  b: "---------", // board
  t: "X",         // turn
  w: "",          // winner
  d: false,       // draw
  x: "플레이어1",
  o: "플레이어2"
}
```

## 플레이 방법

1. 첫 번째 플레이어가 이름을 입력하고 `방 만들기`를 누릅니다.
2. 화면에 나온 방 코드를 두 번째 플레이어에게 알려줍니다.
3. 두 번째 플레이어가 이름과 방 코드를 입력하고 `참가하기`를 누릅니다.
4. 각 플레이어는 자기 차례에만 칸을 둘 수 있습니다.
