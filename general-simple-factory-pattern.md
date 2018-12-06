## 普通简单工厂模式
简单普通工厂模式不属于常见的23种设计模式，只是我在学习的过程中看到了，所以也就记录一下；

在我学习的过程中，发现众多讲到设计模式的博客，书籍都是使用UML来说明的，虽然使用这个很规范，而且也能很具体地表达观点；
但是我个人认为还是不够直观，所以在学习的时候整理了一个简略图．如下：

![image](http://pjb1sfuje.bkt.clouddn.com/general-simple-factory-pattern.jpg "图解普通工厂模式")

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
public class CookerFactory {
    public Cooker produce(String type){
        // 根据输入的参数选择具体的实现类
        if ("cookie".equals(type)) {
            return new CookieCooker();
        }else if ("bread".equals(type)) {
            return new BreadCooker();
        }else{
            System.out.println("You are not our own person...");
            return null;
        }
    }
}

// 测试类
public class FactoryTest{
    public static void main(String[] args) {
        CookerFactory factory = new CookerFactory();
        Cooker cooker = factory.produce("cookie");
        cooker.watchWord();
    }
}
```
