# Fastapi typing

* ### Union

  #### 다중 타입의 값을 받을 수 있다

  #### ex) Union[int | str | None] : int 또는 str 또는 None 값을 받는다.

* ### Optional

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
      "item_id": "bag"
  }
  ```

  #### q 파라미터에 아무것도 넣어주지 않았지만 None으로 지정해주었기 때문에 실행된다. 