- 改变数组中每一个元素的内容(array_map + 匿名函数)
```
$names = array( "fred", "mary", "sally" );
    
print_r ( array_map( function( $name ) {
 return "Hello " . ucfirst( $name ) . "!";
}, $names ) );

输出: Array ( [0] => Hello Fred! [1] => Hello Mary! [2] => Hello Sally! )
参考自: http://www.notedeep.com/note/30/page/312
```
    
- 关于array_reduce
```
这个函数很神奇。看名字像是对数组做减法的函数，但其实远不止这点作用。我的理解是这个函数是一个迭代器，可以用来做一些很神奇的操作。

$result = array_reduce(companyList, function($itemResult, $item) use ($companyMap) {
  $companyEmail = $companyMao[$item['company_id]]；
  foreach ($companyEmail as $email) {
      $itemReasult[$email]['timezone] = item['timezone'];
  }
  return $itemResult;
}, $result);

其中，$result作为function中$itemResult的一个初始参数传递进去，同时传递进函数体的还有use的$companyMap,作用范围在该函数体中。在该迭代函数中，每个迭代用了个foreach，返回的$itemresult作为下一个迭代的对象。
```

- 批量Update语句
```
1. sql结果：
UPDATE mytable SET
    myfield = CASE id
        WHEN 1 THEN 'value'
        WHEN 2 THEN 'value'
        WHEN 3 THEN 'value'
    END
WHERE id IN (1,2,3)

2. php拼装过程：
$sql = "update tbl_general_tag set order_num = case tag_id ";
$tagIdStr = implode(',', $tagIds);
foreach ($tagIds as $orderNum => $tagId) {
    $sql .= sprintf("when %d then %d ", $tagId, $orderNum+1);
}
$sql .= "end where user_id = $userId and tag_id in ($tagIdStr)";
```




