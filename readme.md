## 一、创建第一个新的工程

 打开Android Studio，选择Projects>New Project，然后选择Basic Activity. 



## 二、 创建虚拟设备 

创建后启动

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/9.png?raw=true)



## 三、First Fragment

 查看res>layout>fragment_first.xml

 查看布局的代码（Code），修改Textview的**Text**属性

```
android:text="@string/hello_first_fragment"
```

 右键该代码，选择**Go To > Declaration or Usages**，跳转到values/strings.xml，看到高亮文本

```
<string name="hello_first_fragment">Hello first fragment</string>
```

 修改字符串属性值为“Hello Kotlin!”。更进一步，修改字体显示属性，在Design视图中选择**textview_first**文本组件，在Common Attributes属性下的textAppearance域，设置相关的文字显示属性

 查看布局的XML代码，可以看到新属性被应用

```
android:fontFamily="sans-serif-condensed"
android:text="@string/hello_first_fragment"
android:textColor="@android:color/darker_gray"
android:textSize="30sp"
android:textStyle="bold"
```

 重新运行应用程序 

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/1.png?raw=true)



### 1、添加按钮和约束

#### Toast按钮

 调整Button的约束，设置Button的Top>BottonOf textView，  随后添加Button的左侧约束至屏幕的左侧，Button的底部约束至屏幕的底部。查看Attributes面板，修改将id从button修改为toast_button

 fragment_first.xml布局文件代码中，找到toast_button按钮的text属性部分 , text的赋值是一种硬编码，点击文本，左侧出现灯泡状的提示，选择 **Extract string resource**, 令资源名为toast_button_text，资源值为Toast 

```
<Button
        android:id="@+id/toast_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="24dp"
        android:background="@color/buttonBackground"
        android:text="@string/toast_button_text"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textview_first" />
```



#### TextView文本

 TextView的底部约束至屏幕的底部 ，顶部约束至屏幕的顶部 ，左部约束至屏幕的左部 ，右部约束至屏幕的右部， 更改TextView的文本为**0** 

```
<TextView    android:id="@+id/textview_first"    android:layout_width="wrap_content"    android:layout_height="wrap_content"    android:fontFamily="sans-serif-condensed"    android:text="@string/hello_first_fragment"    android:textColor="@android:color/white"    android:textSize="72sp"    android:textStyle="bold"    app:layout_constraintVertical_bias="0.3"    app:layout_constraintEnd_toEndOf="parent"    app:layout_constraintStart_toStartOf="parent"    app:layout_constraintBottom_toBottomOf="parent"    app:layout_constraintTop_toTopOf="parent" />
```

 

#### Random按钮

 删除next按钮与textview之间的链，可以在设计视图右键相应约束，选择Delete ，同时，删除Next按钮的左侧约束 

 在属性面板中更改Next按钮的id，从button_first改为random_button 

 在string.xml文件，右键**next**字符串资源，选择 **Refactor > Rename**，修改资源名称为**random_button_text**，点击**Refactor** 。随后，修改**Next**值为**Random**。 

```
<Button    android:id="@+id/random_button"    android:layout_width="wrap_content"    android:layout_height="wrap_content"    android:layout_marginEnd="24dp"    android:background="@color/buttonBackground"    android:text="@string/random_button_text"    app:layout_constraintBottom_toBottomOf="parent"    app:layout_constraintEnd_toEndOf="parent"    app:layout_constraintTop_toBottomOf="@+id/textview_first" />
```

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/2.png?raw=true)



#### Count按钮

 向fragment_first.xml文件中添加第三个按钮，位于Toast和Random按钮之间，TextView的下方。新Button的左右约束分别约束至Toast和Random，Top约束至TextView的底部，Buttom约束至屏幕的底部 更改新增按钮id为**count_button**，显示字符串为**Count**，对应字符串资源值为**count_button_text** 

```
<Button    android:id="@+id/count_button"    android:layout_width="wrap_content"    android:layout_height="wrap_content"    android:text="@string/count_button_text"    android:background="@color/buttonBackground"    app:layout_constraintTop_toBottomOf="@+id/textview_first"    app:layout_constraintStart_toStartOf="@+id/toast_button"    app:layout_constraintEnd_toEndOf="@+id/random_button"    app:layout_constraintBottom_toBottomOf="parent"/>
```

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/3.png?raw=true)



### 2、更新按钮和文本框的外观

#### 添加新的颜色资源

 values>colors.xml  定义了一些应用程序可以使用的颜色 

```
<color name="screenBackground">#2196F3</color>
<color name="buttonBackground">#BBDEFB</color>
```



#### 设置组件的外观

 修改res/values/themes.xml的style值，添加**.Bridge**

```
<style name="Theme.MyFirstApp" parent="Theme.MaterialComponents.DayNight.DarkActionBar.Bridge">
```

fragment_first.xml的属性面板中设置屏幕背景色为

```
android:background="@color/screenBackground"
```

设置每个按钮的背景色为

```
android:background="@color/buttonBackground"
```



#### 设置组件的位置

 Toast与屏幕的左边距设置为24dp，Random与屏幕的右边距设置为24dp，利用属性面板的Constraint Widget完成设置 



运行代码结果如下

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/4.png?raw=true)



### 3、添加事件

#### TOAST按钮添加一个toast消息

 打开FirstFragment.kt文件，有三个方法：onCreateView，onViewCreated和onDestroyView，在onViewCreated方法中使用绑定机制设置按钮的响应事件。 

```
binding.randomButton.setOnClickListener {
    findNavController().navigate(R.id.action_FirstFragment_to_SecondFragment)
}
```

 接下来，为TOAST按钮添加事件，使用**findViewById()**查找按钮id 

```
// find the toast_button by its ID and set a click listener
view.findViewById<Button>(R.id.toast_button).setOnClickListener {
   // create a Toast with some text, to appear for a short time
   val myToast = Toast.makeText(context, "Hello Toast!", Toast.LENGTH_LONG)
   // show the Toast
   myToast.show()
}
```



#### 使Count按钮更新屏幕的数字

 向Count按钮添加事件响应，更新Textview的文本显示。
在FirstFragment.kt文件，为count_buttion按钮添加事件： 

```
view.findViewById<Button>(R.id.count_button).setOnClickListener {
   countMe(view)
}
```

 countMe()为自定义方法，以View为参数，每次点击增加数字1 

```
private fun countMe(view: View) {
   // Get the text view
   val showCountTextView = view.findViewById<TextView>(R.id.textview_first)

   // Get the value of the text view.
   val countString = showCountTextView.text.toString()

   // Convert value to a number and increment it
   var count = countString.toInt()
   count++

   // Display the new value in the text view.
   showCountTextView.text = count.toString()
}
```



## 二、 Second Fragment 

### 1、向界面添加TextView显示随机数

打开fragment_second.xml的设计视图中，当前界面有两个组件，一个Button和一个TextView（textview_second）。

去掉TextView和Button之间的约束

拖动新的TextView至屏幕的中间位置，用来显示随机数

设置新的TextView的id为**@+id/textview_random**

设置新的TextView的左右约束至屏幕的左右侧，Top约束至textview_second的Bottom，Bottom约束至Button的Top

设置TextView的字体颜色textColor属性为**@android:color/white**，**textSize**为**72sp**，**textStyle**为**bold**

设置TextView的显示文字为“**R**”

设置垂直偏移量**layout_constraintVertical_bias**为0.45

 新增TextView最终的属性代码 

```
<TextView
   android:id="@+id/textview_random"
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:text="R"
   android:textColor="@android:color/white"
   android:textSize="72sp"
   android:textStyle="bold"
   app:layout_constraintBottom_toTopOf="@+id/button_second"
   app:layout_constraintEnd_toEndOf="parent"
   app:layout_constraintStart_toStartOf="parent"
   app:layout_constraintTop_toBottomOf="@+id/textview_second"
   app:layout_constraintVertical_bias="0.45" />
```

### 2、更新显示界面文本的TextView

在fragment_second.xml文件中，选择textview_second文本框，查看text属性，

```
android:text="@string/hello_second_fragment
```

对应的strings.xml文本为Hello second fragment. Arg: %1$s

更改该文本框id为textview_header

设置layout_width为match_parent，layout_height为wrap_content。

设置top，left和right的margin为24dp，左边距和右边距也就是start和end边距。

若还存在与Button的约束，则删除。

向colors.xml添加颜色colorPrimaryDark，并将TextView颜色设置为@color/colorPrimaryDark，字体大小为24sp。

```
<color name="colorPrimaryDark">#3700B3</color>
```

strings.xml文件中，修改hello_second_fragment的值为"Here is a random number between 0 and %d."

使用Refactor>Rename将hello_second_fragment 重构为random_heading

最终的属性代码 

```
<TextView
   android:id="@+id/textview_header"
   android:layout_width="0dp"
   android:layout_height="wrap_content"
   android:layout_marginStart="24dp"
   android:layout_marginLeft="24dp"
   android:layout_marginTop="24dp"
   android:layout_marginEnd="24dp"
   android:layout_marginRight="24dp"
   android:text="@string/random_heading"
   android:textColor="@color/colorPrimaryDark"
   android:textSize="24sp"
   app:layout_constraintEnd_toEndOf="parent"
   app:layout_constraintStart_toStartOf="parent"
   app:layout_constraintTop_toTopOf="parent" />
```



### 3、更改界面的背景色和按钮布局

向colors.xml文件添加第二个Fragment背景色的值，修改fragment_second.xml背景色的属性为`screenBackground2`

```
<color name="screenBackground2">#26C6DA</color>
```

 将按钮移动至界面的底部 

```
<Button
        android:id="@+id/button_second"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/previous"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />
```



布局结果如下

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/5.png?raw=true)



### 4、检查导航图

 打开nav_graph.xml文件（**res>navigation>nav_graph.xml**） 

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/6.png?raw=true)



### 5、启用SafeArgs

首先打开 **Gradle Scripts > build.gradle (Project: My First App)** 在plugins中添加

```
id 'androidx.navigation.safeargs.kotlin' version '2.5.0-alpha01' apply false
```

 打开 **Gradle Scripts > build.gradle (Module: app)** 在plugins中添加

```
id 'androidx.navigation.safeargs'
```



### 6、创建导航动作的参数

打开导航视图，点击`FirstFragment`，查看其属性。

在`Actions`栏中可以看到导航至`SecondFragment`

同理，查看`SecondFragment`的属性栏

点击Arguments **+**符号

弹出的对话框中，添加参数myArg，类型为整型Integer



### 7、FirstFragment添加代码，向SecondFragment发数据

打开FirstFragment.kt源代码文件，找到onViewCreated()方法 ， 找到Random按钮的响应代码，注释掉原先的事件处理代码

添加

```
val showCountTextView = view.findViewById<TextView>(R.id.textview_first)
val currentCount = showCountTextView.text.toString().toInt()
val action = FirstFragmentDirections.actionFirstFragmentToSecondFragment(currentCount)
findNavController().navigate(action)
```



### 8、添加SecondFragment的代码

导入navArgs包

```
import androidx.navigation.fragment.navArgs
```

 在onViewCreated()中添加

```
val args: SecondFragmentArgs by navArgs()
val count = args.myArg
val countText = getString(R.string.random_heading, count)
view.findViewById<TextView>(R.id.textview_header).text = countText
val random = java.util.Random()
var randomNumber = 0
if (count > 0) {
   randomNumber = random.nextInt(count + 1)
}
view.findViewById<TextView>(R.id.textview_random).text = randomNumber.toString()
```

 

最后运行程序，结果如下

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/7.png?raw=true)

![image](https://github.com/IlIlIlIlIlIlIlIlIlIlIl/exp2/blob/main/image/8.png?raw=true)