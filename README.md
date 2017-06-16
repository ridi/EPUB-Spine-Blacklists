# ePub-Spine-Blacklists

Blacklist 처리 되어야하는 EPub Spine 판별에 필요한 정보를 가지고있는 데이터.
주로 표지, 서지, 저자소개등 연속된 독서 흐름에 방해되는 콘텐츠를 줄여주기 위한 목적으로 이용.

### 형식
```
CP_ID:
  - id: string            # Spine ID, 마지막 spine을 나타낼 경우 ::LAST
    regex: bool           # Spine ID가 정규표현식이면 true로
    force: bool           # true면 글자수에 상관 없이 제외
    max_length: integer   # 글자수 기준 조정
    
  - include: integer      # 다른 ID꺼를 그대로 포함 - 사이클이 생겨서는 안된다
```

### 규칙

* 해당 CP의 Spine이 max_length 미만의 글자수를 가지고 있는 경우 블랙리스트 처리, 단 force값이 true인 경우 무조건 블랙리스트 처리

* id 가 spine의 id를 직접 명시하지 않는 경우도 있다. id가 ::LAST인 경우 마지막 스파인을 뜻하며, regex가 true인 경우 정규표현식이다.

* regex와 force의 default 값은 false, max_length의 default 값은 meta의 max_length

* 도서에 해당하는 CP가 없다면 Undefined 항목을 이용한다



