<div align="center">

## StudentGrades


</div>

### Description

This is a simple program that I wrote for a school project. It basically allows a user to input student names, grades (i.e., 3.5, 4.0, etc.), and the student ID. Then it calculates the highest grade and outputs the name of the student with the highest grade, outputs all the B's (3.0 - 3.9), and the class average. It will also sort Student by ID.
 
### More Info
 
Inputs are the name, Id, and grade. The name is a String as well as the Id and the grade. However, the Id and grade will be returned as an int for id and a float for grade.

You need to have JVM installed. For simple work with Java I use Textpad. The focus does not default to any particular button so you will need to use your mouse to click vice the Enter key. Feel free to modify and play any way you want. You will need to compile it, too. Good Student project.

id as an int

grade as a float


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Gregory Jones](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/gregory-jones.md)
**Level**          |Beginner
**User Rating**    |4.0 (8 globes from 2 users)
**Compatibility**  |Java \(JDK 1\.2\)
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__2-57.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/gregory-jones-studentgrades__2-2020/archive/master.zip)





### Source Code

```
//imported files from the jdk
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.util.*;
/**
*  StudentGrades is a class utilizes the GUI to compute student grades
*  in various ways.
*
*
* @author Gregory M. Jones
* @version 1.1
*
*/
	public class StudentGrades extends JFrame {
	private JLabel name, id, grade, classAverage, highScore, scoreId, score, bs, studentList, sorted, explain;
	private JTextField nameText, idText, gradeText, highScoreText, classAveText, idScoreText, scoreText, bsText;
	private JTextArea listText, sortText;
	private JButton enterButton, averageButton, highScoreButton, bsButton, sortButton;
	/**used to keep track of the current number of students added
	*/
	private int scount=0;
	/**Creates an array of Students (0 through 9).
	*/
	private Student[] Students = new Student[9];
	class Student {
	  private String name;
	  private int id;
	  private float grade;
	  /** Gives assignments for array variables of class Student
	  */
	  public Student( String n, int d, float g )
	  {
	   name = n;
	   id = d;
	   grade = g;
	  }
	  /** getName method returns the 'name' in the Student array.
	  */
	  public String getName() { return name; }
	  /** getId method returns the 'id' in the Student array.
	  */
	  public int getId() { return id; }
	  /** getGrade method returns the 'grade' in the Student array.
	  */
	  public float getGrade() { return grade;}
	}
	/**Method for developing the GUI outline.
	*/
	public StudentGrades()
	{
		super( "Student Grades - Blazing Anger By: Greg Jones" );//Display title of program in title bar.
		/**Bring in the container
		*/
		Container c = getContentPane();
		/**Define a new JPanel for Name label and text field.
		*/
		JPanel namePanel = new JPanel();
		namePanel.setLayout(new FlowLayout(FlowLayout.RIGHT, 5, 5));
		name = new JLabel("Name");
		name.setFont(new Font("Serif", Font.BOLD, 16));
		namePanel.add(name);
		nameText = new JTextField(10);
		namePanel.add(nameText);
		/**Define a new JPanel for Id label and text field.
		*/
		JPanel idPanel = new JPanel();
		idPanel.setLayout(new FlowLayout(FlowLayout.RIGHT, 5, 5));
		id = new JLabel("ID");
		id.setFont(new Font("Serif", Font.BOLD, 16));
		idPanel.add(id);
		idText = new JTextField(10);
		idPanel.add(idText);
		/**Define a new JPanel for Grade label and text field.
		*/
		JPanel gradePanel = new JPanel();
		gradePanel.setLayout(new FlowLayout(FlowLayout.RIGHT, 5, 5));
		grade = new JLabel("Grade");
		grade.setFont(new Font("Serif", Font.BOLD, 16));
		gradePanel.add(grade);
		gradeText = new JTextField(10);
		gradePanel.add(gradeText);
		/**Define a new JPanel for Class Average label and text field.
		*/
		JPanel classAveragePanel = new JPanel();
		classAveragePanel.setLayout(new FlowLayout(FlowLayout.RIGHT, 5, 5));
		classAverage = new JLabel("Class Average");
		classAverage.setFont(new Font("Serif", Font.BOLD, 16));
		classAveragePanel.add(classAverage);
		classAveText = new JTextField(10);
		classAveragePanel.add(classAveText);
		/**Define a new JPanel for High Score label.
		*/
		JPanel highScorePanel = new JPanel();
		highScorePanel.setLayout(new FlowLayout(FlowLayout.CENTER, 5, 5));
		highScore = new JLabel("High Score");
		highScore.setFont(new Font("Serif", Font.BOLD, 16));
		highScorePanel.add(highScore);
		/**Define a new JPanel for ID label and text field.
		*/
		JPanel scoreIdPanel = new JPanel();
		scoreIdPanel.setLayout(new FlowLayout(FlowLayout.RIGHT, 5, 5));
		scoreId = new JLabel("ID");
		scoreId.setFont(new Font("Serif", Font.BOLD, 16));
		scoreIdPanel.add(scoreId);		idScoreText = new JTextField(10);
		scoreIdPanel.add(idScoreText);
		/**Define a new JPanel for Score label and text field.
		*/
		JPanel scorePanel = new JPanel();
		scorePanel.setLayout(new FlowLayout(FlowLayout.RIGHT, 5, 5));
		score = new JLabel("Score");
		score.setFont(new Font("Serif", Font.BOLD, 16));
		scorePanel.add(score);
		scoreText = new JTextField(10);
		scorePanel.add(scoreText);
		/**Define a new JPanel for B's label and text field.
		*/
		JPanel bsPanel = new JPanel();
		bsPanel.setLayout(new FlowLayout(FlowLayout.RIGHT, 5, 5));
		bs = new JLabel("B's");
		bs.setFont(new Font("Serif", Font.BOLD, 16));
		bsText = new JTextField(10);
		bsPanel.add(bs);
		bsPanel.add(bsText);
		/**Define a new JPanel for Student ID List and ID's Sorted labels.
		*/
		JPanel listTitlePanel = new JPanel();
		listTitlePanel.setLayout(new FlowLayout(FlowLayout.LEFT, 5, 5));
		studentList = new JLabel("Student ID List  ");
		studentList.setFont(new Font("Serif", Font.BOLD, 16));
		sorted = new JLabel("ID's Sorted");
		sorted.setFont(new Font("Serif", Font.BOLD, 16));
		listTitlePanel.add(studentList);
		listTitlePanel.add(sorted);
		/**Define a new JPanel for Student ID List and ID's Sorted text
		*areas.
		*/
		JPanel listTextPanel = new JPanel();
		listTextPanel.setLayout(new FlowLayout(FlowLayout.CENTER, 5, 5));
		listText = new JTextArea(15, 5);
		listText.setFont(new Font("Serif", Font.BOLD, 12));
		sortText = new JTextArea(15, 5);
		sortText.setFont(new Font("Serif", Font.BOLD, 12));
		listTextPanel.add(listText);
		listTextPanel.add(sortText);
		/**Define a main JPanel to hold all the other panels with the
		*BoxLayout Manager
		*/
		JPanel mainPanel = new JPanel();
		mainPanel.setLayout(new BoxLayout(mainPanel, BoxLayout.Y_AXIS));
		/**Add each of the above defined JPanels to the mainPanel
		*/
		mainPanel.add(namePanel);
		mainPanel.add(idPanel);
		mainPanel.add(gradePanel);
		mainPanel.add(classAveragePanel);
		mainPanel.add(highScorePanel);
		mainPanel.add(scoreIdPanel);
		mainPanel.add(scorePanel);
		mainPanel.add(bsPanel);
		mainPanel.add(listTitlePanel);
		mainPanel.add(listTextPanel);
		c.add(mainPanel, BorderLayout.WEST);//add the main panel.
		/**Create a separate JPanel for the JButtons
		*/
		JPanel buttonPanel = new JPanel();
		buttonPanel.setLayout(new FlowLayout(FlowLayout.RIGHT, 5, 5));
		enterButton = new JButton ("ADD STUDENT");
		averageButton = new JButton ("AVERAGE");
		highScoreButton = new JButton ("HIGH SCORE");
		bsButton = new JButton ("DISPLAY B's");
		sortButton = new JButton ("SORT ID's");
		explain = new JLabel ("Press until all sorted.");
		c.add(buttonPanel);//add the button panel.
		/**Add the Buttons to the button panel.
		*/
		buttonPanel.add(enterButton);
		buttonPanel.add(averageButton);
		buttonPanel.add(highScoreButton);
		buttonPanel.add(bsButton);
		buttonPanel.add(sortButton);
		buttonPanel.add(explain);
	/**Event Handler (ActionListener) for the Enter Button. Runs the addstudent and
	*addIdList methods.
	*/
	enterButton.addActionListener(new ActionListener()
	{
		public void actionPerformed(ActionEvent e)
	  {
		 addstudent();
		 addIdList();
		 //This is an alternate set of method calls that will call calc_avg, calc_hs, and
		 //calc_bs when the Enter button is hit. Automatically updates the average,
		 //High Score and # of B's as you add students.
	   //Just remove the comment '//' tags if you want to use the Enter button for these methods.
	   //calc_avg();
	   //calc_hs();
	   //calc_bs();
		}
	}
  );
	/**Event Handler (ActionListener) for Average Button. Calls calc_ave method.
	*/
	averageButton.addActionListener(new ActionListener()
	{
   public void actionPerformed(ActionEvent e)
   {
		calc_avg();
	 }
	}
	);
	/**Event Handler (ActionListener) for High Score Button. Calls calc_hs method.
	*/
	highScoreButton.addActionListener(new ActionListener()
	{
   public void actionPerformed(ActionEvent e)
   {
		calc_hs();
	 }
	}
	);
	/**Event Handler (ActionListener) for B's Button. Calls calc_bs method.
	*/
	bsButton.addActionListener(new ActionListener()
	{
   public void actionPerformed(ActionEvent e)
   {
		calc_bs();
	 }
	}
	);
	/**Event Handler (ActionListener) for the Sort Button. Calls sortIdArray method.
	*/
 	sortButton.addActionListener(new ActionListener()
  {
   public void actionPerformed(ActionEvent e)
		 {
			 sortIdArray();
		 }
	 }
  );
	/**Set size of container and call show method.
	*/
		setSize( 400, 600 );
		show();
	}
/**addstudent method that adds a student to the array.
*/
private void addstudent()
{
	String name,tempid,tempgrade;
	int id;
	float grade;
	if (scount < 10)
	{
		//Gets the text from the text Fields
		name = nameText.getText();
		tempid = idText.getText();
		tempgrade = gradeText.getText();
		if (tempid.length() != 0 && tempgrade.length() != 0 && name.length() != 0)
		{
			//makes the actual student class inside of the array
			Students[scount] = new Student(name,Integer.parseInt(tempid),Float.parseFloat(tempgrade));
			//Integer.parseInt() takes a string value and returns an Integer.
			nameText.setText(""); //resets the text fields back to blank.
			idText.setText("");
			gradeText.setText("");
			nameText.requestFocus();//Sets the cursor to the name field
			scount++;//adds one to the student counter
			}
	}
}
/** addIdList method that adds the student ID's to the listText Text Area
*/
private void addIdList() {
 byte i = 0;
 String tempStr = new String();
 for (i=0; i < scount; i++) {
  tempStr += Students[i].getId() + "\n";//gets the id via the getId method for array and assigns to tempStr
 }
 listText.setText(tempStr);
 }
/**Sort array of id's and print out to sortText Text Area.
*/
private void sortIdArray() {
 sortText.setText("");
 byte i = 0;
 String tempStr = new String();
	Student tempStudent;
 for (i = 0; i < scount-1; i++)
	{
		if (Students[i].getId() > Students[i+1].getId())
		{
			tempStudent = Students[i+1];
			Students[i+1] = Students[i];
			Students[i] = tempStudent;
		}
 }
	for (i=0; i < scount; i++) {
  tempStr += Students[i].getId() + "\n";
 }
	sortText.setText(tempStr);
}
/**Calculates all the b's
*/
private void calc_bs()
{
	int bcount=0;
	for(int i=0;i<scount;i++){ if (Students[i].getGrade() <4f && Students[i].getGrade() >= 3f){bcount ++;}}
	//makes a new Integer for a sec with the bcount value, converts it to a string, and then sets
	//the text to it
	bsText.setText(new Integer(bcount).toString());
}
/**Finds the High Score
*/
private void calc_hs()
{
	String stuname = "";
	int stuid = 0;
	float stugrade = 0f, bgrade = 0f;
	for (int i = 0;i < scount;i++)
	{
		//Compares to see if the current students grade is greater then the last best grade, if it is
		//records the name, id and grade for later use.
		if (bgrade < Students[i].getGrade())
		{
			stuname = Students[i].getName();
			stuid = Students[i].getId();
			stugrade = Students[i].getGrade();
			bgrade = stugrade;
		}
	}
	//Changes the text fields to the values recorded earlier
	highScore.setText("High Score : " + stuname);//Changes highscore label and appends the name of the
												//student with high score to label.
	idScoreText.setText(new Integer(stuid).toString());
	scoreText.setText(new Float(stugrade).toString());
}
/**Calculates the average
*/
private void calc_avg()
{
 float totalGrades = 0,studentGrade = 0;
 Float averageGrades;
 for (int i=0;i<scount;i++)
 {
	studentGrade = Students[i].getGrade();
	totalGrades += studentGrade;
 }
 averageGrades = new Float(totalGrades/scount);
 classAveText.setText(averageGrades.toString());
}
/**Adds student ID's to listText Text Area
*/
private void addidlist()
{
	//String stuname = "";
	int stuid = 0;
	//float stugrade = 0f, bgrade = 0f;
	for (int i = 0;i < scount;i++)
	{
			stuid = Students[i].getId();
	}
	listText.setText(new Integer(stuid).toString());
}
/**main method
*/
public static void main( String args[] )
{
	StudentGrades app = new StudentGrades();
	app.addWindowListener(
		new WindowAdapter() {
			public void windowClosing( WindowEvent e )
			{
				System.exit( 0 );
			}
		}
		);
	}
}
```

