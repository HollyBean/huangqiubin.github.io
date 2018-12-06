## 多方法简单工厂模式
这种设计模式与我之前写的[普通简单工厂设计模式](https://github.com/HollyBean/huangqiubin.github.io/blob/master/general-simple-factory-pattern.md "普通简单工厂模式")
(以下简称GSFP)一样，也不属于常见的设计模式；这种设计模式是对GSFP的改进，GSFP如果输入的参数有误，那么工厂将无法正常生产；而多方法简单工厂模式则是将多种
方法都集合到工厂类中，然后通过工厂实例来调用不同的方法；简图如下：

![image](http://pjb1sfuje.bkt.clouddn.com/vary-simple-factory-pattern.jpg "多方法简单工厂")

实现代码如下：
```
// 类接口
public interface Cooker{
    // 口号
    public void watchWord();
}


// 创建其实现类 1
public class CookieCooker implements Cooker{
    @Override
    public void watchWord() {
        System.out.println("I am a Cookie Cook!");
    }
}

// 创建其实现类 2
public class BreadCooker implements Cooker{
    @Override
    public void watchWord() {
        System.out.println("I am a bread Cook!");
    }
}

// 工厂类：注意这里的工厂类是没有接口的
public class CookerFactory{
    // 这里不再需要参数
    public Cooker produce(){
        public Cooker produceCookieCooker(){
            return new CookieCooker();
        }
        public Cooker produceBreadCooker(){
            return new BreadCooker();
        }
    }
}

// 测试类
public class FactoryTest{
    public static void main(String[] args) {
        CookerFactory factory = new CookerFactory()
        Cooker cooker = factory.produceCookieCooker();
        cooker.watchWord();
    }
}
```
