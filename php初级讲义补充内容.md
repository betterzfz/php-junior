* `php`实际上有四种不同的开始和结束标记，常规标记为`<?php echo 'hello, world!'; ?>`，短标记为`<?= 'hello, world!' ?>`或`<? echo 'hello, world!'; ?>`，带`<script>`标签方式的`<script language="php">echo 'hello, world!';</script>`，还有`asp`风格的标记如`<%= 'hello, world!' %>`或`<% echo 'hello, world'; %>`，其中常规标记和带`<script>`标签方式的始终是可用的，短标记在`php5.4`之前是要配置`php.ini`，虽然`php5.4`及以后的版本提供了对短标记的直接支持，但是在未来的版本中可能会移除该特性，而`asp`风格的标记是需要配置的。
* 数据类型的转换
* 预定义变量
* 变量的范围
* 伪类型和伪变量
* 反引号运算符在激活了安全模式或者关闭了`shell_exec()`时是无效的