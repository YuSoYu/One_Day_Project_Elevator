# One_Day_Project_Elevator

# 기능 리스트
||Function|Description|
|------|---|---|
| 1 | **호출 기능** | <ul><li>각 층의 엘리베이터 호출 버튼을 누르면 엘리베이터가 해당층으로 이동한다.</li><li>각 층의 엘리베이터 호출 버튼은 동시에 누를 수 있다.</li></ul> |
| 2 | **호출 취소 기능** | <ul><li>호출 이후, 한 번 더 호출 버튼을 누르면 호출이 취소된다.</li><li>호출 취소 전, 이동중이라면 호출 취소 된 시점에서 엘리베이터 위치를 확인 후 가장 가까운 층으로 이동한다. </li></ul> |
| 3 | **호출 상태 표시 기능** | <ul><li>각 층의 엘리베이터 호출 버튼을 누르면 호출상태 LED도 켜진다.</li><li>엘리베이터가 도착하거나 호출이 취소되면 호출상태 LED는 꺼진다.</li></ul> |
| 4 | **엘리베이터 이동** | <ul><li>엘리베이터는 1층에서 시작한다.</li><li>대기 중 호출이 발생하면 해당 층으로 이동한다.</li><li>이동 중 다른 호출이 발생하면 다음의 규칙을 따른다.</li><ul><li>먼저 호출된 층으로 가는 길에 있는 경우, 경유지로 설정하고 이동</li><li>먼저 호출된 층으로 가는 길에 없는 경우, 최종 목적지로 설정하고 이동</li></ul><li>호출이 없는 경우, 현재 층에서 대기한다.</li><li>엘리베이터는 각 층 사이에 대기할 수 없다.</li></ul> |
| 5 | **엘리베이터 위치 표시 기능** | <ul><li>엘리베이터의 현재 위치에 해당하는 LED는 켜진다.</li><li>엘리베이터가 이동한 뒤, 이전 LED는 꺼져야 한다.</li><li>엘리베이터의 이동 속도는 적절히 조정된다.</li></ul> |


# Flow Chart
1. LED_STATUS_One_Button
- ![이미지](https://private-user-images.githubusercontent.com/101921458/410065358-c1e5cbd3-2e02-4825-baad-7d51b49311a5.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mzg3NzA2MzEsIm5iZiI6MTczODc3MDMzMSwicGF0aCI6Ii8xMDE5MjE0NTgvNDEwMDY1MzU4LWMxZTVjYmQzLTJlMDItNDgyNS1iYWFkLTdkNTFiNDkzMTFhNS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMjA1JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDIwNVQxNTQ1MzFaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1iZTBiNGJlMTdkZDZhOTVlMWViZTZhYzVhZjAxZjMxMmU5ZGUwZmI0NDVmODBiZTFjZTY4MGQwNWY1MzU2ZjBmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.lDZKNG6SVD1cLsdqw6gE9mbTtW12Zx4ZyA-FK0e634o)


2. LED_STATUS
- ![image](https://private-user-images.githubusercontent.com/101921458/410064863-5ffc1ef4-5d4e-491e-8b90-9b831a9dfe9f.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mzg3NzA1NjQsIm5iZiI6MTczODc3MDI2NCwicGF0aCI6Ii8xMDE5MjE0NTgvNDEwMDY0ODYzLTVmZmMxZWY0LTVkNGUtNDkxZS04YjkwLTliODMxYTlkZmU5Zi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMjA1JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDIwNVQxNTQ0MjRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0yOWVmMGE4NTFkNGE3NDkzN2Q1MjMyNDY0YzczNDI1ZmVmNjgzNWNjMzVjMTg5NWQ5YmIyMmI0MmEzNjAwODY2JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.tfVVByCzGsBM_tXfD58fKUuwqgLwK960xXUIH-pvRGE)

3. LED_Sequentail
- ![이미지](https://private-user-images.githubusercontent.com/101921458/410064268-6b59c9a2-12d5-47b5-963b-6747e21d8a58.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mzg3NzA0NzYsIm5iZiI6MTczODc3MDE3NiwicGF0aCI6Ii8xMDE5MjE0NTgvNDEwMDY0MjY4LTZiNTljOWEyLTEyZDUtNDdiNS05NjNiLTY3NDdlMjFkOGE1OC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMjA1JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDIwNVQxNTQyNTZaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kMTkxMGM0ZDE0MjVhYmRlYTViY2E1YjZmZGZhNGI1Yzk0NTQ5NWJkYTYwNjc4ZGM1MzhjMjA4NzY4Y2ZlOTg4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.gn9OtkXdPpkdPnD3rjGeZvFOh58GnxZ82-ZFB0SYTFQ)
  
