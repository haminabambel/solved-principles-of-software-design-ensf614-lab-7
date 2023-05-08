Download Link: https://assignmentchef.com/product/solved-principles-of-software-design-ensf614-lab-7
<br>
Note: This lab is a group assignment, and you can work with a partner. Groups of 3 or more are not allowed.

<strong>Introduction:</strong>

This lab is also on design patterns. The main objective of this lab is to give you an opportunity to practice a few more important design patterns: Observer, Decorator, and Singleton pattern.

<strong><u>Marking Scheme: (30 marks total) </u></strong>

<ul>

 <li>Exercise B: 16 marks</li>

 <li>Exercise C: 4 marks</li>

 <li>Exercise D: 10 marks</li>

</ul>

<strong>Due Date</strong><strong>:</strong><strong> Tuesday Nov 23 before 5:00 PM</strong>.

<strong>A Brief Note on Application of Decorator Design Patten in Real World:</strong>

The concept of a decorator focuses on the dynamically adding new futures/attributes to an object and particularly to add the new feature the original code and other added code for other features must remains unaffected. The Decorator pattern should be used when object responsibilities/feature should be dynamically changed and the concrete implementations should be decoupled from these features. To get a better idea the following figures can help:

Figure from <a href="https://www.codeproject.com/Articles/176815/The-Decorator-Pattern-Learning-with-Shapes">https://www.codeproject.com/Articles/176815/The-Decorator-Pattern-Learning-with-Shapes</a>                 Figure from: <a href="https://conceptf1.blogspot.ca/2016/01/decorator-design-pattern.html">http://conceptf1.blogspot.ca/2016/01/decorator-design-pattern.html</a>

The left figure shows how an original object is furnished by additional attributes. A better real world example is the




on the right that shows how the basic BBQ-chicken pizza is decorate by onion, extra-cheese, and mushrooms.

<strong>Official Definition of the Decorator Pattern:</strong>

The Decorator is a <strong>structural </strong>pattern, because it’s used to form large object structures across many disparate objects. The official definition of this pattern is that:

<strong><em>It allows for the dynamic wrapping of objects in order to modify their existing responsibilities and behaviours.</em></strong>

Traditionally, you might consider subclassing to be the best way to approach this. However, not only subclassing isn’t always a possible way, but the main issue with subclassing is that we will create objects that are strongly coupled, and adding any new feature to the program involves substantial changes to the existing code that is normally a desirable approach.

<table>

 <tbody>

  <tr>

   <td width="451">

    <table width="100%">

     <tbody>

      <tr>

       <td></td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

Let’s take a look at the following class diagram that express the concept of Decorator Pattern:

Figure 3

This diagram has three main elements:

<ul>

 <li>The Component Interface, that defines the interface for objects that need their features to be added</li>

 <li>The Concreter Component, implementing interface Component</li>

 <li>The Decorator, implementing the Component interface and aggregating a reference to the component. This is the important thing to remember, as the Decorator is essentially wrapping the Component. And, one or more Concrete Decorators, extended from Decorator</li>

</ul>

<strong><u>Exercise A:</u></strong>

Lets assume you are working as part of a software development team that you are responsible to write the required code for implementing a simple graphics component that is supposed to look like:

But the detail of this component is displayed in the following figure that consists of a main object, a text area with green color text, which is decorated with two added features: a black border that is a dashed line, and a thicker red color frame.




<strong>What to Do:</strong>

To implement this task refer to the following UML diagram. Also download file DemoDecoratorPattern.java that uses this pattern to test your work:




If your decorator pattern design is properly implemented the output of your program should look like this figure:

<strong><u>Exercise B</u></strong>

Now let’s assume you need to add another decorator. But this time object text must be covered with transparent green-glass cover that it looks like:




<strong>What to Do:</strong>




You should add a new class called ColouredFrameDecorator that decorates the text area with the

new decorating feature which a green glass. Now if you replace the current paintComponent method in the file DemoDecoratorPattern.java with the following code;

<strong>public void</strong> paintComponent(Graphics g){

<strong>int</strong> fontSize = 10;

g.setFont(<strong>new</strong> Font(“TimesRoman”, Font.<strong><em>PLAIN</em></strong>, fontSize));

// GlassFrameDecorator info: x = 25, y = 25, width = 110, and height = 110

t =<strong> new</strong> ColouredGlassDecorator(<strong>new</strong> ColouredFrameDecorator(

<strong>new</strong> BorderDecorator(t, 30, 30, 100, 100), 25, 25, 110, 110, 10), 25, 25, 110, 110);

t.draw(g);

}

The expected output will be:

<strong><u>Sample code that may help you for drawing graphics in java: </u></strong>

Sample Java code to create a rectangle at x and y coordinate of 30 and width and length of 100:

g.drawRect(30, 30,    100,   100);

Sample Java code to create dashed line:

Stroke dashed =<strong> new</strong> BasicStroke(3, BasicStroke.<strong><em>CAP_BUTT</em></strong>, BasicStroke.<strong><em>JOIN_BEVEL</em></strong>, 0,<strong> new</strong> <strong>float</strong>[]{9}, 0);




Graphics2D g2d = (Graphics2D) g; g2d.setStroke(dashed);

Sample Java code to set the font size

<strong>int</strong> fontSize = 10;

g.setFont(<strong>new</strong> Font(“TimesRoman”, Font.<strong><em>PLAIN</em></strong>, fontSize));

Sample Java code to fill a rectangle with some transparency level:

Graphics2D g2d = (Graphics2D) g;

g2d.setColor(Color.<strong><em>yellow</em></strong>); g2d.setComposite(AlphaComposite.<em>getInstance</em>(AlphaComposite.<strong><em>SRC_OVER</em></strong>, 1 * 0.1f)); g2d.fillRect(25,  25,  110,    110);

<strong>What to Submit for Exercises A and B:</strong>

<ol>

 <li>Copy and paste all your source codes and your program output as part of your lab report and submit it in PDF format.</li>

 <li>Create and submit a zip file that contains your source code file (.java files)</li>

</ol>

<strong><u>Exercise C – Developing Singleton Pattern in C++</u></strong><strong><u>  </u></strong><strong>Objective:</strong>

The purpose of this simple exercise is to give you an opportunity to learn how to use Singleton Pattern in a C++ program.

<strong>When Do We Use It?</strong>

Sometimes it’s important to have only one instance for a class. Usually singletons are used for centralized management of resources, where they provide a global point of access to the resources. Good examples include when you need to have a single:

<ul>

 <li>Window manger</li>

 <li>File system manager</li>

 <li>Login manager</li>

</ul>

The singleton pattern is one of the simplest design patterns: it involves only one class which is responsible to instantiate itself, to make sure it creates not more than one instance; in the same time it provides a global point of access to that instance. In this case the same instance can be used from everywhere, being impossible to invoke directly the constructor each time.

<strong>Implementation:</strong>

The implementation involves a static member in the “Singleton” class, a private constructor and a static public method that returns a reference to the static member. A class diagram that represents the concept of this pattern is as follows:




<strong>What to Do – Part I:</strong>

<strong>Step 1: </strong>download file main.cpp from D2L.

<strong>Step 2: </strong>write the class definitions as indicated in the following UML diagram: class LoginServer, class Client_A, class Client_B, and struct User.

<strong>Step 3: </strong>compile and run your classes with the given main.cpp to find out if your Singleton Pattern works.

<strong>What to Do – Part II:</strong>

Now you should test your code for an important fact about Singleton Pattern. At the end of the given file main.cpp there is a conditional compilation directive, #if 0. Change it to #if 1 and report what happens:

<ul>

 <li>Does your program allow creating objects of LoginServer?</li>

 <li>If yes, is an object of LoginServer able to find user “Tim”?</li>

</ul>




¥ If no, why?

<strong>What to Submit:</strong>

<ol>

 <li>Copy and paste all your source codes and your program output as part of your lab report and submit it in PDF format.</li>

 <li>2 answers to the question in Exercise D, part II</li>

 <li>Create and submit a zip file that contains your source code file (.java files)</li>

</ol>