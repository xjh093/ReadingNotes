1.软件测试类型：

 - 单元测试-Unit Tests，

 - 集成测试-Integration Tests，

 - 系统测试-System Tests

 ---

 2.单元测试是指对软件系统中最小可测试单元进行的检查和验证。

 --- 

 3.单元，一般批功能不可再分割的模块或者函数。

 ---  

 4.集成测试是单元测试的逻辑扩展，最简单的形式是把两个已经测试过的单元组合成一个组件，并测试它们之间的接口。

 ---  

 5.组件，是指多个单元的集成聚合。

 ---  

 6.iOS功能集成测试其实就是功能测试。

 ---  

 7.系统测试是将已经确认的软件、计算机硬件、外设、网络等其他元素结合在一起，进行信息系统组装测试和确认测试。

 ---  

 8.iOS单元测试的辅助工具：

 OCHamcrest:https://github.com/hamcrest/OCHamcrest

 OCMockito:https://github.com/jonreid/OCMockito

 ---  

 9.UI Automation自动化测试第三方工具：

 TuneupJs:https://github.com/vkolgi/tuneup_js

 

 下载代码：

 git clone https://github.com/vkolgi/tuneup_js.git tuneup

 

 使用规则:

 1).在文件加入TuneupJs的import:

 #import "tuneup/tuneupljh"

 

 2).测试方法需要使用以下方式定义:

```
 test("测试方法的简要说明",

    function(){

    //具体的测试行为加上结果判断的断言

 });
```
 

 iOS测试工具中，ynm3k的UI控件遍历优势较大

 ynm3k:https://github.com/douban/ynm3k

 

 下载代码：

 git clone https://github.com/douban/ynm3k.git ynm3k

 初始化:

 cd ynm3k

 sh setup.sh

 

 在文件中导入：#import "ynm3k/robot4i0s/importAll.js"

--- 

 10.测试类型：

 - 功能测试。

 - 兼容性测试。

 - 网络流量测试。

 - 升级测试。

 - 性能测试。

 - 稳定性测试。

  --- 

 11.基于UI Automation写的猴子测试脚本：

 https://github.com/douban/ynm3k/blob/master/robot4ios/util/iOSMonkey2.js
