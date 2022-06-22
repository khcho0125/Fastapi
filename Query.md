# Query 

### Fastapi라이브러리의 Query는 spring boot의 Valid와 같다.

#### 매개변수의 추가 정보나 유효성 검사를 선언할 수 있다.

#### Optional과 마찬가지로 기본값 설정도 할 수 있고

#### Size 범위를 지정해 준다던지 매칭되어야 하는 정규식을 정의할 수 있다.

```python
async def test(name: str = Query(default=None, min_length=3, max_length=10, regex="[a-z]"))
```

#### 만약 매개변수 값이 무조건 필요하다면 default에 `...` 을 넣으면 된다.

```python
async def test(name: str = Query(default=..., min_length=3, max_length=10, regex="[a-z]"))
```

* #### 필수 None

  #### None 매개변수를 허용할 수 있지만 None 마저 필수로 입력되도록 하고 싶다면 아래와 같이 작성하면 된다.

  ```python
  async def test(name: Union[str, None] = Query(default=...)):
  ```

  #### 만약 `...` 이 불편하다면 pydantic의 Required를 가져와 사용할 수 있다.

  ```python
  async def test(name: Union[str, None] = Query(default=Required)):
  ```

---

#### Query의 title과 description을 정의해주면 /docs, /redoc 에서 추가 정보를 보여줄 수 있다.

```python
async def test(name: Union[str, None] = Query(default=None, title="Query string", description="ABC", min_length=3)):
```

* #### /redoc

  <img src="https://user-images.githubusercontent.com/82090641/175012837-772dfc85-8be9-4574-85f4-2a3c6eaffd68.png">

* #### /docs

  <img src="https://user-images.githubusercontent.com/82090641/175012938-021bc61f-14a5-478e-b170-8a1c91ba71a4.png">

#### 위와 같이 지정해준 추가 정보가 명시된다.

---

#### 매개변수 값을 받을 필드 명을 변경하고 싶을 땐 alias를 정의해주면 된다.

```python
async def test(name: Union[str, None] = Query(default=None, alias="user_name")):
```

#### 대신 alias로 지정된 변수 명으로는 값을 받을 수 없다.

---

#### 매개변수를 더 이상 사용하지 않을 땐 deprecated나 include_in_schema를 사용한다.

> #### OpenApi에만 영향을 끼치기 때문에 자주 사용할 것 같진 않다.

* #### deprecated 

  #### 매개 변수 사용이 중단되었지만 그것을 사용하는 클라이언트가 있기 때문에 잠시 두어야 하는 상황에 쓰인다.

  ```python
  async def test(name: Union[str, None] = Query(default=None, deprecated=True)):
  ```

* #### include_in_schema

  #### OpenApi에서 매개 변수를 제외할 때 사용한다. 

  ```python
  async def test(name: Union[str, None] = Query(default=None, include_in_schema=True)):
  ```