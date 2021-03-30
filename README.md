# naverboostcourse

<details><summary>1. Thread & Handler </summary>  
  새로 만든 스레드는 메인 스레드와 별개로 실행될 수 있고 독립적인 실행이 가능하기 때문에 자주 사용된다. 다만 메인 스레드에서 관리하는 UI 구성요소를 접근할 때는 핸들러가 반드시 사용되어야 한다. 그 이유는 UI나 파일과 같은 리소스는 여러 개의 스레드가 동시에 접근했을 때 시스템에서 어떤 것을 먼저 처리해야 하는지 모르는 문제가 발생할 수 있기 때문이다. 핸들러는 각각의 스레드 안에 만들어질 수 있고 다른 스레드에서 요청하는 정보를 순서대로(queue) 실행시켜 줄 수 있기 때문에 리소스에 대한 동시 접근의 문제를 해결해 준다. 스레드에서 핸들러로 메시지를 보내려면 Message 객체를 사용하며, Message 객체를 obtainMessage 메소드로 참조한 후 sendMessage 메시지를 이용해 핸들러로 보내면 handleMessage 메소드가 자동으로 호출되기 때문에 전달된 Message 객체를 처리할 수 있다.  다만 이 과정이 세 단계를 거치면서 복잡해지기 때문에 좀 더 간단한 방법을 사용한다.  
Post 메소드 호출 : 핸들러의 Post메소드를 호출하면 Runnable객체를 전달할 수 있다. 핸들러로 전달된 Runnable객체는 메인 스레드에서 실행될 수 있으며, 따라서 UI를 접근하는 코드는 Runnable 객체 안에 넣어두면 된다. </details>

<details><summary>2. AsyncTask </summary>
  Thread를 사용하면서 UI객체에 접근하고 싶다면 핸들러를 사용하고, 이를 더욱 간편하게 하고자 post 메소드를 사용하였다. 그리고 이보다 더 나은 방식으로 AsyncTask를 활용한다. AsyncTask는 하나의 클래스 안에 스레드로 동작하는 부분과 UI객체에 접근하는 부분을 함께 넣어둘 수 있도록 한다. 이 때문에 스레드를 사용하는 하나의 작업 단위가 하나의 클래스로 만들어질 수 있다. 예제에서는 AsyncTask를 상속한 ProgressTask를 사용한다. AsyncTask가 doinBackground에서 값을 증가시키고 publishProgress를 통해서 UI업데이트까지 AsyncTask클래스 안에서 처리해준다.</details>
