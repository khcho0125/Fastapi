# Fastapi typing

- ### Union

  #### 다중 타입의 값을 받을 수 있다

  #### ex) Union[int | str | None] : int 또는 str 또는 None 값을 받는다.

- ### Optional

  #### default 값을 지정해주는 타입이다.

  #### ex) str

  ```json
  {
      "detail": [
          {
              "loc": [
                  "query",
                  "q"
              ],
              "msg": "field required",
              "type": "value_error.missing"
          }
      ]
  }
  ```

  #### field required 메시지가 뜨면서 값이 들어오지 않았다고 알려준다.

  #### ex) Optional[str]

  ```json
  {
      "query": "pencil"
  }
  ```

  #### q 파라미터에 아무것도 넣어주지 않았지만 None으로 지정해주었기 때문에 실행된다.

  - #### 2022-06-22 추가사항

    #### Optional을 사용하지 않고도 아래와 같이 required Query Parameter 로 지정할 수 있지만

    ```python
    async def test(query: str, q: str = None):
    ```

    #### 위 코드는 Fastapi가 q = None이라는 걸 선택적이라고 인지한다.

    #### Optional은 Fastapi 가 사용하지 않지만 다른 사람이나 자신이 보았을 때 코드 오류를 찾아낼 수 있도록 도와주기 때문에 사용한다고 한다.

    ```python
    async def test(query: str, q: Optional[str] = None):
    ```

    #### 가능하면 Optional을 꼭 명시해주도록 하자

