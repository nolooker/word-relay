<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>끝말잇기</title>
</head>

<body>
    <div><span id="order">1</span>번째 참가자</div>
    <div>제시어 : <span id="word"></span></div>
    <input type="text">
    <button>입력</button>
    
    <script>
        const number    = Number(prompt('몇 명이 참가하나요?'));
        const $button   = document.querySelector('button');
        const $input    = document.querySelector('input');
        const $word     = document.querySelector('#word');
        const $order    = document.querySelector('#order');

        let word; // 제시어
        let newWord; // 현재 단어

        const onClickButton = () => {
            if(!word){ // 제시어가 비어 있는가?
                
                word = newWord; // 입력한 단어가 제시어가 된다.
                $word.textContent = word; // 화면에 제시어 표시

                const order = Number($order.textContent);
                if(order + 1 > number) {
                    $order.textContent = 1;
                } else {
                    $order.textContent = order + 1;
                }

                $input.value = '';
                $input.focus();

            } else { // 비어 있지 않다.
                if(word[word.length - 1] === newWord[0]) { // 입력한 단어가 올바른가?
                     // 올바르다.
                    word = newWord; // 현재 단어를 제시어에 저장한다.
                    $word.textContent = word; // 화면에 제시어 표시

                    const order = Number($order.textContent);
                    if(order + 1 > number) {
                        $order.textContent = 1;
                    } else {
                        $order.textContent = order + 1;
                    }

                    $input.value = '';
                    $input.focus();

                } else { // 올바르지 않다.
                    alert('올바르지 않은 단어 입니다.');
                    console.log('올바르지 않다.');

                    $input.value = '';
                    $input.focus();
                }
            }
        };

        const onInput = (event) => {
            newWord = event.target.value; // 입력하는 단어를 현재 단어로
            console.log('글자 입력', event.target.value);
        };

        $button.addEventListener('click', onClickButton);
        $input.addEventListener('input',onInput);

    </script>
</body>
</html>
