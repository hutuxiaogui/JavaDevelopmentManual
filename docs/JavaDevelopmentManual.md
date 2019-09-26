

# 一、 编程规约

## (一) 命名风格

1. <font color=#C00000>**【强制】**</font>代码中的命名均不能以下划线或美元符号开始，也不能以下划线或美元符号结束。

	<font color=#FF4500>**反例**</font>：_name /    name / $name / name_ / name$ / name 

2. <font color=#C00000>**【强制】**</font>代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。

	<font color=#977C00>**说明**</font>：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，纯拼音命名方式更要避免采用。
	<font color=#099B5D>**正例**</font>：renminbi / alibaba / taobao / youku / hangzhou  等国际通用的名称，可视同英文。

	<font color=#FF4500>**反例**</font>：DaZhePromotion [打折] / getPingfenByName() [评分] / int  某变量 = 3

3. <font color=#C00000>**【强制】**</font>类名使用 UpperCamelCase 风格，但以下情形例外：DO / BO / DTO / VO / AO/ PO / UID 等。
  
	<font color=#099B5D>**正例**</font>：JavaServerlessPlatform / UserDO / XmlService / TcpUdpDeal / TaPromotion

	<font color=#FF4500>**反例**</font>：javaserverlessplatform / UserDo / XMLService / TCPUDPDeal / TAPromotion

4. <font color=#C00000>**【强制】**</font>方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式。

	<font color=#099B5D>**正例**</font>： localValue / getHttpMessage() / inputUserId

5. <font color=#C00000>**【强制】**</font>常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。

	<font color=#099B5D>**正例**</font>：MAX_STOCK_COUNT / CACHE_EXPIRED_TIME

	<font color=#FF4500>**反例**</font>：MAX_COUNT / EXPIRED_TIME

6. <font color=#C00000>**【强制】**</font>抽象类命名使用 Abstract 或 Base 开头；异常类命名使用 Exception 结尾；测试类命名以它要测试的类的名称开始，以 Test 结尾。

7. <font color=#C00000>**【强制】**</font>类型与中括号紧挨相连来表示数组。

	<font color=#099B5D>**正例**</font>：定义整形数组 int[] arrayDemo;

	<font color=#FF4500>**反例**</font>：在 main 参数中，使用 String args[]来定义。

8. <font color=#C00000>**【强制】**</font>POJO 类中布尔类型变量都不要加 is 前缀，否则部分框架解析会引起序列化错误。

	<font color=#977C00>**说明**</font>：在本文 MySQL 规约中的建表约定第一条，表达是与否的值采用 is_xxx 的命名方式，所以，需要在<resultMap>设置从 is_xxx 到 xxx 的映射关系。

	<font color=#FF4500>**反例**</font>：定义为基本数据类型 Boolean isDeleted 的属性，它的方法也是 isDeleted()，RPC 框架在反向解析的时候，“误以为”对应的属性名称是 deleted，导致属性获取不到，进而抛出异常。

9. <font color=#C00000>**【强制】**</font>包名统一使用小写，点分隔符之间有且仅有一个自然语义的英语单词。包名统一使用单数形式，但是类名如果有复数含义，类名可以使用复数形式。

	<font color=#099B5D>**正例**</font>：应用工具类包名为 com.alibaba.ai.util、类名为 MessageUtils（此规则参考 spring 的框架结构）

10. <font color=#C00000>**【强制】**</font>避免在子父类的成员变量之间、或者不同代码块的局部变量之间采用完全相同的命名，使可读性降低。

	<font color=#977C00>**说明**</font>：子类、父类成员变量名相同，即使是 public 类型的变量也是能够通过编译，而局部变量在同一方法内的不同代码块中同名也是合法的，但是要避免使用。对于非 setter/getter 的参数名称也要避免与成员变量名称相同。

	<font color=#FF4500>**反例**</font>：
    
```java
public class ConfusingName { 
	public int age;
	// 非 setter/getter 的参数名称，不允许与本类成员变量同名
	public void getData(String alibaba) { 
		if(condition) {
			final int money = 531;
			// ...
		}

		for (int i = 0; i < 10; i++) {
			// 在同一方法体中，不允许与其它代码块中的 money 命名相同
			final int money = 615;
			// ...
		}
	}
}

class Son extends ConfusingName {
	// 不允许与父类的成员变量名称相同
	public int age;
}
```
11. <font color=#C00000>**【强制】**</font>杜绝完全不规范的缩写，避免望文不知义。

	<font color=#FF4500>**反例**</font>：AbstractClass“缩写”命名成 AbsClass；condition“缩写”命名成 condi，此类随意缩写严重降低了代码的可阅读性。

12. <font color=#FFC000>**【推荐】**</font>为了达到代码自解释的目标，任何自定义编程元素在命名时，使用尽量完整的单词组合来表达其意。

	<font color=#099B5D>**正例**</font>：在 JDK 中，表达原子更新的类名为：AtomicReferenceFieldUpdater。

	<font color=#FF4500>**反例**</font>：int a 的随意命名方式。

13. <font color=#FFC000>**【推荐】**</font>在常量与变量的命名时，表示类型的名词放在词尾，以提升辨识度。

	<font color=#099B5D>**正例**</font>：startTime / workQueue / nameList / TERMINATED_THREAD_COUNT

	<font color=#FF4500>**反例**</font>：startedAt / QueueOfWork / listName / COUNT_TERMINATED_THREAD

14. <font color=#FFC000>**【推荐】**</font>如果模块、接口、类、方法使用了设计模式，在命名时需体现出具体模式。

	<font color=#977C00>**说明**</font>：将设计模式体现在名字中，有利于阅读者快速理解架构设计理念。

	<font color=#099B5D>**正例**</font>： 
		public class OrderFactory; 
		public class LoginProxy;
		public class ResourceObserver;

15. <font color=#FFC000>**【推荐】**</font>接口类中的方法和属性不要加任何修饰符号（public  也不要加），保持代码的简洁性，并加上有效的 Javadoc 注释。尽量不要在接口里定义变量，如果一定要定义变量，肯定是与接口方法相关，并且是整个应用的基础常量。

	<font color=#099B5D>**正例**</font>：接口方法签名  void commit();

				接口基础常量  String COMPANY = "alibaba";

	<font color=#FF4500>**反例**</font>：接口方法定义  public abstract void f();

	<font color=#977C00>**说明**</font>：JDK8 中接口允许有默认实现，那么这个 default 方法，是对所有实现类都有价值的默认实现。

16. 接口和实现类的命名有两套规则：

	1）<font color=#C00000>**【强制】**</font>对于 Service 和 DAO 类，基于 SOA 的理念，暴露出来的服务一定是接口，内部的实现类用Impl 的后缀与接口区别。

	<font color=#099B5D>**正例**</font>：CacheServiceImpl 实现 CacheService 接口。

	2）<font color=#FFC000>**【推荐】**</font>如果是形容能力的接口名称，取对应的形容词为接口名（通常是–able 的形容词）。

	<font color=#099B5D>**正例**</font>：AbstractTranslator 实现 Translatable 接口。

17. <font color=#76923C>**【参考】**</font>枚举类名带上 Enum 后缀，枚举成员名称需要全大写，单词间用下划线隔开。

	<font color=#977C00>**说明**</font>：枚举其实就是特殊的类，域成员均为常量，且构造方法被默认强制是私有。

	<font color=#099B5D>**正例**</font>：枚举名字为 ProcessStatusEnum 的成员名称：SUCCESS / UNKNOWN_REASON。

18. <font color=#76923C>**【参考】**</font>各层命名规约：

	A)	Service/DAO 层方法命名规约

		1）	获取单个对象的方法用 get 做前缀。
		
		2）	获取多个对象的方法用 list 做前缀，复数形式结尾如：listObjects。
		
		3）	获取统计值的方法用 count 做前缀。
		
		4）	插入的方法用 save/insert 做前缀。
		
		5）	删除的方法用 remove/delete 做前缀。
		
		6）	修改的方法用 update 做前缀。

	B)	领域模型命名规约

		1）	数据对象：xxxDO，xxx 即为数据表名。
		
		2）	数据传输对象：xxxDTO，xxx 为业务领域相关的名称。
		
		3）	展示对象：xxxVO，xxx 一般为网页名称。
		
		4）	POJO 是 DO/DTO/BO/VO 的统称，禁止命名成 xxxPOJO。


## (二) 常量定义
## (三) 代码格式
## (四) OOP规约
## (五) 集合处理
## (六) 并发处理
## (七) 控制语句
## (八) 注释规约
## (九) 其它
# 二、异常日志
## (一) 异常处理
## (二) 日志规约
# 三、单元测试
# 四、安全规约
# 五、MySQL数据库
## (一) 建表规约
## (二) 索引规约
## (三) SQL语句
## (四) ORM映射
# 六、工程结构
## (一) 应用分层
## (二) 二方库依赖
## (三) 服务器
# 七、设计规约
# 附录：专有名词解释
1. **POJO**（Plain Ordinary Java Object）: 在本手册中，POJO 专指只有 setter / getter /
toString 的简单类，包括 DO/DTO/BO/VO 等。
2. **GAV**（GroupId、ArtifactctId、Version）: Maven 坐标，是用来唯一标识 jar 包。
3. **OOP**（Object Oriented Programming）: 本手册泛指类、对象的编程处理方式。
4. **ORM**（Object Relation Mapping）: 对象关系映射，对象领域模型与底层数据之间的转换，本文泛指 iBATIS, mybatis 等框架。
5. **NPE**（java.lang.NullPointerException）: 空指针异常。
6. **SOA**（Service-Oriented Architecture）:  面向服务架构，它可以根据需求通过网络对松散耦合的粗粒度应用组件进行分布式部署、组合和使用，有利于提升组件可重用性，可维护性。
7. **IDE**（Integrated Development Environment）:  用于提供程序开发环境的应用程序，一般包括代码编辑器、编译器、调试器和图形用户界面等工具，本《手册》泛指 IntelliJ IDEA 和
eclipse。
8. **OOM**（Out Of Memory）:  源于 java.lang.OutOfMemoryError，当 JVM 没有足够的内存来为对象分配空间并且垃圾回收器也无法回收空间时，系统出现的严重状况。
9. **一方库**：本工程内部子项目模块依赖的库（jar 包）。
10. **二方库**：公司内部发布到中央仓库，可供公司内部其它应用依赖的库（jar 包）。
11. **三方库**：公司之外的开源库（jar 包）。