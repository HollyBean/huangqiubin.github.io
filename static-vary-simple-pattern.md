## 静态多方法简单工厂模式
这种模式是对多方法[简单工厂模式](https://github.com/HollyBean/huangqiubin.github.io/blob/master/vary-simple-factory-pattern.md)的改进，
静态多方法简单工厂模式，顾名思义，就是将工厂类中的多个方法都设置为静态方法，这样，在调用的时候就无需实例化一个工厂类对象了．而是可以直接通过工厂类类名来
生产实现类；简图如下：


![image](http://pjb1sfuje.bkt.clouddn.com/static-vary-simple-pattern.jpg)


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
    public static Cooker produceCookieCooker(){
        return new CookieCooker();
    }
    public static Cooker produceBreadCooker(){
        return new BreadCooker();
    }
}

// 测试类
public class FactoryTest{
    public static void main(String[] args) {
        Cooker cooker = CookerFactory.produceCookieCooker();
        cooker.watchWord();
    }
}
```
