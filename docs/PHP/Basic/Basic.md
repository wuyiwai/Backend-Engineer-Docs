##### 参考文档
1. [数组函数](https://secure.php.net/manual/zh/ref.array.php)
2. [字符串函数](https://secure.php.net/manual/zh/ref.strings.php)

##### 数组
- [array_column](https://secure.php.net/manual/zh/function.array-column.php) - 返回数组中指定的一列
- [array_combine](https://secure.php.net/manual/zh/function.array-combine.php) -创建一个数组，用一个数组的值作为其键名，另一个数组的值作为其值 
- [array_count_values](https://secure.php.net/manual/zh/function.array-count-values.php) - 统计数组中所有的值出现的次数
- [array_diff](https://secure.php.net/manual/zh/function.array-diff.php) - 计算数组的差集
- [array_fiill_keys](https://secure.php.net/manual/zh/function.array-fill-keys.php) - 使用指定的键和值填充数组
- [array_fill](https://secure.php.net/manual/zh/function.array-fill.php) - 用给定的值填充数组
- [array_filter](https://php.net/manual/zh/function.array-filter.php) - 用回调函数过滤数组中的单元 - **真的会过滤**
- [array_key_exists](https://php.net/manual/zh/function.array-key-exists.php) - 检查数组是否有指定的键名或索引
- [array_map](https://secure.php.net/manual/zh/function.array-map.php) - 为数组的每个元素应用回调函数
- [array_merge](https://php.net/manual/zh/function.array-merge.php) - 合并一个或多个数组 - **会重建索引**
- [array_multisory](https://php.net/manual/zh/function.array-multisort.php) - 对多个数组或多维数组进行排序
- [array_pop](https://secure.php.net/manual/zh/function.array-pop.php) -  弹出数组最后一个单元（出栈）
- [array_push](https://php.net/manual/zh/function.array-push.php) - 将一个或多个单元压入数组的末尾
- [array_shift](https://php.net/manual/zh/function.array-shift.php) - 将数组开头的单元移出数组
- [array_unshift](https://php.net/manual/zh/function.array-unshift.php) - 在数组开头插入一个或多个单元
- [array_values](https://secure.php.net/manual/zh/function.array-values.php) - 返回数组中所有的值并重新建立数字索引
- [in_array](https://secure.php.net/manual/zh/function.in-array.php) - 检查数组中是否存在某个值
- [list](https://secure.php.net/manual/zh/function.list.php) - 把数组中的值赋给一组变量
- [array_reduce](https://secure.php.net/manual/zh/function.array-reduce.php) - 用回调函数迭代地将数组简化为单一的值 - 可以用来做一些迭代操作.比如对一个数组的每一项做一些操作.跟foreach有点像

##### 字符串
- [explode](https://secure.php.net/manual/zh/function.explode.php) - 使用一个字符串分割另一个字符串
- [implode](https://secure.php.net/manual/zh/function.implode.php) - 将一个一维数组的值转化为字符串
- [money_format](https://secure.php.net/manual/zh/function.money-format.php) - 将数字格式化成货币字符串 - **很有意思**
- [parse_str](https://secure.php.net/manual/zh/function.parse-str.php) - 将字符串解析成多个变量
- [str_repeat](https://secure.php.net/manual/zh/function.str-repeat.php) - 重复一个字符串
- [strrev ](https://secure.php.net/manual/zh/function.strrev.php) - 反转字符串
- [strpos](https://secure.php.net/manual/zh/function.strpos.php) - 查找字符串首次出现的位置

##### 类型判断
- [is_numeric](<https://www.php.net/manual/zh/function.is-numeric.php>) -检测变量是否为数字或数字字符串 -- eg:array_filter(array, 'is_numeric')

##### 匿名函数
- 匿名函数（Anonymous functions），也叫闭包函数（*closures*），允许 临时创建一个没有指定名称的函数。最经常用作回调函数（[callback](https://php.net/manual/zh/language.pseudo-types.php#language.types.callback)）参数的值。当然，也有其它应用的情况。
- 匿名函数目前是通过 [Closure](https://php.net/manual/zh/class.closure.php) 类来实现的。
- 闭包可以从父作用域中继承变量。 任何此类变量都应该用 *use* 语言结构传递进去。 **PHP 7.1 起，不能传入此类变量： [superglobals](https://php.net/manual/zh/language.variables.predefined.php)、 $this 或者和参数重名。**

##### 等于判断
```
$a = 0;
$b = null;
$c = '';
$arr_one = [];
$arr_two = [''];
$arra_three = ['', 1];

echo 0 == null; // 1
echo 0 == false; //1
echo false == null; //1

if (0) echo "1";  // 无输出
if (null) echo "2";  // 无输出
if (false) echo "3";  // 无输出
if ([]) echo "4";  // 无输出
if ('') echo "5";  // 无输出
if (['']) echo '6'; //6
```

