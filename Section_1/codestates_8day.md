# 코드스테이츠 - 7 day

## ✉️ 학습목표

- <과제1. 계산기 구현하기>의 Bare Minimum Requirements를 완성하지 못했다면

- <과제1. 계산기 구현하기>의 Bare Minimum Requirements> 완성하기

- 이해되지 않는 개념 아고라스테이츠에 질문하기

- <과제1. 계산기 구현하기>의 Bare Minimum Requirements를 완성했다면

- <과제2. User flow에 따라 기능 구현하기>의 Advanced Challenges 도전하기
- 아고라스테이츠에 올라온 다른 수강생의 질문에 답변하기
- 블로그에 정리 및 회고를 마친 후, 계산기의 CSS를 수정하여 더욱 예쁜 계산기를 만들기

- <과제2. User flow에 따라 기능 구현하기>의 Advanced Challenges를 완성했다면

- <과제2. User flow에 따라 기능 구현하기>의 Nightmare에 도전하기
- 아고라스테이츠에 올라온 다른 수강생의 질문에 답변하기
- 블로그에 정리 및 회고를 마친 후, 계산기의 CSS를 수정하여 더욱 예쁜 계산기를 만들기

<!--진행 중-->
- <과제2. User flow에 따라 기능 구현하기>의 Nightmare를 완성했다면
- 아고라스테이츠에 올라온 다른 수강생의 질문에 답변하기
- 계산기를 만든 과정과 경험을 블로그에 정리 및 회고하기
- 블로그에 정리 및 회고를 마친 후, 계산기의 CSS를 수정하여 더욱 예쁜 계산기를 만들기

```javascript
  if (target.matches('button')) {
    if (action === 'number') {

      if (prevKey === 'default') {
        display.textContent = buttonContent;
        currNum = buttonContent;
        prevKeytype(action);
      } else if (prevKey === 'operator') {
        currNum = buttonContent;
        display.textContent = buttonContent;
        prevKeytype(action);
      } else {
        currNum += buttonContent;
        prevKeytype(action);
        display.textContent = currNum;
      }
    }

    if (action === 'operator') {
      if (prevKey === 'operator') {
        operatorText = operatorType(buttonContent);
        return;
      }
      if (isOperator) {
        total = calculate(prevNum, operatorText, currNum);
        prevNum = total;
        prevKeytype(action);
        operatorText = operatorType(buttonContent);
        display.textContent = total;
      } else {
        prevNum = currNum;
        operatorText = operatorType(buttonContent);
        prevKeytype(action);
        isOperator = true;
      }
    }

    if (action === 'decimal') {

      if (currNum === '0') {
        currNum += '.';
        display.textContent = currNum;
        prevKeytype("number");
      } else if (prevKey === 'default') {
        currNum += '0.';
        display.textContent = currNum;
        prevKeytype("number");
      } else if (prevKey === 'operator') {
        prevNum = currNum;
        currNum = '0.';
        display.textContent = currNum;
        prevKeytype("number");
      } else {
        if (currNum.includes('.')) return;
        currNum += buttonContent;
        display.textContent = currNum;
        prevKeytype("number");
      }

    }

    if (action === 'clear') {
      prevKey = 'default';
      currNum = '';
      prevNum = '';
      operatorText = '';
      total = 0;
      display.textContent = '0';
      isOperator = false;
    }

    if (action === 'calculate') {
      // 방어 코드
      if (!currNum && !prevNum && !operatorText) return;
      if (prevKey === 'operator') {
        let result = calculate(currNum, operatorText, currNum);
        display.textContent = result;
      } else if (prevKey === 'calculate') {
        console.log(total, operatorText, currNum);
        let result = calculate(total, operatorText, currNum);
        display.textContent = result;
        total = result;
      } else {
        let result = calculate(prevNum, operatorText, currNum);
        display.textContent = result;
        prevKeytype(action);
        total = result;
      }
    }
  }
```