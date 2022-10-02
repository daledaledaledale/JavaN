`ArrayList`

- ArrayList는 배열을 좀 더 편하게 쓸수있도록 Java에서 제공해주는 Class입니다.
- 일반 배열과는 다르게 메모리가 가능한한 추가할 수 있고
- 삭제에 대해서도 해당 index를 비워두기만 하는게 아니라 재정렬해주는 기능을 기본으로 제공해주고 있습니다.

`interface와 내부 변수`

```java
public class ArrayList<E> extends AbstractList<E>
        implements List<E>, RandomAccess, Cloneable, java.io.Serializable
``` 

- ArrayList의 배열의 크기는 처음 add를 할 때 정해진다.

`생성자`
```java
List<String> list = new ArrayList<>();
```
```java
public ArrayList() {
  this.elementData = DEFAUILTCAPACITY_EMPTY_ELEMENTDATA;
}
```
- 일반적으로 사용하는 별도의 파라미터가 없는 생성자입니다. 
- Array에 값을 대입하는걸 알 수 있습니다. 
- DEFAULTCAPACITY_EMPTY_ELEMENTDATA의 값은 비어있는 Array값입니다. 
- 즉, size 0의 Array가 만들어질 것입니다.

`add`

- `add(Object)`는 ArrayList의 제일 마지막에 값을 하나 추가하는 method입니다. 
- 중간에 삽입하고 싶으시다면 `add(index, Object)`를 사용하시면 됩니다. 
```java
public boolean add(E e) {
  ensureCapacityInternal(size + 1);
  elementData[size++] = e;
  return true;
}
```
- 가장 먼저 내부 Object[]배열의 크기를 재산정합니다.
- 그리고 해당 배열에 값을 입력 후 size값을 증가 그리고 return합니다.

`remove`

- remove는 데이트러르 제거하는 메서드 입니다.
- remove(int index)의 삭제
```java
public E remove(int index) {
        rangeCheck(index);

        modCount++;
        E oldValue = elementData(index);

        int numMoved = size - index - 1;
        if (numMoved > 0)
            System.arraycopy(elementData, index+1, elementData, index,
                             numMoved);
        elementData[--size] = null; // clear to let GC do its work

        return oldValue;
    }
```
- emove 메서드를 실행하면 가장 먼저 입력받은 index가 적절한 값인지 체크합니다.
- 그리고 삭제되는 Object의 값을 가져와서 변수에 담습니다. 
- 그 후 arraycopy를 이용해 삭제되는 부분 + 1 ~ 마지막까지의 영역을 삭제되는 부분의 시작점을 기준으로 해서 옮깁니다. 
- 그러면 삭제될 부분의 값은 다음 index의 값으로 겹쳐서 덮여 쓰여지게 됩니다. 
- 그리고 size의 마지막 index는 size - 1의 값과 중복되기 때문에 null처리를 하여 GC가 삭제할 수 있도록 합니다. 
- 그 후 임시 변수에 담아두었던 삭제된 값을 리턴합니다.

