```scala
def get(key:A):Option[B] = {
		if (contains(key))
				Some(getValue(key))
		else
				None
}
```

Nil 表示长度为0的List

### Scala isEmpty、nonEmpty、idDefined

```scala
!seq.isEmpty -> seq.nonEmpty
seq.size == 0 -> seq.isEmpty
seq.size != 0 -> seq.nonEmpty
!(seq.length > 1) -> seq.isEmpty
!option.isEmpty -> option.isDefined
option == None -> option.isEmpty
option != None -> option.isDefined

```

### Scala关键词-lazy

**Scala中使用关键字lazy来定义惰性变量，实现延迟加载(懒加载)。** 
**惰性变量只能是不可变变量，并且只有在调用惰性变量时，才会去实例化这个变量。**

在**Java**中，要实现延迟加载(懒加载)，需要自己手动实现。一般的做法是这样的:

```java
public class JavaLazyDemo {
    private String name;

    //初始化姓名为huangbo
    private String initName(){
        return "huangbo";
    }

    public String getName(){
        //如果name为空，进行初始化
        if(name == null){
            name = initName();
        }
        return  name;
    }

}
```

在Scala中对延迟加载这一特性提供了语法级别的支持:

```scala
lazy val name = initName()
```

使用lazy关键字修饰变量后，只有在使用该变量时，才会调用其实例化方法。也就是说在定义property=initProperty()时并不会调用initProperty()方法，只有在后面的代码中使用变量property时才会调用initProperty()方法。

如果**不使用lazy关键字对变量修饰**，那么变量property是立即实例化的:

```scala
object ScalaLazyDemo {
  def init():String = {
    println("huangbo 666")
    return "huangbo"
  }

  def main(args: Array[String]): Unit = {
    val name = init();
    println("666")
    println(name)
  }
}
//-------------------
output:
huangbo 666
666
huangbo
```

上面的property没有使用lazy关键字进行修饰，所以property是立即实例化的，调用了initName()方法进行实例化。

**使用Lazy进行修饰**

```scala
object ScalaLazyDemo {
  def init():String = {
    println("huangbo 666")
    return "huangbo"
  }

  def main(args: Array[String]): Unit = {
    lazy val name = init();
    println("666")
    println(name)
  }
}
//---------------------
output:
666
huangbo 666
huangbo
```



## scala关键词-final

`final`是一个关键字，用于防止超类成员继承为派生类。也可以声明`final`变量，方法和类。

