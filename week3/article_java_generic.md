
#### java generics 
Java generics is useful when we don't know the object type of class's properties or function's parameters. It allows object type to be a parameter to class or method using the following syntax.
```
class <T>
interface <T>
<T> function(T name)
```
Note: primitives are not allowed in generics.
here's an example of generic class. suppose we have a `HeroTeamMembers` class to record the hero team, we can't put an Avenger member into XMen team, so we use a generic type parameter to specify the team of heros.
```
public class HeroTeamMembers<T> {
  List<T> heros = new ArrayList<T>();
  T leader;
  public HeroTeamMembers() {

  }

  public void addHero(T hero){
    this.heros.add(hero);
  }

  public void setLeader(T leader){
    this.leader = leader;
  }

  public List<T> getHeros(){
    return this.heros;
  }

  public T getLeader(){
    return this.leader;
  }

  public static void main(String[] args) {
    HeroTeamMembers<XMen> xmenMembers = new HeroTeamMembers<XMen>();
    xmenMembers.addHero(new XMen("Storm"));
    xmenMembers.addHero(new XMen("Beast"));
    System.out.println(xmenMembers.getHeros());

    Avenger avenger = new Avenger("Iron Man");
    HeroTeamMembers<Avenger> avengerMembers = new HeroTeamMembers<Avenger>();
    avengerMembers.addHero(new Avenger("Iron Man"));
    avengerMembers.addHero(new Avenger("Captain America"));

    System.out.println(avengerMembers.getHeros());
  }
}

```

#### what's the benefits of generics
 * type safety.
   To be compatible with previous java version, raw type like `List` not `List<String>` exists. But the compiler doesn't know the element type of raw type `List`, so the following code will compile ok but run error.
   ```
   List list = new ArrayList();
   list.add("Iron Man");
   list.add(1);
   for (Object object: )
   ```
   by using generics we have a compile type check which prevents `ClassCastExceptions` and removes the need for casting.
 * avoid code duplication.
 * generic algorithm for different types of objects.

#### how generics works
Generics is implemented using **Type erasure**, the compiler erases all type related information and no type related information is available during runtime. This is done to ensure binary backward compatibility of Java written in previous non-generic versions. The type arguments are only used for compilation and linking, not for execution. 

Type erasure:
all generic type information is erased and type parameters is replaced with their bound type, which is Object if not explicit bound is specified. 
##### Class Type Erasure
```
public class List<E>{ private E[] list; ...}
```
to
```
public class List { private Object[] list; ...}
```

```
public class List<E extends Comparable<E>>{ private E[] list; ...}
```
to
```
public class List { private Comparable[] list; ...}
```

##### Method Type Erasure
```
public <E> void print(E[] array)
```
to
```
public void print(Object[] array)
```

```
public <E extends Comparable<E>> void print(E[] array)
```
to
```
public void print(Comparable[] array)
```

##### Bridge Methods
Bridge methods are synthetic methods to implement some of Java language features.
```public class IntegerStack extends Stack<Integer>{
        public void push(Integer value){
            super.push(value);
        }
    }
```
to
```
public class IntegerStack extends Stack{
    public void push(Object value){
        push((Integer)value);
    }
    public void push(Integer value){
        super.push(value);
    }
}
```
#### expanded usage
##### Bounded Types
if we want to restrict the generic type to a specific type or to a subtype of that specific type, we can use `<T extends UpperBoundType>`. Similarly, restricting to a supertype of that specific type, use `<T super LowerBoundType>`.

##### Wildcards
In some cases, we don't need to know the type of a parameter. The `?` wildcard character can be used to represent an unknown type using generic code.
for example:
```
private <T> boolean contains(List<?> list, T obj)
```
oftentimes wildcards with bounded types are used to restrict the parameter type.
```
private <T> boolean contains(List<? extends Number> list, T obj)
```

#### References
[how-exactly-do-generics-work](https://stackoverflow.com/questions/27606449/how-exactly-do-generics-work)
[java-type-erasure](https://www.baeldung.com/java-type-erasure)















