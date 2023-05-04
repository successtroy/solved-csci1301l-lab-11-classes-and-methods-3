Download Link: https://assignmentchef.com/product/solved-csci1301l-lab-11-classes-and-methods-3
<br>
<strong>Introduction </strong>

In this lab, we continue working on classes and methods. The work is based on the previous lab, the <strong>Stat </strong>class. You will use existing code that you should have made since last lab and add or modify codes to the <strong>Stat </strong>class. You will practice on implementing method overloading and design a few algorithms to operate on the arrays.




Since this lab assignment relies on the work from the previous lab. You must ensure that the code from the previous assignment works. You are not allowed to use any code that was not made by yourself to work on this lab. Moreover, you should not provide any of your code from the previous assignment to anybody else.

<strong> </strong>

<strong>Lab objectives </strong>




After completing this lab, you should be able to create classes and gain further experience by utilizing:

<ul>

 <li>constructors,</li>

 <li>access modifiers,</li>

 <li>instance variables,</li>

 <li>general methods with different return types,</li>

 <li>methods called another methods,</li>

 <li>specific accessor and mutator methods,</li>

 <li>different kinds of overloading methods, and</li>

 <li>one-dimensional arrays of various data types.</li>

</ul>

<strong> </strong>

<strong>Assignment </strong>




During method calls, automatic type conversion of primitive data types does not apply to arrays of primitive data types. We understand that an array with a narrower ranged type of data will not automatically convert to a wider ranged type of data, e.g. from int to double. Moreover, automatic type conversion can be performed on individual elements of an array, but not on the array itself.




By considering this background, you will add some methods that specifically deal with certain type of data in an array. Additionally, you will also write some methods to operate on an array and to obtain additional statistical data from the array.




Sometimes, we may handle methods invoked with <strong>null</strong> as a parameter. In this assignment, you will modify several methods to check that value passed to the methods is not <strong>null.</strong> We will ensure the robustness of the program so that all calculations are performed on some values, not on “nothing”, which could trigger errors.




In this lab, you will modify the existing code from <em>Stat.java </em>that deals with additional statistics of data, including variance and standard deviation. Details are described as follows:




<ol>

 <li>Use the UML diagram and method descriptions below to modify your <strong>Stat </strong> Numbers in front of the methods in the class diagram are not part of the code. They are for explaining the program requirements.</li>

</ol>




<table width="487">

 <tbody>

  <tr>

   <td width="487"><strong>                         Stat </strong></td>

  </tr>

  <tr>

   <td width="487"><strong> </strong><strong>– data: double[] </strong><strong> </strong></td>

  </tr>

  <tr>

   <td width="487"><strong> </strong><strong>1.      </strong><strong>+ Stat() </strong><strong>2.      </strong><strong>+ Stat(double[] d) </strong><strong>3.      </strong><strong>+ Stat(float[] f) </strong><strong>4.      </strong><strong>+ Stat(int[] i) </strong><strong>5.      </strong><strong>+ Stat(long[] lo) </strong><strong>6.      </strong><strong>+ setData(float[] f): void </strong><strong>7.      </strong><strong>+ setData(double[] d): void </strong><strong>8.      </strong><strong>+ setData(int[] i): void </strong><strong>9.      </strong><strong>+ setData(long[] lo): void </strong><strong>10.    </strong><strong>+ getData(): double[] </strong><strong>11.    </strong><strong>+ equals(Stat s): boolean </strong><strong>12.    </strong><strong>+ reset(): void </strong><strong>13.    </strong><strong>+ append(int[] i): void </strong><strong>14.    </strong><strong>+ append(float[] f): void </strong><strong>15.    </strong><strong>+ append(long[] lo): void </strong><strong>16.    </strong><strong>+ append(double[] d): void </strong><strong>17.    </strong><strong>+ isEmpty(): boolean </strong><strong>18.    </strong><strong>+ toString(): String </strong><strong>19.    </strong><strong>+ min(): double </strong><strong>20.    </strong><strong>+ max(): double </strong><strong>21.    </strong><strong>+ average(): double </strong><strong>22.    </strong><strong>+ mode(): double </strong><strong>23.    </strong><strong>– occursNumberOfTimes(double value): int </strong><strong>24.    </strong><strong>+ variance(): double </strong><strong>25.    </strong><strong>+ standardDeviation(): double </strong></td>

  </tr>

 </tbody>

</table>




Texts in red will be the methods that you need to add into the existing class. Texts in black are existing methods that you should have made since last lab, but they may need to be modified according to the new program need.




Recall the previous lab,<strong> Stat</strong> class stores an array of double type values called <strong>data </strong>(private type). The <strong>data</strong> has the type double[], which is a reference type. This means that <strong>data</strong> itself will store a reference to the memory location where the array is store. However, <strong>data </strong>does not store the array.




<ol start="2">

 <li>After you have created the skeleton code of <strong>Stat</strong> class according the UML class diagram, implement the detail of the methods.</li>

</ol>




<ul>

 <li><strong>(1) Stat() </strong></li>

</ul>

This is the default constructor for the class <strong>Stat</strong>. It should create a <strong>double</strong> array having a length 0. It is possible to create an array of length 0 in Java. Consider having a variable to hold a reference to such an array of length 0 (another way is to assign <strong>null </strong>to that variable).

Clearly, you will modify the method of Stat class that you did since last time to reflect the fact that a length 0 array is created.




<strong>=-= Hint =-= </strong>

Pay attention to the difference between these three kinds of arrays:

<ul>

 <li>An array with null property means “there is a so-called array of <em>no-array</em>“. For example, int[] array = null;</li>

 <li>An empty array means “there is an array with <em>no element</em>“.</li>

</ul>

For example, int[] array = new int[0];

<ul>

 <li>An array with null values means “There is an array but its elements have no value(yet)”.</li>

</ul>

For example, String[] array = new String[50];  // if no value will be assigned later




<ul>

 <li><strong>(2, 3, 4, 5) Stat(double[] d), Stat(int[] i),</strong> <strong>Stat(long[] lo),</strong> <strong>Stat(float[] f)</strong></li>

</ul>

These are all constructors for the class <strong>Stat</strong>. By using the constructor, the program will create a double array of the same length as the parameter array and holding copies of its values. A reference to the new array should be assigned to <strong>data</strong>. If the parameter is <strong>null</strong>, an empty array will be assigned to <strong>data</strong>.




<ul>

 <li><strong>(6, 7, 8, 9) setData(double[] d)</strong>, <strong>setData(int[] i)</strong>, <strong>setData(long[] lo)</strong>, <strong>setData(float[] f)</strong> These are the set methods (mutator). They are used to set the values of the <strong>data</strong> If the array used as parameter is not <strong>null</strong>, the method should create a new array containing exactly the elements of <strong>d</strong> and assign to <strong>data</strong> a reference to this new array. If the parameter is <strong>null</strong>, an empty array should be assigned to <strong>data</strong>.</li>

</ul>




<ul>

 <li><strong>(10) getData()</strong></li>

</ul>

This method should be left unchanged from the previous lab. The method should be able to handle empty array (i.e. the array length is 0).




<ul>

 <li><strong>(11) equals(Stat s)</strong></li>

</ul>

This method should be left unchanged from the previous lab. The method returns the <strong>boolean</strong> value <strong>true</strong> if the <strong>data</strong> objects of both the calling Stat object and the passing Stat object <strong>s</strong> have all the same values in the same order, or <strong>false</strong> otherwise. If the parameter <strong>s</strong> is null, the method returns <strong>false</strong>.




<ul>

 <li><strong>(12) reset()</strong></li>

</ul>

This method clears the data array. A new empty double array will be created and assigned to data.




<ul>

 <li><strong>(13, 14, 15, 16) append(double[] d)</strong>, <strong>append(int[] i)</strong>, <strong>append(long[] lo)</strong>, <strong>append(float[] f)</strong> These methods will create a new double array that contains exactly the elements of data, followed by those elements of the array passed as the parameter. A reference to this array will be assigned to data. If the parameter is null, the method will do nothing. See examples at the end of the document.</li>

</ul>




<ul>

 <li><strong>(17) isEmpty()</strong></li>

</ul>

This method returns a <strong>boolean </strong>value <strong>true </strong>if the <strong>data</strong> object is empty (i.e. such an array is an empty array, which has a length 0). Otherwise, it returns <strong>false.</strong>




<ul>

 <li><strong>(18) toString()</strong></li>

</ul>

As in the previous lab, this method returns a <strong>String</strong> of the data elements stored in the <strong>Stat</strong> object. Please look at the sample output at the end of the document for formatting. See how commas and square brackets are added.




<ul>

 <li><strong>(19) min()</strong></li>

</ul>

This method returns the minimum of the <strong>data </strong>array. If the array is empty, then the method returns <strong>Double.NaN</strong>.




<ul>

 <li><strong>(20) max()</strong></li>

</ul>

This method returns the maximum of the <strong>data</strong> array. If the array is empty, then the method returns <strong>Double.NaN</strong>.




<ul>

 <li><strong>(21) average()</strong></li>

</ul>

This method returns the average of the <strong>data </strong>array. The average is a double type value as the mean value of a given array of numbers. If the array is empty, then the method returns <strong>Double.NaN</strong>.

<strong> </strong>

<strong>=-= Hint =-= </strong>

<strong>Double.NaN</strong> is what the method will return. For example, return Double.NaN;

<strong>NaN </strong>stands for “Not a Number”. Treat it as “an undefined value” instead of “an error”.




<ul>

 <li><strong>(22) mode()</strong></li>

</ul>

Most part of the implementation will be the same as from the previous lab. This method returns the value that appears most frequently in the array. If there is no such unique, or if the <strong>data</strong> array is empty, the method will return <strong>Double.NaN</strong>.

<ul>

 <li><strong>(23) occursNumberOfTimes(double value)</strong></li>

</ul>

This method returns the number of times the value occurs in the <strong>data</strong> array. This is <strong>private</strong> method for the mode() method.




It is very likely that the mode() method that you have written contains many lines of code. A part of the mode() method includes the processing of getting the number of times such a value occurs in the array. Therefore, it is better to make code decomposition so that each method is handling one specific task.




This method implementation is optional.




<ul>

 <li><strong>(24) variance()</strong></li>

</ul>

This method returns the variance of the data in the <strong>data</strong> array. We define variance as the sum of [squared (difference between each element and the average)], divided by the total number of elements. If the <strong>data</strong> array is empty, the method returns <strong>Double.NaN</strong>.




For example, if there is an array of elements {1.0, 3.0, 5.0}. The difference between each element and the average (which is 3.0) is 2.0, 0.0, -2.0. Then the squared values of these three differences are 4.0, 0, 4.0. Next, the sum of these squared values is 4.0+0+4.0 = 8.0. This sum is divided by the total number of elements (which is 3). The result will be 8.0 / 3 = 2.6667.




<ul>

 <li><strong>(25) standardDeviation()</strong></li>

</ul>

This method returns the square root of the variance. If the <strong>data</strong> array is empty, the method returns <strong>Double.NaN</strong>.




<ol start="3">

 <li>After you have completed all above steps for modifying the <strong>Stat</strong> class, write a main method in a separate driver class to test each public method of the <strong>Stat</strong> For each method, there should be several test cases to use. Refer to the sample program outputs for select test cases.</li>

</ol>




It is very important that you thoroughly test your program by using multiple different types of test cases. For example (example only! Not a comprehensive list!), you should have arrays of different data types to test if method overloading works. You should also have arrays with 0, 1, 2, and multiple elements to test if the program can process them correctly. You should consider how arrays are connected using append() method, when they have different lengths (including 0 length arrays) and with different data types.

<strong> </strong>

<strong>It is very important that you are NOT allowed to use any methods from java.util.Arrays or any Java Stream APIs throughout the entire program code. </strong>

<strong> </strong>

<ol start="4">

 <li>Once you make the program working correctly. Understand the following statement for</li>

</ol>

Academic Honesty and add it into the top of your source code to submit. The following lines should be added ABOVE the original first line of code.

/*

<ul>

 <li>[CLASS/FILE NAME].java * Author: [YOUR NAME]</li>

 <li>Statement of Academic Honesty:</li>

</ul>

*

<ul>

 <li>The following code represents my own work. I have neither</li>

 <li>received nor given inappropriate assistance. I have not copied</li>

 <li>or modified code from anywhere other than the authorized</li>

 <li>I recognize that any unauthorized sharing, assistance,</li>

 <li>or plagiarism will be handled in accordance with both the</li>

 <li>University of Georgia’s Academic Honesty Policy and the</li>

 <li>policies of this course. I recognize that my work is based on</li>

 <li>an assignment created by the Department of Computer</li>

 <li>Science at the University of Georgia. Any publishing or posting * of source code at any time for this project is prohibited.  */</li>

</ul>




Replace [CLASS/FILE NAME] with the required name according to the assignment instruction. Replace [YOUR NAME] with your actual name.




<strong>Submission instruction </strong>




After you have completed and thoroughly tested your program, upload and submit the <strong>modified</strong> file <em>Stat.java</em>. Keep your original <em>Stat.java</em> file that was made since last time elsewhere.




You do not have to submit the driver class file that contains the main method. However, you may include it if you really want, but we will use different test cases to test your program.




<strong>Grading </strong>




A score between 0 and 10 will be assigned, with a minimum of 1 point increment (i.e. only integers).




<ol>

 <li>The source code is correctly provided, including the right file format/name extension. The file name is consistent with the source code’s class name. (1 point)</li>

 <li>Correct data types for variables are used, correct return types for the method are used, and correct access modifiers (public or private) are used. (1 point)</li>

 <li>Good programming practices are followed, including variable naming, coding layout, and comments. (1 point)</li>

 <li>No package declaration at the top of the program and no non-standard Java library or class is used, such as Arrays class, stream. (1 point)</li>

 <li>The program can pass 6 tests that cover one or more methods in the Stat class. Passing each test program is worth 1 point. (6 points)</li>

</ol>




Special notice regarding the submission:




<ol>

 <li>Late submission penalty. Points will be deducted from the original grade. If your submission is after the posted deadline…

  <ul>

   <li>within 24 hours: -3</li>

   <li>between 24 hours and 48 hours: -6</li>

   <li>between 48 hours and 72 hours: -9</li>

   <li>after 72 hours: assignment will not be accepted.</li>

  </ul></li>

</ol>




<ol>

 <li>If the source code file is missing, partially or completely broken, unable to open (including using a wrong file format), unable to compile, irrelevant to the assignment, purposely made to contain malicious codes, or determined to be an academic misrepresentation or a case of plagiarism, you will receive 0 grade for this assignment.</li>

</ol>







Below are sample inputs/outputs. This is not a comprehensive list of test cases.




<h1>Example 1</h1>

<em><u>Example main method:</u></em> <strong>double</strong>[] data1 = {}; Stat stat1 = <strong>new</strong> Stat(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average());

System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation()); System.<em>out</em>.println(“stat1 is empty = ” + stat1.isEmpty() + “
”);




<em><u>Example output:</u></em> stat1 data = [] stat1 min = NaN stat1 max = NaN stat1 average = NaN stat1 mode = NaN stat1 variance = NaN stat1 standard deviation = NaN

stat1 is empty = true

<strong> </strong>

<h1>Example 2</h1>

<em><u>Example main method:</u></em>

<strong>double</strong>[] data1 = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };

Stat stat1 = <strong>new</strong> Stat(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average());

System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation());

System.<em>out</em>.println(“stat1 is empty = ” + stat1.isEmpty() + “
”); stat1.reset();

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average());

System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation());

System.<em>out</em>.println(“stat1 is empty = ” + stat1.isEmpty() + “
”);




<em><u>Example output:</u></em>

stat1 data = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0] stat1 min = 1.0 stat1 max = 9.0 stat1 average = 5.0 stat1 mode = NaN stat1 variance = 6.666666666666667 stat1 standard deviation = 2.581988897471611

stat1 is empty = false




stat1 data = [] stat1 min = NaN stat1 max = NaN stat1 average = NaN stat1 mode = NaN stat1 variance = NaN stat1 standard deviation = NaN stat1 is empty = true




<h1>Example 3</h1>

<em><u>Example main method:</u></em>       <em> </em>

<strong>float</strong>[] data1 = {10.0F,10.0F};

Stat stat1 = <strong>new</strong> Stat(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average());

System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”);                 <strong>long</strong>[] data2 = {80L, 60L};

stat1.append(data2);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average());

System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”);




<em><u>Example output:</u></em>

stat1 data = [10.0, 10.0] stat1 min = 10.0 stat1 max = 10.0 stat1 average = 10.0 stat1 mode = 10.0 stat1 variance = 0.0

stat1 standard deviation = 0.0




stat1 data = [10.0, 10.0, 80.0, 60.0] stat1 min = 10.0 stat1 max = 80.0 stat1 average = 40.0 stat1 mode = 10.0 stat1 variance = 950.0

stat1 standard deviation = 30.822070014844883




<h1>Example 4</h1>

<em><u>Example main method:</u></em>

<strong>double</strong>[] data1 = {50.0, 60.0}; <strong>float</strong>[]  data2 = {70.0F, 80.0F}; <strong>int</strong>[]    data3 = {90, 100}; <strong>long</strong>[]    data4 = {100L, 110L};

Stat stat1 = <strong>new</strong> Stat();

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());                                 stat1.setData(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString()); stat1.setData(data2);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString()); stat1.setData(data3);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString()); stat1.setData(data4);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString()); data1 = <strong>null</strong>; stat1.setData(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());




<em><u>Example output:</u></em> stat1 data = [] stat1 data = [50.0, 60.0] stat1 data = [70.0, 80.0] stat1 data = [90.0, 100.0] stat1 data = [100.0, 110.0] stat1 data = []




<h1>Example 5</h1>

<em><u>Example main method:</u></em>

<strong>double</strong>[] data1 = {50.0, 60.0}; <strong>float</strong>[]  data2 = {70.0F, 80.0F};

<strong>int</strong>[]    data3 = {90, 100}; <strong>long</strong>[]    data4 = {100L, 110L};

Stat stat1 = <strong>new</strong> Stat();

System.<em>out</em>.println(“stat1 data = ” + stat1.toString()); stat1.append(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

stat1.append(data2);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString()); stat1.append(data3);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString()); stat1.append(data4);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString()); data1 = <strong>null</strong>; stat1.append(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average());

System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”);




<em><u>Example output:</u></em> stat1 data = [] stat1 data = [50.0, 60.0] stat1 data = [50.0, 60.0, 70.0, 80.0] stat1 data = [50.0, 60.0, 70.0, 80.0, 90.0, 100.0] stat1 data = [50.0, 60.0, 70.0, 80.0, 90.0, 100.0, 100.0, 110.0] stat1 data = [50.0, 60.0, 70.0, 80.0, 90.0, 100.0, 100.0, 110.0] stat1 min = 50.0 stat1 max = 110.0 stat1 average = 82.5 stat1 mode = 100.0 stat1 variance = 393.75

stat1 standard deviation = 19.84313483298443




<strong>Example 6</strong>

<em><u>Example main method:</u></em> <strong>double</strong>[] data1 = {10,10}; <strong>int</strong>[] data2 = {10,10}; Stat stat1 = <strong>new</strong> Stat(data1);

Stat stat2 = <strong>new</strong> Stat(data2);

Stat stat3 = <strong>new</strong> Stat();

Stat stat4 = <strong>null</strong>;

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat2 data = ” + stat2.toString());

System.<em>out</em>.println(“stat2 data = ” + stat2.toString());

System.<em>out</em>.println(“stat1 equals stat2 = ” +  stat1.equals(stat2));

System.<em>out</em>.println(“stat1 equals stat3 = ” +  stat1.equals(stat3));

System.<em>out</em>.println(“stat1 equals stat4 = ” +  stat1.equals(stat4));




<em><u>Example output:</u></em>

stat1 data = [10.0, 10.0] stat2 data = [10.0, 10.0] stat2 data = [10.0, 10.0] stat1 equals stat2 = true stat1 equals stat3 = false stat1 equals stat4 = false




<h1>Example 7</h1>

<em><u>Example main method:</u></em>

<strong>double</strong>[] data1 = {}; <strong>double</strong>[] data2 = { 25 }; <strong>float</strong>[] data3 = {}; <strong>float</strong>[] data4 = { 25 }; <strong>int</strong>[] data5 = {}; <strong>int</strong>[] data6 = { 50 }; <strong>long</strong>[] data7 = {}; <strong>long</strong>[] data8 = { 12 }; Stat stat1 = <strong>new</strong> Stat(); stat1.append(data1); stat1.append(data2); stat1.append(data3); stat1.append(data4); stat1.append(data5); stat1.append(data6); stat1.append(data7); stat1.append(data8); data1 = <strong>null</strong>; stat1.append(data1);

System.out.println(“stat1 data = ” + stat1.toString());

System.out.println(“stat1 min = ” + stat1.min());

System.out.println(“stat1 max = ” + stat1.max());

System.out.println(“stat1 average = ” + stat1.average());

System.out.println(“stat1 mode = ” + stat1.mode());

System.out.println(“stat1 variance = ” + stat1.variance());

System.out.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”);




<em><u>Example output:</u></em>

stat1 data = [25.0, 25.0, 50.0, 12.0] stat1 min = 12.0 stat1 max = 50.0 stat1 average = 28.0 stat1 mode = 25.0 stat1 variance = 189.5

stat1 standard deviation = 13.765899897936205