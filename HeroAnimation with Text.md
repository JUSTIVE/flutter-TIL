# Text 위젯을 Hero Animation할때 주의해야 할 점

text 위젯을 Hero 위젯으로 덮을 경우 이미지와는 다르게 glitch가 발생하는 것을 확인할 수 있다.  

```dart
Hero(
    tag: tag_something,
    child: Text('someText')
    //이대로 하면 각각의 화면에서는 문제가 없으나 전환 도중에 렌더링 경고 및
    //텍스트가 제대로 배치되지 않는 문제가 있다.
)
```

이를 [링크](https://github.com/flutter/flutter/issues/12463)에서 해답을 구할 수 있었는데,  
답은 간단하게 Text 위젯을 Material 위젯으로 감싸는 것이다.

```dart
Hero(
    tag: tag_something
    child: Material(
        color: Colors.transparent,
        child: Text('someText')
    )
)
```

이렇게만 하면 짜잔!