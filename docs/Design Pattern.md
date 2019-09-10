> 参考阅读
> 1. [PHP 设计模式全集2018](<https://learnku.com/docs/php-design-patterns/2018>)
> 2. [Laravel China 设计模式](<http://laravel-china.github.io/php-the-right-way/pages/Design-Patterns.html>)

##### 工厂模式

```
<?php
class Automobile
{
    private $vehicleMake;
    private $vehicleModel;

    public function __construct($make, $model)
    {
        $this->vehicleMake = $make;
        $this->vehicleModel = $model;
    }

    public function getMakeAndModel()
    {
        return $this->vehicleMake . ' ' . $this->vehicleModel;
    }
}

class AutomobileFactory
{
    public static function create($make, $model)
    {
        return new Automobile($make, $model);
    }
}

// 用工厂的 create 方法创建 Automobile 对象
$veyron = AutomobileFactory::create('Bugatti', 'Veyron');

print_r($veyron->getMakeAndModel()); // outputs "Bugatti Veyron"
```

##### 单例模式 
- 暂时不常用 todo

##### 策略模式
- 个人理解:这种设计有点类似于switch的控制结构,把业务解耦,针对一些角色,种类等可以枚举或者新增不能一起太大变化的业务
- 使用策略模式，你可以把一族不同的算法（业务）封装到不同的类中，使 client 类可以在不知道具体实现的情况下选择实例化其中一个算法。策略模式有几种不同的变体，最简单的是下面这种：
- 第一段代码展示了一组输出算法，分别具体实现了 `OutputInterface` 的 `load` 方法，返回序列化结果，json 和数组：

```
<?php

interface OutputInterface
{
   public function load();
}

class SerializedArrayOutput implements OutputInterface
{
   public function load()
   {
       return serialize($arrayOfData);
   }
}

class JsonStringOutput implements OutputInterface
{
   public function load()
   {
       return json_encode($arrayOfData);
   }
}

class ArrayOutput implements OutputInterface
{
   public function load()
   {
       return $arrayOfData;
   }
}
```
通过像上面这样把不同类型的输出算法封装起来，其他的开发者可以很容易地在不影响 client 代码的情况下添加新的输出类型。

每个具体的输出类实现了 `OutputInterface` —— 这有两个目的，第一是它提供了一个所有输出类都必须遵守的契约，第二，你将会在本文后面的部分看到，通过实现公共的接口，你可以利用[类型约束](http://php.net/language.oop5.typehinting)保证 client 中使用的输出类必须是实现了 `OutputInterface` 的类。

接下来的一小段代码展示了一个 client 类如何使用其中一个输出算法，并可以在运行时根据需要选用不同的算法。

```
<?php
class SomeClient
{
   private $output;

   public function setOutput(OutputInterface $outputType)
   {
       $this->output = $outputType;
   }

   public function loadOutput()
   {
       return $this->output->load();
   }
}
```

上面的 `client`类有一个必须在运行时设置的私有属性，并且是“OutputInterface”类型的。 一旦这个属性被设置为具体的实例（三个输出类中之一的实例），并且 `loadOutput` 方法被调用，那么它的 `load` 方法就会被调用，返回回序列化结果或 json 或数组。

```
<?php
$client = new SomeClient();

// Want an array?
$client->setOutput(new ArrayOutput());
$data = $client->loadOutput();

// Want some JSON?
$client->setOutput(new JsonStringOutput());
$data = $client->loadOutput();
```
