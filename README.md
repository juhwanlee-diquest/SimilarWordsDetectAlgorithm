# SimilarWordsDetectAlgorithm

## 프로젝트 설명

SNS 대화는 굉장히 더럽다. 예를 들어 욕설을 detection 하는 AI모델을 만든다고 생각하자.

"병신" 단어 그대로 있다면 어렵지 않을 것이다.

하지만, 보통 SNS 대화에서는 "병1신", "ㅂㅅ", "ㅂ1ㅅ" 와 같이 구성되어 있다.

이러한 것을 파악하기란 참 어렵다.

## 해결방법

자음 모음을 구분해서 Levenshtein distance를 계산한다.

detection.ipynb 코드를 통해서 직접 수행할 수 있다.

예시.

text = "너 정말 병1신 같은 짓 좀 그만해. 이 ㅅ발, 왜 이렇게 일이 꼬이기만 하는 거야? 너 ㅂㅅ처럼 굴지 말고 제대로 좀 해. ㅅㅂ, 내가 왜 이딴 상황에 처하게 된 거야?"

slang = ['병신', '시발']

detection.ipynb
-> [('병신', '병1신', 5, 0.8571428571428572), ('병신', ' 병1신', 4, 0.75), ('병신', '병1신 ', 5, 0.75), ('시발', '발', 24, 0.6), ('시발', 'ㅅ발', 23, 0.8), ('시발', ' ㅅ발', 22, 0.6), ('시발', 'ㅅ발,', 23, 0.6), ('시발', '이 ㅅ발', 21, 0.5714285714285714)]

이처럼 유사한 단어를 추출할 수 있다. 
