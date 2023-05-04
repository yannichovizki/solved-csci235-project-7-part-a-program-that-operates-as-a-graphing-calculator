Download Link: https://assignmentchef.com/product/solved-csci235-project-7-part-a-program-that-operates-as-a-graphing-calculator
<br>
<h1></h1>

This project is to write a program that operates as a graphing calculator. It will have a window that allows a user to enter in a function and set min and max values for <em>x</em> and <em>y</em> (to specify the viewing range); it will draw a graph of the function within the specified range. The original program that was written by Dr. VanDrunen looks like this:

You are not required to mimic the GUI exactly, but your program should have a window with the basic features/elements that are found in the example window.




The program should have three parts:

<ol>

 <li>Parsing and interpreting the function</li>

 <li>Making the window</li>

 <li>Drawing the actual graph</li>

</ol>







<strong>Interpreting the function </strong>

Download project files from Schoology.




The first task is similar to the Parse Tree program that we did in class and lab.




The calculator will display the graph of a function whose body is defined by the following expression:







<em>expression</em> à <em>numeral</em> | <em>x</em> | (<em>expression op expression</em>) <em>op</em> à + | – | / | * | ^

<strong> </strong>

Expressions now use floating point instead of integer. Thus, the values will be double rather than int.

Expressions can have a variable <em>x</em>.

The operator ^ (exponentiation) has been added.




Recall that the expression must be fully parenthesized. In addition, we do not allow a unary negation, and thus -3x^2 + 5 must be provided in the form of ((0 – (3 * (x ^ 2))) + 5) or (((0 – 3) * (x ^ 2)) + 5).

<strong> </strong>

As we did for Parse Trees, the calculator program must interpret an expression in String by building appropriate trees.

<strong> </strong>

<h1>Task #1: The Tree classes</h1>

The ExprNode interface has the evaluate method, double evaluate(double x);

The method now returns a double and has a double, formal parameter. This parameter <u>indicates the value</u> <u>of the variable <em>x</em></u>.

1




<u>Your task is to write classes </u><u>Number, </u><u>Variable, and </u><u>Operation which will implement </u><u>ExprNode</u>. You will need to figure out how each evaluate method will differ. (Hint: What will those classes do with the formal parameter <em>x</em>? The Variable class is<strong> the only one that will use it</strong>, the Number class will ignore it, and the Operation class will pass it along in the recursive calls.)

<strong> </strong>

<h1>Task #2: Building the trees</h1>

The class <sub>ExprStringSlicer</sub> does the same work, and the class <sub>Interpreter</sub> has a static method parse(). <u>Your task is to write the recursive </u><u><sub>parse</sub> method</u>. Its base cases will handle <sub>Number</sub> and Variable as the variable <em>x</em> has been introduced.

<strong> </strong>

You can test your work using the main method of the class, giving an expression (in quotes) and an <em>x</em>value on the command line, i.e., $java Interpreter “((0 – (x ^ 2)) + 5)” 3.5

<strong> </strong>

Don’t worry yet about handling erroneous input.




<h1>Task #3: Displaying the window</h1>

The PaintPanel and Painter are provided. <u>Your task is to complete the main method of </u><u>GraphCalc</u>. The class already has some code for GUI components as seen below. You can rearrange those components and add them to your window, panels, or layout managers.




public static void main(String[] args) {




JFrame window = new JFrame(“Graphing calculator”);

window.setLayout(new FlowLayout());

window.setSize(350, 600);




PaintPanel graphPanel = new PaintPanel(350, 350);




JTextField funcField = new JTextField(25);

JTextField xminField = new JTextField(5);

JTextField yminField = new JTextField(5);

JTextField xmaxField = new JTextField(5);

JTextField ymaxField = new JTextField(5);




xminField.setText(“-10”);         xminField.setText(“-10”);         xmaxField.setText(“10”);         ymaxField.setText(“10”);




JButton go = new JButton(“Go”);




window.add(graphPanel);    JPanel panel2 = new JPanel();     panel2.setLayout(new FlowLayout());

panel2.add(go);      window.add(panel2);         window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

window.setVisible(true);

}







The last task of this project will be drawing the graph on the <sub>PaintPanel</sub> whenever the Go button is pressed.

2


