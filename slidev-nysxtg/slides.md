---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
---

# 设计模式学习汇报

软件8班——陈艺夫

<div class="abs-br m-6 flex gap-2">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white  bg-opacity-10">
    开始汇报 <carbon:arrow-right class="inline"/>
  </span>
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---

# 什么是设计模式？
设计模式（Design pattern）是一套被反复使用、多数人知晓的、经过分类编目的、代码设计经验的总结。
<br>
<br>

- 📝 **目的** - 为了可重用代码、让代码更容易被他人理解、保证代码可靠性。
- 🎨 **影响** - 设计模式于己于他人于系统都是多赢的，设计模式使代码编制真正工程化，设计模式是软件工程的基石，如同大厦的一块块砖石一样。
- 🌟 **分类** -主要分为三类。 

          📤创建型模式：对象实例化的模式，创建型模式用于解耦对象的实例化过程。
          📤结构型模式：把类或对象结合在一起形成一个更大的结构。
          📤行为型模式：类和对象如何交互，及划分责任和算法。
- 🛠 **详情** - 查看[详细分类](https://img-blog.csdnimg.cn/20190410154344878.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0MTE1ODk4,size_16,color_FFFFFF,t_70)
<br>
<br>

了解更多 [设计模式](https://blog.csdn.net/qq_34115898/article/details/89185073?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165078129516781818711122%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165078129516781818711122&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-89185073.142^v9^pc_search_result_control_group,157^v4^control&utm_term=%E4%BB%80%E4%B9%88%E6%98%AF%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F&spm=1018.2226.3001.4187)

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# 单例模式（Singleton）

在内存中只会创建且仅创建一次对象的设计模式。

- **用途** - 在程序中多次使用同一个对象且作用相同时，为了防止频繁地创建对象使得内存飙升，单例模式可以让程序仅在内存中创建一个对象，让所有需要调用的地方都共享这一单例对象。
- **特点** - 只能有一个实例；必须自己创建自己的唯一实例；必须给所有其他对象提供这一实例。
- **模式动机** - 让类自身负责保存它的唯一实例。这个类可以保证没有其他实例被创建，并且它可以提供一个访问该实例的方法。

<img 
  class="w-105"
  src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4ubmxhcmsuY29tL3l1cXVlLzAvMjAyMC9wbmcvMTY5NDAyOS8xNTk0NTE1MTI2Njk4LTg5NmU2NDQzLTBmOWUtNGM4Yy1iNGEwLWJiMDRjOWUxY2I2ZC5wbmc?x-oss-process=image/format,png"
/>

<style>
img{
  position: relative;
	left: 20%;
}
</style>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# 懒汉式
懒汉式创建对象的方法是在程序使用对象前，先判断该对象是否已经实例化（判空）。
<br>
若已实例化直接返回该类对象。否则则先执行实例化操作。

```ts {all|8,15|9-10|all}
public class Singleton {
    private static volatile Singleton singleton;
    private Singleton(){}
    public static Singleton getInstance() {
      if (singleton == null) {  
          synchronized(Singleton.class) { 
              if (singleton == null) { 
                  singleton = new Singleton();
              }
          }
      }
      return singleton;
    }
}
```

<arrow v-click="3" x1="430" y1="350" x2="320" y2="285" color="#564" width="3" arrowSize="1" />

🌟 **又称：Double Check（双重校验） + Lock（加锁）**

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# 饿汉式
饿汉式在类加载时已经创建好该对象，在程序调用时直接返回该单例对象即可。
<br>
即我们在编码时就已经指明了要马上创建这个对象，不需要等到被调用时再去创建。

```ts {all|3-4|9|all}
public class Singleton{
    
    private static final Singleton singleton 
                            = new Singleton();
    
    private Singleton(){}
    
    public static Singleton getInstance() {
        return singleton;
    }
}
```

<arrow v-click="3" x1="400" y1="450" x2="310" y2="360" color="#564" width="3" arrowSize="1" />


<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---
# 枚举实现

- **举个简单的例子：**
```ts {}
public enum Singleton {
    INSTANCE;
    
    public void doSomething() {
      System.out.println("这是枚举类型的单例模式！");
    }
}
```

- **优势1** -代码对比饿汉式与懒汉式来说，更加地简洁。
- **优势2** -不需要做任何额外的操作去保证对象单一性与线程安全性。
- **优势3** -使用枚举可以防止调用者使用反射、序列化与反序列化机制强制生成多个单例对象，破坏单例模式。

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---

# 常见问题1：指令重排序问题
指令重排序是指：JVM在保证最终结果正确的情况下，可以不按照程序编码的顺序执行语句，尽可能提高程序的性能。

<img 
  class="w-250"
  src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4ubmxhcmsuY29tL3l1cXVlLzAvMjAyMC9wbmcvMTY5NDAyOS8xNTk0NTIyMzkwNzk3LTRkZjBkMDA4LTM3MmMtNDkxZi04YjlhLWY4NjBmODAzNzFhYi5wbmc?x-oss-process=image/format,png"
/>
<br>

- **创建对象三步走：** 为singleton分配内存空间；初始化singleton对象；将singleton指向分配好的内存空间。
- **问题：** 例如有两线程A、B时，其中线程B可能获取到未初始化的singleton对象，就会报NPE异常。
- **解决方案：** 使用volatile关键字修饰的变量，可以保证其指令执行的顺序与程序指明的顺序一致，不会发生顺序变换，这样在多线程环境下就不会发生NPE异常了。
- **PS：** volatile还有个作用，可以保证其内存可见性。

---

# 常见问题2：反射与序列化问题
无论是完美的懒汉式还是饿汉式，都可以被反射与序列化破坏掉（产生多个对象）。

- **利用反射破坏单例模式：** 
```ts {all|2|3|4|5|all}
public static void main(String[] args) {
    Constructor<Singleton> construct = Singleton.class.getDeclaredConstructor();
    construct.setAccessible(true); 
    Singleton obj1 = construct.newInstance(); 
    Singleton obj2 = Singleton.getInstance(); 
    System.out.println(obj1 == obj2); // false
}
```

- **利用序列化与反序列化破坏单例模式：**
```ts {all|2,3|4|5|7|all}
public static void main(String[] args) {
    ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("Singleton.file"));
    oos.writeObject(Singleton.getInstance());
    File file = new File("Singleton.file");
    ObjectInputStream ois =  new ObjectInputStream(new FileInputStream(file));
    Singleton newInstance = (Singleton) ois.readObject();
    System.out.println(newInstance == Singleton.getInstance()); // false
}
```

---

# 单例模式优劣总结：

<div grid="~ cols-2 gap-4">

  <div>

  - **优势：**
  <br>

  1.保证java应用程序中一个类只有一个实例存在。
  <br>

  2.可以防止数据的冲突，节省内存，节约资源，对于一般频繁创建和销毁对象的可以使用单例模式。因为它限制了实例的个数，有利于java垃圾回收。
  <br>
  （例如：数据库连接池、httpclient连接单例）
  <br>

  3.Singleton通过将构造方法限定为private避免了类在外部被实例化。在同一个虚拟机范围内，Singleton的唯一实例只能通过getInstance()方法访问。
  <br>

  </div>

  <div>

  - **劣势：**
  <br>

  1.为节省资源创建单例模式，可能会导致共享连接池的对象程序过多，出现连接池溢出等问题。
  <br>

  2.不适用于变化的对象。
  <br>
  如果同一类型的对象总是要在不同的用例场景发生变化，单例就会引起数据的错误，不能保存彼此的状态。
  <br>

  3.其构造函数是静态的。所以在继承单例时，出现问题，不能被子类继承。
  <br>

  </div>

</div>


---
class: px-20
---

# 抽象工厂模式：
定义了一个接口用于创建相关或有依赖关系的对象族，而无需明确指定具体类。

<div grid="~ cols-2 gap-2" m="-t-2">

```yaml
---
优点: 
1.具体产品在应用层的代码隔离，无需关系创建的细节。
2.将一个系列的产品统一到一起创建。
---
```

```yaml
---
缺点:
1.规定了所有可能被创建的产品集合，产品族中扩展新的产品困难。
2.增加了系统的抽象性和理解难度。
---
```

```ts {}
//工厂接口
public interface AbsFactory {
       Pizza CreatePizza(String ordertype) ;
}

//main方法
public class PizzaStore {
       public static void main(String[] args) {
              OrderPizza mOrderPizza;
              mOrderPizza = new OrderPizza("London");
       }
}
```

```ts {}
//工厂实现
public class LDFactory implements AbsFactory {
       @Override
       public Pizza CreatePizza(String ordertype) {
              Pizza pizza = null;
              if ("cheese".equals(ordertype)) {
                     pizza = new LDCheesePizza();
              } else if ("pepper".equals(ordertype)) {
                     pizza = new LDPepperPizza();
              }
              return pizza;
       }
}
```

</div>

“Pizza工厂”案例的[分析类图](https://img-blog.csdnimg.cn/20190609001610898.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0ExMzQyNzcy,size_16,color_FFFFFF,t_70)
---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---
# 🤹谢谢观看

<style>
h1 {
  margin-top: 200px;
  text-align: center;
  font-size: 60px; 
}
</style>

