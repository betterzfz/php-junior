- 请分别定义三个变量，值分别为5，2，9，通过条件控制结构判断三个变量谁最大，输出变量名称和对应的值。
```php
$x = 5;
$y = 2;
$z = 9;
if ($x >= $y) {
    if ($x >=$z) {
        echo '最大值为：$x='.$x;
    } else  {
        echo '最大值为：$z='.$z;
    }
} else {
    if ($y >= $z) {
        echo '最大值为：$y='.$y;
    } else  {
        echo '最大值为：$z='.$z;
    }
}
```
- 对于给定的值为8的变量，依次判断0-9这十个数中与之相等的数字，当相等的时候输出‘找到了’。
```php
$x = 8;
switch ($x) {
    case 0:
        echo '找到了';
        break;
    case 1:
        echo '找到了';
        break;
    case 2:
        echo '找到了';
        break;
    case 3:
        echo '找到了';
        break;
    case 4:
        echo '找到了';
        break;
    case 5:
        echo '找到了';
        break;
    case 6:
        echo '找到了';
        break;
    case 7:
        echo '找到了';
        break;
    case 8:
        echo '找到了';
        break;
    case 9:
        echo '找到了';
        break;
}
```
- 请分别使用三种循环形式计算1到100的和，要求通过条件表达式退出循环。
```php
$i = 1;
$sum = 0;
while ($i <= 100) {
    $sum += $i;
    $i++;
}
$i = 1;
$sum = 0;
do {
    $sum += $i;
    $i++;
} while ($i <= 100);
$sum = 0;
for ($i = 0;$i <= 100;$i++) {
    $sum += $i;
}
```
- 请分别使用三种循环形式计算1到100的和，要求在循环体中退出循环。
```php
$i = 1;
$sum = 0;
while (TRUE) {
    if ($i > 100) {
        break;
    }
    $sum += $i;
    $i++;
}
$i = 1;
$sum = 0;
do {
    if ($i > 100) {
        break;
    }
    $sum += $i;
    $i++;
} while (TRUE);
$sum = 0;
for ($i = 0;;$i++) {
    if ($i > 100) {
        break;
    }
    $sum += $i;
}
```
- 请分别使用三种循环形式遍历一个至少有3个元素的素组，分别输出数组元素的键和值，要求通过条件表达式退出循环。
```php
$arr = [1, 2, 3];
while (list($key, $value) = each($arr)) {
    echo 'key:'.$key.'=>'.'value:'.$value;
    echo '<br/>';
}
reset($arr);
list($key, $value) = each($arr);
do {
    echo 'key:'.$key.'=>'.'value:'.$value;
    echo '<br/>';
} while (list($key, $value) = each($arr));
reset($arr);
for (;list($key, $value) = each($arr);) {
    echo 'key:'.$key.'=>'.'value:'.$value;
    echo '<br/>';
}
```
- 请分别使用三种循环形式遍历一个至少有3个元素的素组，分别输出数组元素的键和值，要求在循环体中退出循环。
```php
$arr = [1, 2, 3];
while (TRUE) {
    if (list($key, $value) = each($arr)) {
        echo 'key:'.$key.'=>'.'value:'.$value;
        echo '<br/>';
    } else {
        break;
    }
}
reset($arr);
do {
    if (list($key, $value) = each($arr)) {
        echo 'key:'.$key.'=>'.'value:'.$value;
        echo '<br/>';
    } else {
        break;
    }
} while (TRUE);
reset($arr);
for (;;) {
    if (list($key, $value) = each($arr)) {
        echo 'key:'.$key.'=>'.'value:'.$value;
        echo '<br/>';
    } else {
        break;
    }
}
```