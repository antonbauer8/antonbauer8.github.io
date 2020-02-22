---
layout: page
title: Java GUI and Event Handling
---

## Swing / AWT:
### AWT
- First Java GUI library was known as the Abstract Windows Toolkit (AWT). 
- AWT is fine for developing simple graphical user interfaces, but not for complex GUI projects. 
- A newer, more robust, and flexible library is known as Swing components. 
- Not used often today

### Swing
- Swing components are less dependent on the target platform and use less of the native GUI resource. 
- Swing components that don’t rely on native GUI are referred to as lightweight components and AWT components are referred to as heavyweight components.
- Much more common today

### AWT vs. Swing
- To distinguish new Swing component classes from their older AWT counterparts, the Swing GUI component classes are named with a prefixed `J`. 
- Although AWT components are still supported in Java, it is better to learn to how program using Swing components, because the AWT user- interface components will eventually fade away. 

### Using a GUI Builder
- Writing code for a GUI can be very tedious.
- Repetitive code, positioning widgets manually.
- Eclipse and NetBeans both have good WYSIWYG tools to build GUIs
- Drag and drop interface.
- Set component properties with dialog boxes.
- Automatic code generation.
- **BUT... WYSIWYG tools that generate code need developers that know what they are doing, which make these tools prone to great errors for novices**

## Layout Managers:

### Swing Layout Managers
- UI components are placed in containers
- Each container has a layout manager to arrange the UI components within the container
- Layout managers are set in containers using the setLayout(LayoutManager) method of the container object
- Full documentation on layout managers:  [link][1]
- *Reference generic layouts on lecture notes* [link][2]

### Null Layout / AbsoluteLayout:
- `setLayout(null)` means NO layout or absolute positioning.
- YOU set the size and position of all components yourself using each component’s setBounds()method.
- Advantage: works well in a GUI builder.
- Disadvantages:
	- VERY time-consuming to build/maintain without a GUI builder.
	- OS-dependent: components and fonts have different sizes on different systems.
	- No dynamic resizing of components.

#### Positioning Controls in Null Layout:
- Every SWING control has a setBounds()method

```java
private JFrame frmBank = new JFrame();
private JButton btnOK = new JButton("OK");

btnOK.setBounds(10, 10, 100, 30); //structured as (x-coord, y-coord, width, height)

frmBank.getContentPane().add(btnOK);
```
- ***NOTE***: The GUI Coordinate System starts with (0,0) in the top left corner and x values go right and y values go down
	- Basically the 4th quadrant of the Cartesian Coordinate System, but always use positive values

## Components:

- “Lightweight” GUI Objects
	- Bottom of the Swing hierarchy - placed inside top-level containers
	- Typically the objects to which we attach event handlers.
	- Support for tool tips and keyboard shortcuts for accessibility.
- All Swing components descend from JComponent 
	- Text components: `JTextComponent > JTextField, JTextArea`
	- `JButton, JLabel, JComboBox, JRadioButton, JCheckBox, JList, JSpinner, and more.`

### Creating GUI Objects:

```java
// Create a button with text OK 
JButton jbtOK = new JButton("OK"); 
 
// Create a label with text "Enter your name: " 
JLabel jlblName = new JLabel("Enter your name: "); 
 
// Create a text field with text "Type Name Here" 
JTextField jtfName = new JTextField("Type Name Here"); 
 
// Create a check box with text bold 
JCheckBox jchkBold = new JCheckBox("Bold"); 
 
// Create a radio button with text red 
JRadioButton jrbRed = new JRadioButton("Red"); 
 
// Create a combo box with choices red, green, and blue 
JComboBox jcboColor = new JComboBox(new String[]{"Red", "Green", "Blue"}); 
```

### Text Boxes:
- JTextArea - Accepts/displays multiple lines of text
		- Constructor:
		- `JTextArea textArea = new JTextArea(5, 40);`
	- 2 Useful Methods:
		- `textArea.setText("something");  // Overwrites text!`
		- `textArea.append("Hello, " + name + "\n");`

- JTextField - Accepts/displays a single line of text
	- Constructor:
		- `JTextField jtfName = new JTextField("Text");`

### Buttons:
- Constructor & Usage:
	- `JButton button = new JButton("Login");`

### Radio Buttons:
- User may choose one item from a small number of choices
	- Constructor:
		- `JRadioButton smallRB = new JRadioButton("Small");`
		- `JRadioButton mediumRB = new JRadioButton("Medium");`
- To make a set of JRadioButton objects work together, add them to a ButtonGroup object.
	- Example:

```java 
    ButtonGroup group = new ButtonGroup();
    group.add(smallRB);
    group.add(mediumRB);
    group.add(largeRB);

    // Turn "on" the "Small" radio button 
    smallRB.setSelected(true);
```

### Check Boxes:
- User may select (check) multiple items from a small number of choices
	- Constructor:
		- `JCheckBox boldCheckBox = new JCheckBox("Bold");`
	- Common methods:
		- `boldCheckBox.setSelected(true);  // set state`
		- `boldCheckBox.isSelected(); // true or false`
		- `boldCheckBox.setEnabled(false); // disable box`

### Combo Boxes:
- JComboBox is a small drop-down menu
	- User can select one of many items.
	- JComboBox can store any kind of object, not just Strings!
		- Method call : `comboBox.addItem(Object o);`
		- Object array : `String[] states = {"Ohio", "New York"};`
	- By default, a combo box is not editable by the user.
	- Use setEditable(true) method to allow users to type in their own text.

	- Constructor & Usage:

```java
    JComboBox combo = new JComboBox();
    combo.addItem("Pennsylvania");
    combo.addItem("Ohio");

// Get the user's choice
String stateStr = (String) combo.getSelectedItem();
```

### GUI Control Naming Conventions:
|**Gui Control**| **Prefix**  | **Example**       |
| ------------- |:-----------:| -----------------:|
| JButton       | btn         | btnValidatePin    |
| JComboBox     | cbo         | cboAccountList    |
| JCheckBox     | chk         | chkAwesomeCheckBox|
| JRadioButton  | rad         | radAccountOptions |
| JTextArea     | txt         | txtPinNumber      |
| JTextField    | txt         | txtPinNumber      |
| JLabel        | lbl         | lblPinNumber      |


## Event Handling:
- Events in Java:
	- Event --\> Event Listener --\> Event Handler
- What Are Events?
	- Anything that a user can do to a GUI:
		- Click
		- Right-click
		- Move mouse
		- Enter a text field
		- Leave a text field
		- Open/close windows

- **Timer events**
	- Something that happens automatically after a specified period of time had elapsed or at specific points in time
- **External events:**
	- Push notifications
	- Emails
	- Keywords in newsfeeds
	- Virtually anything...

### Event Listeners:
- Either built-in or custom Java classes that listen (wait) for a specific event to occur
- Statements called by event listeners are not executed until the event actually occurs

### Event Handlers:
- Statements / code called by event listeners and executed in response to an event.

```java
JButton btnTestButton = new JButton("Test Button");
btnTestButton.addActionListener(new ActionListener() { //This part is the event listener
    public void actionPerformed(ActionEvent e) { 
        // code here will be executed
        // after btnTextButton is clicked
        //This part is the event handler
    }
});
```

### Event Objects:
- Objects that are passed to event handlers by event listeners.
- Contain information about event that triggered the handler
- Example: for an MouseClick event (user clicked a GUI object with a mouse), event object will contain properties such as mouse click coordinates.

```java
public void actionPerformed(ActionEvent e) //ActionEvent e is the event object
```

- Resource on Events:
[link][3]

[1]:	http://docs.oracle.com/javase/tutorial/uiswing/layout/visual.html "Swing Layout Managers"
[2]:	https://docs.google.com/presentation/d/163l3IffXliWCZYZNGJDexABoeT0y_crW6vcVE4AsA7U/edit#slide=id.p46 "Lecture Notes"
[3]:	http://docs.oracle.com/javase/tutorial/uiswing/events/ "Event Resource"