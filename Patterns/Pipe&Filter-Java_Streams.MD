# Pipe and Filter pattern

## Java Streams
![image](https://user-images.githubusercontent.com/29380084/115104594-7dd4b400-9f94-11eb-8634-60a4619422c2.png)


- sequence(배열, collections, IO, generators)에 여러 operations(filter)를 조합하여 원하는 
결과(result)를 얻는다. 
- 적용 가능한 메소드는 map, filter, takeWhile, limit, flatMap, disticnt 등이 있다. 
- result 형태로는 aggregate(sum, count, fintFirst, reduce) 또는
sequence(collect) 가 가능하다. 

Streams는 자바8에 도입된 기능인데, 이전 자바 버전에서는 배열/컬렉션 인스턴스를 
다룰때는 for/foreach 문을 순회하며 element 하나씩 다루었다. 로직이 복잡할수록 코드가 
길고 복잡해지며, 여러 메소드를 적용할 경우 다수의 loop를 순회해야 했다. 

-> Streams를 도입함으로서 여러 가지 일을 한번에 처리할 수 있어 간략한 코드 작성이 
가능하다. 

ex) 배열에서 홀수인 원소의 제곱을 배열의 원소로 반환하는 코드

```
int[] vs = {1,2,3,4,5,6,7,8,9,10};
IntPredicate even = x -> x % 2 == 0;
List<Integer> vsList = Aarrays.stream(vs)
  .map(x -> x*x)
  .filter(even.negate())
  .mapToObj(Integer::valueof)
  .collect((Collectos.toList());
  
> [1, 9, 25, 49, 81]
```

각 operation 적용후에는 Stream<T> type의 intermediate stream이 생성되고, terminal 
stream으로는 특정 type의 반환값이 return된다. Stream은 순차처리와 병렬처리가 가능하다.
integer 배열을 stream으로 변환하여 map(), filter(), mapToObj(), collect() 메소드를 적
용하고 List<Integer>를 얻는 코드이다
  
각 operation 적용후에는 Stream<T> type의 intermediate stream이 생성되고, terminal stream으로는 특정 type의 반환값이 return된다.
Stream은 순차처리와 병렬처리가 가능하다.
 
