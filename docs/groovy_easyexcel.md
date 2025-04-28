---
layout: default
title: groovy中使用easyexcel读取文件
description: groovy中使用easyexcel读取文件
---

# groovy 中使用easyexcel

## 问题：在groovy中使用easyexcel读取文件时，出现如下报错：
```java
com.alibaba.excel.exception.ExcelDataConvertException: Converter not found, convert NUMBER to org.codehaus.groovy.reflection.ClassInfo

	at com.alibaba.excel.util.ConverterUtils.doConvertToJavaObject(ConverterUtils.java:177)
	at com.alibaba.excel.util.ConverterUtils.convertToJavaObject(ConverterUtils.java:121)
	at com.alibaba.excel.util.ConverterUtils.convertToJavaObject(ConverterUtils.java:87)
	at com.alibaba.excel.read.listener.ModelBuildEventListener.buildUserModel(ModelBuildEventListener.java:145)
	at com.alibaba.excel.read.listener.ModelBuildEventListener.invoke(ModelBuildEventListener.java:37)
	at com.alibaba.excel.read.listener.ModelBuildEventListener.invoke(ModelBuildEventListener.java:30)
	at com.alibaba.excel.read.processor.DefaultAnalysisEventProcessor.dealData(DefaultAnalysisEventProcessor.java:109)
	at com.alibaba.excel.read.processor.DefaultAnalysisEventProcessor.endRow(DefaultAnalysisEventProcessor.java:50)
	at com.alibaba.excel.analysis.v07.handlers.RowTagHandler.endElement(RowTagHandler.java:66)
	at com.alibaba.excel.analysis.v07.handlers.sax.XlsxRowHandler.endElement(XlsxRowHandler.java:99)
	at java.xml/com.sun.org.apache.xerces.internal.parsers.AbstractSAXParser.endElement(AbstractSAXParser.java:610)
	at java.xml/com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl.scanEndElement(XMLDocumentFragmentScannerImpl.java:1718)
	at java.xml/com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl$FragmentContentDriver.next(XMLDocumentFragmentScannerImpl.java:2883)
	at java.xml/com.sun.org.apache.xerces.internal.impl.XMLDocumentScannerImpl.next(XMLDocumentScannerImpl.java:605)
	at java.xml/com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl.scanDocument(XMLDocumentFragmentScannerImpl.java:534)
	at java.xml/com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:888)
	at java.xml/com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:824)
	at java.xml/com.sun.org.apache.xerces.internal.parsers.XMLParser.parse(XMLParser.java:141)
	at java.xml/com.sun.org.apache.xerces.internal.parsers.AbstractSAXParser.parse(AbstractSAXParser.java:1216)
	at java.xml/com.sun.org.apache.xerces.internal.jaxp.SAXParserImpl$JAXPSAXParser.parse(SAXParserImpl.java:635)
	at com.alibaba.excel.analysis.v07.XlsxSaxAnalyser.parseXmlSource(XlsxSaxAnalyser.java:239)
	at com.alibaba.excel.analysis.v07.XlsxSaxAnalyser.execute(XlsxSaxAnalyser.java:261)
	at com.alibaba.excel.analysis.ExcelAnalyserImpl.analysis(ExcelAnalyserImpl.java:124)
	at com.alibaba.excel.ExcelReader.read(ExcelReader.java:66)
	at com.alibaba.excel.ExcelReader.read(ExcelReader.java:56)
	at com.alibaba.excel.read.builder.ExcelReaderSheetBuilder.doRead(ExcelReaderSheetBuilder.java:65)
	at com.alibaba.excel.read.builder.ExcelReaderSheetBuilder$doRead.call(Unknown Source)
	at org.codehaus.groovy.runtime.callsite.CallSiteArray.defaultCall(CallSiteArray.java:47)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:115)
	at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:119)
	at com.groovy.MyTest.MyTest.MyTest01(MyTest.groovy:25)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.junit.platform.commons.util.ReflectionUtils.invokeMethod(ReflectionUtils.java:686)
	at org.junit.jupiter.engine.execution.MethodInvocation.proceed(MethodInvocation.java:60)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain$ValidatingInvocation.proceed(InvocationInterceptorChain.java:131)
	at org.junit.jupiter.engine.extension.TimeoutExtension.intercept(TimeoutExtension.java:149)
	at org.junit.jupiter.engine.extension.TimeoutExtension.interceptTestableMethod(TimeoutExtension.java:140)
	at org.junit.jupiter.engine.extension.TimeoutExtension.interceptTestMethod(TimeoutExtension.java:84)
	at org.junit.jupiter.engine.execution.ExecutableInvoker$ReflectiveInterceptorCall.lambda$ofVoidMethod$0(ExecutableInvoker.java:115)
	at org.junit.jupiter.engine.execution.ExecutableInvoker.lambda$invoke$0(ExecutableInvoker.java:105)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain$InterceptedInvocation.proceed(InvocationInterceptorChain.java:106)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain.proceed(InvocationInterceptorChain.java:64)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain.chainAndInvoke(InvocationInterceptorChain.java:45)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain.invoke(InvocationInterceptorChain.java:37)
	at org.junit.jupiter.engine.execution.ExecutableInvoker.invoke(ExecutableInvoker.java:104)
	at org.junit.jupiter.engine.execution.ExecutableInvoker.invoke(ExecutableInvoker.java:98)
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.lambda$invokeTestMethod$6(TestMethodTestDescriptor.java:212)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.invokeTestMethod(TestMethodTestDescriptor.java:208)
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.execute(TestMethodTestDescriptor.java:137)
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.execute(TestMethodTestDescriptor.java:71)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$5(NodeTestTask.java:135)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$7(NodeTestTask.java:125)
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:135)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:123)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:122)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:80)
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1541)
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.invokeAll(SameThreadHierarchicalTestExecutorService.java:38)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$5(NodeTestTask.java:139)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$7(NodeTestTask.java:125)
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:135)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:123)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:122)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:80)
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1541)
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.invokeAll(SameThreadHierarchicalTestExecutorService.java:38)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$5(NodeTestTask.java:139)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$7(NodeTestTask.java:125)
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:135)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:123)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:122)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:80)
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.submit(SameThreadHierarchicalTestExecutorService.java:32)
	at org.junit.platform.engine.support.hierarchical.HierarchicalTestExecutor.execute(HierarchicalTestExecutor.java:57)
	at org.junit.platform.engine.support.hierarchical.HierarchicalTestEngine.execute(HierarchicalTestEngine.java:51)
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:248)
	at org.junit.platform.launcher.core.DefaultLauncher.lambda$execute$5(DefaultLauncher.java:211)
	at org.junit.platform.launcher.core.DefaultLauncher.withInterceptedStreams(DefaultLauncher.java:226)
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:199)
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:132)
	at com.intellij.junit5.JUnit5IdeaTestRunner.startRunnerWithArgs(JUnit5IdeaTestRunner.java:57)
	at com.intellij.rt.junit.IdeaTestRunner$Repeater$1.execute(IdeaTestRunner.java:38)
	at com.intellij.rt.execution.junit.TestsRepeater.repeat(TestsRepeater.java:11)
	at com.intellij.rt.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:35)
	at com.intellij.rt.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:232)
	at com.intellij.rt.junit.JUnitStarter.main(JUnitStarter.java:55)


Process finished with exit code -1
```
## 问题分析
easyexcel版本：4.0.3
读取文件的代码如下
```java
void MyTest01() {
        AnalysisEventListener listener = new AnalysisEventListener<Person>() {

            @Override
            void invoke(Person data, AnalysisContext context) {
                println data.name
            }

            @Override
            void doAfterAllAnalysed(AnalysisContext context) {
                println "read done"
            }
        }

        EasyExcel.read(new ByteArrayInputStream(new File("E:\\Learn\\ProgramDesign\\Java\\idea\\jdk11-gradle-groovy\\src\\test\\groovy\\com\\groovy\\MyTest\\test.xlsx").bytes), Person, listener)
                .sheet(0)  // 默认读取第一个 sheet
                .doRead()  // 开始读取

}
```

```java
import com.alibaba.excel.annotation.ExcelProperty

class Person {
    @ExcelProperty(value = "Name")
    String name
}
```

下面时excel文件内容：

![image](https://github.com/user-attachments/assets/9af57346-5174-4c18-8c71-e35003bdb7fb)


但是如果将Person按照下面两种方式写，却不会报错，能够正确读取文件：

```java
import com.alibaba.excel.annotation.ExcelProperty

class Person {
    @ExcelProperty(value = "Name")
    String name
    @ExcelProperty(value = "Age")
    String age
}
```

```java
import com.alibaba.excel.annotation.ExcelIgnoreUnannotated
import com.alibaba.excel.annotation.ExcelProperty

@ExcelIgnoreUnannotated()
class Person {
    @ExcelProperty(value = "Name")
    String name
}
```


经过调试发现，easyexcel读取文件后，会将excel文件中的字段映射到Person字段中，但是Person出现除了name字段以外的字段，导致将文件字段内容映射到Person类是出现了类型转换的错误。

根据调试分析，源代码通过反射获取Person类属性，一共会得到name, $staticClassInfo, $callSiteArray, $staticClassInfo$, metaClass, __$stMC 。

但是明明Person类中只定义了一个name属性，为什么会得到这么多属性？通过分析Person字节码文件，可以发现Person类被编译字节码文件后会自动添加一些字段，
下面是Person的字节码文件内容：

```java
// class version 55.0 (55)
// access flags 0x21
public class com/groovy/MyTest/Person implements groovy/lang/GroovyObject {

  // compiled from: Person.groovy

  // access flags 0x2
  private Ljava/lang/String; name
  @Lcom/alibaba/excel/annotation/ExcelProperty;(value={"Name"})

  // access flags 0x100A
  private static synthetic Lorg/codehaus/groovy/reflection/ClassInfo; $staticClassInfo

  // access flags 0x1089
  public static transient synthetic Z __$stMC

  // access flags 0x1082
  private transient synthetic Lgroovy/lang/MetaClass; metaClass

  // access flags 0x100A
  private static synthetic Lorg/codehaus/groovy/reflection/ClassInfo; $staticClassInfo$

  // access flags 0x100A
  private static synthetic Ljava/lang/ref/SoftReference; $callSiteArray

  // access flags 0x1
  public <init>()V
  @Lgroovy/transform/Generated;()
   L0
    INVOKESTATIC com/groovy/MyTest/Person.$getCallSiteArray ()[Lorg/codehaus/groovy/runtime/callsite/CallSite;
    ASTORE 1
    ALOAD 0
    INVOKESPECIAL java/lang/Object.<init> ()V
    ALOAD 0
    INVOKEVIRTUAL com/groovy/MyTest/Person.$getStaticMetaClass ()Lgroovy/lang/MetaClass;
    ASTORE 2
    ALOAD 2
    ALOAD 0
    SWAP
    PUTFIELD com/groovy/MyTest/Person.metaClass : Lgroovy/lang/MetaClass;
    ALOAD 2
    POP
   L1
    RETURN
    LOCALVARIABLE this Lcom/groovy/MyTest/Person; L0 L1 0
    MAXSTACK = 2
    MAXLOCALS = 3

  // access flags 0x1004
  protected synthetic $getStaticMetaClass()Lgroovy/lang/MetaClass;
    ALOAD 0
    INVOKEVIRTUAL java/lang/Object.getClass ()Ljava/lang/Class;
    LDC Lcom/groovy/MyTest/Person;.class
    IF_ACMPEQ L0
    ALOAD 0
    INVOKESTATIC org/codehaus/groovy/runtime/ScriptBytecodeAdapter.initMetaClass (Ljava/lang/Object;)Lgroovy/lang/MetaClass;
    ARETURN
   L0
   FRAME SAME
    GETSTATIC com/groovy/MyTest/Person.$staticClassInfo : Lorg/codehaus/groovy/reflection/ClassInfo;
    ASTORE 1
    ALOAD 1
    IFNONNULL L1
    ALOAD 0
    INVOKEVIRTUAL java/lang/Object.getClass ()Ljava/lang/Class;
    INVOKESTATIC org/codehaus/groovy/reflection/ClassInfo.getClassInfo (Ljava/lang/Class;)Lorg/codehaus/groovy/reflection/ClassInfo;
    DUP
    ASTORE 1
    PUTSTATIC com/groovy/MyTest/Person.$staticClassInfo : Lorg/codehaus/groovy/reflection/ClassInfo;
   L1
   FRAME APPEND [org/codehaus/groovy/reflection/ClassInfo]
    ALOAD 1
    INVOKEVIRTUAL org/codehaus/groovy/reflection/ClassInfo.getMetaClass ()Lgroovy/lang/MetaClass;
    ARETURN
    MAXSTACK = 2
    MAXLOCALS = 2

  // access flags 0x1001
  public synthetic getMetaClass()Lgroovy/lang/MetaClass;
  @Lgroovy/transform/Generated;()
  @Lgroovy/transform/Internal;()
    ALOAD 0
    GETFIELD com/groovy/MyTest/Person.metaClass : Lgroovy/lang/MetaClass;
    DUP
    IFNULL L0
    ARETURN
   L0
   FRAME SAME1 groovy/lang/MetaClass
    POP
    ALOAD 0
    DUP
    INVOKEVIRTUAL com/groovy/MyTest/Person.$getStaticMetaClass ()Lgroovy/lang/MetaClass;
    PUTFIELD com/groovy/MyTest/Person.metaClass : Lgroovy/lang/MetaClass;
    ALOAD 0
    GETFIELD com/groovy/MyTest/Person.metaClass : Lgroovy/lang/MetaClass;
    ARETURN
    MAXSTACK = 2
    MAXLOCALS = 1

  // access flags 0x1001
  public synthetic setMetaClass(Lgroovy/lang/MetaClass;)V
  @Lgroovy/transform/Generated;()
  @Lgroovy/transform/Internal;()
    ALOAD 0
    ALOAD 1
    PUTFIELD com/groovy/MyTest/Person.metaClass : Lgroovy/lang/MetaClass;
    RETURN
    MAXSTACK = 2
    MAXLOCALS = 2

  // access flags 0x1001
  public synthetic invokeMethod(Ljava/lang/String;Ljava/lang/Object;)Ljava/lang/Object;
  @Lgroovy/transform/Generated;()
  @Lgroovy/transform/Internal;()
    ALOAD 0
    INVOKEVIRTUAL com/groovy/MyTest/Person.getMetaClass ()Lgroovy/lang/MetaClass;
    ALOAD 0
    ALOAD 1
    ALOAD 2
    INVOKEINTERFACE groovy/lang/MetaClass.invokeMethod (Ljava/lang/Object;Ljava/lang/String;Ljava/lang/Object;)Ljava/lang/Object; (itf)
    ARETURN
    MAXSTACK = 4
    MAXLOCALS = 3

  // access flags 0x1001
  public synthetic getProperty(Ljava/lang/String;)Ljava/lang/Object;
  @Lgroovy/transform/Generated;()
  @Lgroovy/transform/Internal;()
    ALOAD 0
    INVOKEVIRTUAL com/groovy/MyTest/Person.getMetaClass ()Lgroovy/lang/MetaClass;
    ALOAD 0
    ALOAD 1
    INVOKEINTERFACE groovy/lang/MetaClass.getProperty (Ljava/lang/Object;Ljava/lang/String;)Ljava/lang/Object; (itf)
    ARETURN
    MAXSTACK = 3
    MAXLOCALS = 2

  // access flags 0x1001
  public synthetic setProperty(Ljava/lang/String;Ljava/lang/Object;)V
  @Lgroovy/transform/Generated;()
  @Lgroovy/transform/Internal;()
    ALOAD 0
    INVOKEVIRTUAL com/groovy/MyTest/Person.getMetaClass ()Lgroovy/lang/MetaClass;
    ALOAD 0
    ALOAD 1
    ALOAD 2
    INVOKEINTERFACE groovy/lang/MetaClass.setProperty (Ljava/lang/Object;Ljava/lang/String;Ljava/lang/Object;)V (itf)
    RETURN
    MAXSTACK = 4
    MAXLOCALS = 3

  // access flags 0x1
  public getName()Ljava/lang/String;
  @Lgroovy/transform/Generated;()
    ALOAD 0
    GETFIELD com/groovy/MyTest/Person.name : Ljava/lang/String;
    ARETURN
    MAXSTACK = 1
    MAXLOCALS = 1

  // access flags 0x1
  public setName(Ljava/lang/String;)V
  @Lgroovy/transform/Generated;()
    ALOAD 0
    ALOAD 1
    PUTFIELD com/groovy/MyTest/Person.name : Ljava/lang/String;
    RETURN
    MAXSTACK = 2
    MAXLOCALS = 2

  // access flags 0x100A
  private static synthetic $createCallSiteArray()Lorg/codehaus/groovy/runtime/callsite/CallSiteArray;
    LDC 0
    ANEWARRAY java/lang/String
    ASTORE 0
    NEW org/codehaus/groovy/runtime/callsite/CallSiteArray
    DUP
    LDC Lcom/groovy/MyTest/Person;.class
    ALOAD 0
    INVOKESPECIAL org/codehaus/groovy/runtime/callsite/CallSiteArray.<init> (Ljava/lang/Class;[Ljava/lang/String;)V
    ARETURN
    MAXSTACK = 4
    MAXLOCALS = 1

  // access flags 0x100A
  private static synthetic $getCallSiteArray()[Lorg/codehaus/groovy/runtime/callsite/CallSite;
    GETSTATIC com/groovy/MyTest/Person.$callSiteArray : Ljava/lang/ref/SoftReference;
    IFNULL L0
    GETSTATIC com/groovy/MyTest/Person.$callSiteArray : Ljava/lang/ref/SoftReference;
    INVOKEVIRTUAL java/lang/ref/SoftReference.get ()Ljava/lang/Object;
    CHECKCAST org/codehaus/groovy/runtime/callsite/CallSiteArray
    DUP
    ASTORE 0
    IFNONNULL L1
   L0
   FRAME SAME
    INVOKESTATIC com/groovy/MyTest/Person.$createCallSiteArray ()Lorg/codehaus/groovy/runtime/callsite/CallSiteArray;
    ASTORE 0
    NEW java/lang/ref/SoftReference
    DUP
    ALOAD 0
    INVOKESPECIAL java/lang/ref/SoftReference.<init> (Ljava/lang/Object;)V
    PUTSTATIC com/groovy/MyTest/Person.$callSiteArray : Ljava/lang/ref/SoftReference;
   L1
   FRAME APPEND [org/codehaus/groovy/runtime/callsite/CallSiteArray]
    ALOAD 0
    GETFIELD org/codehaus/groovy/runtime/callsite/CallSiteArray.array : [Lorg/codehaus/groovy/runtime/callsite/CallSite;
    ARETURN
    MAXSTACK = 3
    MAXLOCALS = 1
}
```
确实存在：

private static synthetic Lorg/codehaus/groovy/reflection/ClassInfo; $staticClassInfo

public static transient synthetic Z __$stMC

private transient synthetic Lgroovy/lang/MetaClass; metaClass

private static synthetic Lorg/codehaus/groovy/reflection/ClassInfo; $staticClassInfo$

private static synthetic Ljava/lang/ref/SoftReference; $callSiteArray

继续调试源码，发现下面这个方法会筛选掉一些字段：

```java
    private static FieldCache declaredFields(Class<?> clazz) {
        if (clazz == null) {
            return null;
        }
        return FIELD_CACHE.computeIfAbsent(clazz, key -> {
            List<Field> tempFieldList = new ArrayList<>();
            Class<?> tempClass = clazz;
            // When the parent class is null, it indicates that the parent class (Object class) has reached the top
            // level.
            while (tempClass != null) {
                Collections.addAll(tempFieldList, tempClass.getDeclaredFields());
                // Get the parent class and give it to yourself
                tempClass = tempClass.getSuperclass();
            }
            // Screening of field
            Map<Integer, List<Field>> orderFieldMap = new TreeMap<Integer, List<Field>>();
            Map<Integer, Field> indexFieldMap = new TreeMap<Integer, Field>();
            Map<String, Field> ignoreMap = new HashMap<String, Field>(16);

            ExcelIgnoreUnannotated excelIgnoreUnannotated = clazz.getAnnotation(ExcelIgnoreUnannotated.class);
            for (Field field : tempFieldList) {
                declaredOneField(field, orderFieldMap, indexFieldMap, ignoreMap, excelIgnoreUnannotated);
            }
            return new FieldCache(buildSortedAllFieldMap(orderFieldMap, indexFieldMap), indexFieldMap, ignoreMap);
        });
    }
```

```java
private static void declaredOneField(Field field, Map<Integer, List<Field>> orderFieldMap,
        Map<Integer, Field> indexFieldMap, Map<String, Field> ignoreMap,
        ExcelIgnoreUnannotated excelIgnoreUnannotated) {

        ExcelIgnore excelIgnore = field.getAnnotation(ExcelIgnore.class);
        if (excelIgnore != null) {
            ignoreMap.put(field.getName(), field);
            return;
        }
        ExcelProperty excelProperty = field.getAnnotation(ExcelProperty.class);
        boolean noExcelProperty = excelProperty == null && excelIgnoreUnannotated != null;
        if (noExcelProperty) {
            ignoreMap.put(field.getName(), field);
            return;
        }
        boolean isStaticFinalOrTransient =
            (Modifier.isStatic(field.getModifiers()) && Modifier.isFinal(field.getModifiers()))
                || Modifier.isTransient(field.getModifiers());
        if (excelProperty == null && isStaticFinalOrTransient) {
            ignoreMap.put(field.getName(), field);
            return;
        }
        if (excelProperty != null && excelProperty.index() >= 0) {
            if (indexFieldMap.containsKey(excelProperty.index())) {
                throw new ExcelCommonException("The index of '" + indexFieldMap.get(excelProperty.index()).getName()
                    + "' and '" + field.getName() + "' must be inconsistent");
            }
            indexFieldMap.put(excelProperty.index(), field);
            return;
        }

        int order = Integer.MAX_VALUE;
        if (excelProperty != null) {
            order = excelProperty.order();
        }
        List<Field> orderFieldList = orderFieldMap.computeIfAbsent(order, key -> ListUtils.newArrayList());
        orderFieldList.add(field);
  }
```

仔细观察以下这段代码，他会剔除 static final和transientx 修饰的字段。也就是__$stMC和metaClass。经过测试，使用java 类生成的字节码也会包含这两个字段。

```java
  boolean isStaticFinalOrTransient =
      (Modifier.isStatic(field.getModifiers()) && Modifier.isFinal(field.getModifiers()))
          || Modifier.isTransient(field.getModifiers());
  if (excelProperty == null && isStaticFinalOrTransient) {
      ignoreMap.put(field.getName(), field);
      return;
  }
```

分析其中这两段代码，发现如果类用 @ExcelIgnoreUnannotated() 修饰，并且没有被@ExcelProperty注解的属性也会被剔除掉
```java
ExcelIgnoreUnannotated excelIgnoreUnannotated = clazz.getAnnotation(ExcelIgnoreUnannotated.class)
```

```java
ExcelProperty excelProperty = field.getAnnotation(ExcelProperty.class);
boolean noExcelProperty = excelProperty == null && excelIgnoreUnannotated != null;
if (noExcelProperty) {
    ignoreMap.put(field.getName(), field);
    return;
}
```


通过以上分析，就可以解释读取文件出错的原因了。

当Person类中声明的属性少于excel文件中的字段，并且没有用@ExcelIgnoreUnannotated() 注解类时，$staticClassInfo, $callSiteArray, $staticClassInfo$ 这三个字段将会参与到字段映射的操作中去，于是出现了类型转换的错误。











