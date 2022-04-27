# TIL_3일차

강의 번호: JAVA
날짜: 2022년 4월 27일
복습: No
유형: 강의기록
작성일시: 2022년 4월 27일 오후 9:23

# OverLoading

메서드 작성시 동일한 이름으로 매개변수를 다양하게 만들 수 있다. 주로 생성자함수 등을 작성하는데 있어서 다양한 조건에 맞춰서 메서드 호출 할 수 있도록 하는 것.

 

```java
public class Person {
	//멤버변수 , private(접근제어자) 키워드를 사용하면 다른 클래스에서 접근 불가능 
	private String name;
	private int age;

	//기본 생성자 함수
	public Person() {} //default 생성자 함수. 

	//생성자함수
	public Person(String name, int age) {//생성자 함수 생성 방법 체크하기
		this.name = name;
		this.age = age;
	}
	
	//setter(Person 클래스의 필드(name, age)를 개별적으로 설정해주는 메서드)
	//명명규칙 : setXxx(), Xxx=> CamelCase 적용된 필드명
	public void setName(String name) {
		this.name = name;
		System.out.println("setName() 호출");
	}
}
```

# 참조변수란? - 힙(heap)메모리?, 스택(stack)메모리?

new 라는 키워드를 사용해서 인스턴스를 생성할 경우, heap 메모리 부분에 실제 값이 할당되며 ‘heap 메모리의 주소값’이 선언된 참조변수에 저장된다.

```java
public class YourClassNameHere {    
public static void main(String[] args) {        
	Mouse mickey; // 클래스명 변수명;         
		mickey = new Mouse();                
		mickey.name = "미키마우스";        
		mickey.age = 85;        
		mickey.address = "플로리다주";                
		System.out.println(mickey);                
		mickey.sing();    
		}
	}

	class Mouse {    
		int age;    
		String name;    
		String address;        
		public void sing() {        
		System.out.println(name + "찍찍!!");    
	}  
}
```

---

# TodoList 작업 과정 정리하기

---

주어진 자료 todo-data-simple.text

1	숙제하기	2022-03-05	수학, 영어 숙제
2	조깅하기	2022-03-07	공원에서 1시간 동안 조깅을 한다
3	놀기	2022-03-02	친구랑 논다.

tsv형식으로 저장된 텍스트를 통해 todo리스트 만들기 시작.

<aside>
💡 아래는 기본 세팅 이미지가 크므로 인용으로 접어두었습니다.

</aside>

- Maven 프로젝트로 새 작성 이후 폴더 경로를 동일하게 작성.
    
    ![시작.JPG](TIL_3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1%2050bef2a5b2ec4c3e9e308939519214b1/%EC%8B%9C%EC%9E%91.jpg)
    
    ![폴더 경로 동일하게 세팅.JPG](TIL_3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1%2050bef2a5b2ec4c3e9e308939519214b1/%ED%8F%B4%EB%8D%94_%EA%B2%BD%EB%A1%9C_%EB%8F%99%EC%9D%BC%ED%95%98%EA%B2%8C_%EC%84%B8%ED%8C%85.jpg)
    

자 이제 시작해보자...

---

<aside>
📌 하나의 Class인 App.java에서 데이터 입출력, 연산, 출력 처리하는 부분을 다 하고 있다.      이런 Godclass의 부담을 덜기 위해서 텍스트 내용을 관리하는 별도의 Class ‘Todo’를 생성 한 뒤 할 일 순서의 번호에 따라 하나의 Todo를 조회하는 기능을 구현해보자.

</aside>

## 1. Todo클래스 작성

먼저 Todo 클래스 작성을 위해 필드 값을 입력한다. 그 중 날짜와 관련된 LocalDate 타입을 사용하고자 import를 진행했습니다. **(import 단축키는 Ctrl+Shift+O)**

- 접어둔 코드
    
    ```java
    package com.todo.model;
    
    import java.time.LocalDate;
    
    public class Todo {
    	private Long id;
    	private String title;
    	private String description;
    	private LocalDate dueDate; //time Class의 하위개념 중 하나인 데이터 타입 LocalDate를 사용하기 위해 import해야한다.(참조타입)
    	private Boolean isCompleted;
    	
    }
    ```
    

![필드값 생성.jpg](TIL_3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1%2050bef2a5b2ec4c3e9e308939519214b1/%ED%95%84%EB%93%9C%EA%B0%92_%EC%83%9D%EC%84%B1.jpg)

---

## 2. 필드 값을 이용한 생성자 함수 작성.

필드 값 설정 후 생성자 함수를 작성하는 것은 이클립스에서 제공하는 기능을 활용했습니다. 

단축키는 Alt+Shift+S 

- 접어둔코드
    
    ```java
    package com.todo.model;
    
    import java.time.LocalDate;
    
    public class Todo {
    	private Long id;
    	private String title;
    	private String description;
    	private LocalDate dueDate; //time Class의 하위개념 중 하나인 데이터 타입 LocalDate를 사용하기 위해 import해야한다.(참조타입)
    	private Boolean isCompleted;
    	
    	//isCompleted를 제외한 필드값을 활용하는 생성자함수 작성 
    	public Todo(Long id, String title, String description, LocalDate dueDate) {
    		super();
    		this.id = id;
    		this.title = title;
    		this.description = description;
    		this.dueDate = dueDate;
    		this.isCompleted = false; //기본적으로 완료상태가 아니라는 상황에 맞추어 false값 부여
    	}
    }
    ```
    

---

## 3. setter, getter 정의

현재 각 필드 값 Long id, String title, String description, LocalDate dueDate, Boolean isCompleted는 각각 private 필드로 정의되어 있기 때문에 접근자 메서드인 setter와 getter를 작성하겠습니다.

- 접어둔 코드
    
    ```java
    package com.todo.model;
    
    import java.time.LocalDate;
    
    public class Todo {
    	private Long id;
    	private String title;
    	private String description;
    	private LocalDate dueDate; //time Class의 하위개념 중 하나인 데이터 타입 LocalDate를 사용하기 위해 import해야한다.(참조타입)
    	private Boolean isCompleted;
    	public Todo(Long id, String title, String description, LocalDate dueDate) {
    		super();
    		this.id = id;
    		this.title = title;
    		this.description = description;
    		this.dueDate = dueDate;
    	}
    
    	//각 필드가 private로 설정되어 있으므로 접근자 함수 getter, setter 설정하였습니다.
    	public Long getId() {
    		return id;
    	}
    	public void setId(Long id) {
    		this.id = id;
    	}
    	public String getTitle() {
    		return title;
    	}
    	public void setTitle(String title) {
    		this.title = title;
    	}
    	public String getDescription() {
    		return description;
    	}
    	public void setDescription(String description) {
    		this.description = description;
    	}
    	public LocalDate getDueDate() {
    		return dueDate;
    	}
    	public void setDueDate(LocalDate dueDate) {
    		this.dueDate = dueDate;
    	}
    	public Boolean getIsCompleted() {
    		return isCompleted;
    	}
    	public void setIsCompleted(Boolean isCompleted) {
    		this.isCompleted = isCompleted;
    	}
    		
    }
    ```
    

---

## 4. App.java에서 파일 입출력 준비

프로젝트 안에 저장되어있는 todo-data-simple.txt를 입력하기 위한 작업을 진행합니다. 

1. 파일을 읽어올 기본적인 경로를 설정하는 RESOURCES라는 이름의 정적 필드 작성

2.날짜의 기록 포맷을 정의하는 DATE_PATTERN이라는 이름의 정적 필드 작성

3.파일을 읽어오는 메서드 작성시 필요한 입출력 예외처리 작업 

- 접어둔 코드
    
    ```java
    package com.todo;
    
    import java.io.IOException;
    import java.nio.file.Files;
    import java.nio.file.Path;
    import java.nio.file.Paths;
    import java.time.format.DateTimeFormatter;
    import java.util.List;
    
    import com.todo.model.Todo;
    
    public class App {
    		private static final String RESOURCES = "src/main/recources";
    		private static final DateTimeFormatter DATE_PATTERN = DateTimeFormatter.ofPattern("yyyy-MM-dd");
    				
    		public static void main(String[] args) throws IOException {
    			final Path filePath = Paths.get(RESOURCES + "todo-data-simple/txt");
    			Long numberOfRows = Files.lines(filePath).count(); //Files.lines(filePath)가 Long 타입으로 반환되므로 Long 타입의 변수에 할당
    			
    			// Todo 클래스의 인스턴스를 담을 Todo 타입의 객체 배열 생성
    			
    			Todo[] todos = new Todo[numberOfRows.intValue()];//배열 안의 numberOfRows는 정수값만 들어갈 수 있으므로 intValue속성을 사용한다.
    			
    			// java.util.List에 임폴트
    			List<String> lines = Files.readAllLines(filePath);
    	}
    
    }
    ```
    

## 5. 파일 입력 후 배열에 넣어 값들을 관리할 수 있도록 한다.

솔직히 이 부분이 제일 어려웠다. 의도는 알겠는데, 막상 비슷하게 코드를 짜보라고 하면 엄두가 안 날 듯... 게다가 txt파일을 읽어오는데 있어서 경로 이슈가 발생하여 한참을 끙끙 앓았다. 

![경로 오류.JPG](TIL_3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1%2050bef2a5b2ec4c3e9e308939519214b1/%EA%B2%BD%EB%A1%9C_%EC%98%A4%EB%A5%98.jpg)

하단 경고창을 보면 src\main\resourcestodo-data-simple.txt라고 적혀있으나 한 번 해결한 이후로 

 src\main\resources\todo-data-simple.txt 이 상황이어도 인식하기에 오류창을 다시 띄운다고 고생했다... 어쨌든 같은 프로젝트 안에 있는 파일 참조시 경로 문제가 발생할 경우 절대 경로로 조치 해볼 생각.

- 접어둔 코드
    
    ```java
    package com.todo;
    
    import java.io.IOException;
    import java.nio.file.Files;
    import java.nio.file.Path;
    import java.nio.file.Paths;
    import java.time.LocalDate;
    import java.time.format.DateTimeFormatter;
    import java.util.List;
    
    import com.todo.model.Todo;
    
    public class App {					//RESOURCES = 경로가 비슷한게 많아서 파일 추적하는 과정에서 오류가 발생하는 듯 하다. 이럴땐 절대 경로로 참조할 수 있도록 해보자
    		private static final String RESOURCES = "C:\\BigData\\02.backend\\01.java\\Step02_todo_mvc_TIL3\\src\\main\\resources/";
    		private static final DateTimeFormatter DATE_PATTERN = DateTimeFormatter.ofPattern("yyyy-MM-dd");
    				
    		public static void main(String[] args) throws IOException {
    			final Path filePath = Paths.get(RESOURCES + "todo-data-simple.txt");
    			Long numberOfRows = Files.lines(filePath).count(); //Files.lines(filePath)가 Long 타입으로 반환되므로 Long 타입의 변수에 할당
    			
    			// Todo 클래스의 인스턴스를 담을 Todo 타입의 객체 배열 생성
    			
    			Todo[] todos = new Todo[numberOfRows.intValue()];//배열 안의 numberOfRows는 정수값만 들어갈 수 있으므로 intValue속성을 사용한다.
    			
    			// java.util.List에 임폴트
    			List<String> lines = Files.readAllLines(filePath);
    			System.out.println(lines);
    			
    			int index = 0;
    			//forEach 반복문 사용. 파일에서 읽어온 lines의 내용을 요소 line에 순차적으로 대입한다.
    			for (String line : lines) {
    				
    				//String 타입의 배열 columns에 각 줄의 내용을 tab 기준으로 나누어 넣는다.
    				final String[] columns = line.split("\t");
    				
    				final long id = Long.parseLong(columns[0]);
    				final String title = columns[1];
    				final LocalDate dueDate = LocalDate.parse(columns[2], DATE_PATTERN);
    				final String description = columns[3];
    				
    				// 각 필드값을 가지는 Todo 타입의 todo 객체 생성
    				Todo todo = new Todo(id, title, description, dueDate);
    				
    				todos[index] = todo;
    				index++;
    				
    				//반복문 종료
    			}
    			for (int i = 0; i < todos.length; i++) {
    				System.out.println(todos[i]); //참조 변수 값 그대로 출력하면 내부적으로 toString()이 호출됩니다.
    			}
    			
    	}
    
    }
    ```
    

마무리로 원하는 인덱스 값에 따라 todo리스트를 불러올 수 있도록 조치했다.