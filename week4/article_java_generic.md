
### java generics rules
#### Don't use raw types
a `raw type generic` is a generic which has no accompanying type parameters like `List` not `List<E>`, it ensures binary backward compatibility of Java written in previous non-generic versions.
```
    List listInteger = new ArrayList();
    listInteger.add("Rain");
```
It compiles ok, just get a warning `Unchecked call to 'add(E)' as a member of raw type 'java.util.List'`. We thought `listInteger` is a list of `Integer`, but now a `String` sneaks in, so when we traverse the list and get each element as an `Integer`, we will get `ClassCastException`. 
##### List not like List<Object>
`List` is raw type, while `List<Object> ` is parameterized type. we can pass `List<String>` to `List` not `List<Object>`. We will lose type safety when we use a raw type, but not when we use a parameterized type.

#### Eliminate unchecked warnings
```
List<String> list = new ArrayList();
```
The above code leads to a warning `Unchecked assignment: 'java.util.ArrayList' to 'java.util.List<java.lang.String>' `, it's an unchecked warning.
##### Eliminate every unchecked warning that you can
##### Use @SuppressWarnings("unchecked") to suppress the unchecked warnings only when we are sure the code is typesafe.
##### Use @SuppressWarnings("unchecked") on the smallest scope possible.

#### Prefer lists to arrays
lists belong to generics. The differences between arrays and generics:
 * arrays are covariant while generics are invariant.
 * arrays are reified while generics are not, generics are implemented by erasure.
```
     Object[] array = new Long[1];
    array[0] = "Hello";
```
throws `ArrayStoreException` at runtime. 
```
    List<Object> list = new ArrayList<Long>();
    list.add("Hello");
```
compiles error. We'd rather find out the errors at compile time.

#### Favor generics types
**Generify any types that should be generic**. Generic types are safer and easier to use that types that require casts in client code.
use `public class stack<E> {private E[] elements;}` not `public class Stack{private Object[] elements;}`

#### Favor generics methods
use `public static <E> Set<E> union(Set<E> s1, Set<E> s2)`
not `public static Set union(Set s1, Set s2)`

#### Use bounded wildcards to increase api flexibility
 * If a parameterized type represents a T producer, use `<? extends T>`
 * If a parameterized type represents a T consumer, use `<? super T>`
 * Do not use bounded wildcard types as return types. 

### Combine generics and varargs judiciously 
 * Mixing generics and varargs can violate type safety, it may cause `Heap pollution`
 * The `SafeVarargs` annotation should be used only when we are sure it's typesafe.

### Consider typesafe heterogeneous containers
like `Map<Class<?>, Object> map`, we parameterize the key not the container then we will get heterogeneous container.

#### References
Effective Java Book  














