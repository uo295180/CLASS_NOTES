##  INTRODUCTION TO THE DEVELOPMENT OF VISUAL APPLICATIONS

Java Foundation Classes is the standard API for GUI in Java. It has three libraries: 
1. **AWT**: 
	It allows the contruction of GUI for every version of the JDK
2. **Swing**: 
	Based in AWT, it allows more advanced GUI.
3. **Java2D**
### AWT

It can build any GUI to be executed in **every version** of the JDK. Designed as a standard API  that allows to use native components of the operating system. 
- Drawbacks:
	- Only the functionalities present in every operating system are available
	- It's very difficult to build portable applications.

AWT provides containers, components, events and layouts. A component must be inside a container and thy expect an action from the user (event). A container is also a component, so it can be inside other containers too. The layout decides the way components are placed inside containers. 
Packages:
 -  java.awt.*;
 - java.awt.event*;

### SWING

Published in 1997 to solve limitations of AWT. Its package is **java.swing**. Their components are:
- Written in Java
- Homogenous Look and Feel between platforms
- Can be used in every platform with Java 1.1 or newer

>[!info]-
>Swing is part of the JDK since JDK 1.2

>[!note]
>Swing can change the look and feel of the application on runtime

If we compare Swing to AWT, we can see that:
- Swing has more components than AWT
	- Tables, trees, sliders, spinners, progress bars, internal frames and text components
	- It allows to add borders to the components
- Components can have *tooltips*
- Allows to link keyboard events to components

Swing architecture is based on containers and components, and the interaction between the system and the user is done through events

### Components

- Elements that the user can interact with. Basic elements for the GUI development. 
- A component has:
	- **Properties** (with default values)
	- **Methods** (functionality)
	- **Events**: Internal or external signal that fires the execution of a code block implementd as a method. Examples
		- Mouse Click ^5b7c56
		- Call a method
		- Modify a property

>[!info]-
>The developer must write the code to manage every event involved in the interaction

### Containers

- Group components
- Containers:
	- Contains and manage components
	- They're also components
- Containeres places components applying a **layout**.

### Composite design pattern
Compose objects into tree structures to represent part-whole hierarchies. It lets clients managing individual objects and compositions of objects uniformly

>[!When to use?]-
>It can be used when clients should ignore the difference between compositions of objects and individual objects

### Basic components

In Swing a window is implemented by a high-level container (*JFrame*). JFrames cannot be inside other containers. JFrames can only contain one component, a *JPanel* named *ContentPane* that should contain all the other components.
![[Pasted image 20231030172120.png]]



## THEORY PILLS LABS 1 & 2

### Containers

Main type of containers:
- Frame (JFrame)
- Dialog (JDialog)
- Panel (JPanel)
- Scroll Panel (JScrollPane)
- Tabbed panel (JTabbedPane)
- Tool bar (JToolBar)

#### Frame (JFrame)

- It cannot be contained by any other window. (Main window)
- It has border, title, control menu, minimizing and maximizing buttons and resizing controls
- It can contain **menu bars**
- It can only contain one panel (*contentPane*), that is in charge of containing all other components

#### Panel (JPanel)

- Groups components inside a window or a different panel
- Uses *Layout managers* to group and organize components
- Important methods:
	- getComponentCount() : number of components in the panel
	- getComponents() : set of components in the panel

### Basic components

**Buttons**:
- Command
- Flip-flop (*Toggle*)
- Check Boxes
- Radio Buttons
**Combo Box**

#### Command Buttons (JButton)

They can contain text, graphics or both. A mnemonic must be defined for fer each button except for the default button or the cancel button. Those without text must include a tooltip. Tooltips must be enabled by default, but we must provide an option to disable them (could be a checkbox) 
Buttons containing only text must show it centered, but those containing both must show the text right or under the graphics. If pressing a button involves interacting with another dialog we must add "..." at the end.

#### Toggle Buttons (JToggleButton)

Two states, on & off. Can have text and/or graphics. Both must state for both states. They can represent independent options or exclusive options. True means on and false means off.

#### CheckBox (JCheckBox)

Two states, on & off. Selected property evidences if the checkbox is selected or not

#### Radio buttons (JRadioButton)

Restricts the selection just to one of the grouped options. In Java, we need a ButtonGroup. Similar to toggle, but more convenient in dialogs. We can group them visually using titled panels. Properties and methods similar to checkBoxes.

#### ComboBoxes (JComboBox)

Used to select just one option between several. The text inside must be **capitalized**. Elements must be **ordered** and mnemonics must be defined. We can distinguish two types:
- Not Editable:
	- Also called List Boxes
	- They show a list from where the user can choose one element
		- We can use them instead of radio buttons
			- Space is limited
			- Too many options
			
- Editables:
	- User can key, select or modify the text.
	- It can help the user allowing him/her to key a value

### Text components

They allow the user to see & edit text:
- *JLabel*
- *JTextField*
- *JPasswordField*
- *JTextArea*

#### Label (JLabel)

They can contain both text or/and graphics and are non editable. They cannot be selected. Text must be **short** and terminology must  be familiar to users. We can use mnemonics to focus the component next to the label (*labelFor*). If their associated component is inactive, they should be too. Text inside must be capitalized and, if they refer to a component, they should end with ":". They have two main functions, identify components and notify about the state or guide the users.

#### Text Field (JTextField)

They show a text line. They can be editable to let the user write on it, or non editable, where users can select and copy text but they cannot change it. This text can only be modified programmatically. Mnemonics must be associated to the label. 

#### Password Field (JPasswordField)

Editable TextField that shows masked characters instead of the introduced by the user. Similar to textfield but without copying and pasting

#### Text Area (JTextArea)

Provides an space where the user can see, key and edit multiple lines. It has founts, size and simple style. We could include it into a ScrollPane if we need scrollbars

Properties:
- lineWrap -> True
- wrapStyleWord -> True

Methods:
- setText //
- append //
- insert //
## FOUNDATIONS OF HUMAN COMPUTER INTERACTION

>[!info]-
>We have interfaces everywhere. The pannel to control the radio or windows of our car is also an interface
### What's HCI?

>[!HCI (Human Computer Interaction) ]
>It's a discipline concerned with the **design, evaluation and implementation** of **interactive computing systems** for human use with the study of major phenomena surrounding them 
>[link](http://www.acm.org/sigchi/)

HCI involves user interfaces design, appart of many other aspects, but we're only concerned on the first topic.

### The User Interface

**Set of interaction points between user and system**. It involves every output and input. The UI is an important factor determining the **success or failure** of a product. 

>[!info]-
> - It involves around the 50% of the source code
> - More than 70% of the **development effort** in interactive applications 

A poor UI involves:
- Low productivity rates
- Unfeasible training periods
- High error rates that generate frustation

HCI's goal is to build or improve security, utility, effectiveness, efficiency, but mainly **USABILITY**, of interactive systems

### Usability

A product must be used by specified users to achieve specific goals with **effectiveness**, **efficiency** and **satisfaction** in a specific context of use.
	- *Effectiveness* is the complete and exact consecution of users' goal
	- *Efficiency* is the complete and exact consecution of users' goals in relation with the used resources. 
	- *Satisfaction* concerns the comfort and **user acceptance** of the system

Then, we can say that a system is *usable* when:
- It's **easy to learn**
- It's **easy to use**

Dimensions of usability:
- **Learnability (L):** is it easy to learn?
- **Efficiency (E):** once learned, is it fast to use?
- **Safety (S):** are errors few and recoverable?

>[!info]-
>Other dimensions that are relevant too:
>	- **Ergonomics:** Comfort, fatigue
>	- **Aesthetics:** Satisfaction, happiness

Then, usability concerns dialog design,  cognitive link between user and system, documentation quality, online help...
Several design principles can be applied, obtaining lower production costs, support and maintanence costs and use costs, and better quality rates of the products

We can divide this principles into three main categories:
- a. Learnability
- b. Flexibility
- c. Robustness

### A) Learnability

Goal: **Reduce the effort** that a new user must face to work with our system and become an **expert user**. For this purpose, we could use:
- A.1 Prediciton
- A.2 Synthesis
- A.3 Familiarity
- A.4 Consistency

##### A.1) Prediction

We can say that a **system is predictable** when the **initial experience** of t he user is **enough to guess** the result of future interactions. For that purpose, controlling the **visibility of operations**  enforces the predictability of the system.
	- Inform user about the **available** and **unavailable** operations![[Pasted image 20231030183240.png]]
	- They don't need to remember when an operation can be done or not

A system where the user is enforced to remember what was shown in the previous screen is not a predictable system

##### A.2) Synthesis

A **synthesizable system** informs the user about any change in the system, so they can be aware of this change. This notifications can be:
- **Inmmediate**: Shows the changes without user request. *(Ideal one)*![[Pasted image 20231030183816.png]]
- **Sporadic**: Changes are shown onlu after user request![[Pasted image 20231030183903.png]]


##### A.3) Familiarity

Correlation between users' knowledge and the knowledge requested for to interaction with a new system. It can be improved using **metaphors** from the real world that the user is already used to
![[Pasted image 20231030184130.png]]


##### A.4) Consistency

All the mechanisms should be used in the **same way**, whenever or wherever we use them. Consistence is a **foundation principle** in interface design. In order to reach it, we need:
- Use style guides
- Use a common *look and feel*
- Try to avoid changing the functionality of those techniques that user already knows. [Example](https://www.nngroup.com/articles/do-interface-standards-stifle-design-creativity/)


### B) Flexibility

The different ways that systems and users interachange information. For this purpose, we can use the following principles:
- B.1 Initiative in the dialog
- B.2 Task delegation
- B.3 Replacement capacity
- B.4 Customization capacity

##### B.1) Initiative in the dialog

Who takes the initiative in the communication? The system or the user?

>[!info]-
>Ideally: the user. However, sometimes it's interesting to let the system do it:
>	Example of a system-guided interaction:
>		Modal dialog that prevents the user from interacting with any other window of the application before closing it ("Save as" dialog in word)
>		

##### B.2) Task delegation

It involves the possibility of transferring task control from the user to the system (Security backups, spell checker, etc)
![[Pasted image 20231030185515.png]]

##### B.3) Replacement capacity

Some parameters of the application can be replaced with another equivalent 

>[!example]-
>Color selection can be shown by name, by hex value or by color palette
>
![[Pasted image 20231030185941.png]]





##### B.4) Customization capacity

Users and/or system can **customize** the interface regarding **design preferences** and/or **available options, based on the user's experience level**.![[Pasted image 20231030190214.png]]
![[Pasted image 20231030190220.png]]

### C) Robustness principles

Robustness involves main features required to reach the goals and the user perception of robustness. In order to achieve robustness, we need to take into account the following principles:
- C.1 Obserbability ^e2d1af
- C.2 Recoverability
- C.3 Response times
- C.4 Task advisability

##### C.1) Observability

^fd84b2

The system informs the user about its internal state through its representation in the UI.![[Pasted image 20231030190704.png]]

##### C.2) Recoverability

Recoverabilty refears to the capacity of reaching the initial goal after an error in the interaction. I applies the "*Proportional effort*" principle

>[!Proportional effort principle]
>Whether disallowing an action is hard to be done, then the action itself must also be difficult to be done

![[Pasted image 20231030191009.png]]
Delete a file: Hard to be undone

![[Pasted image 20231030191038.png]]
Rename a file: Easy to be undone

##### C.3) Response times

Delays that the system requires to evidence the state changes to the user. They should be as **short as possible**. If thet were not short enough, we must find a way to notify the user that his/her request is being processed ![[CPM FIRST EXAM#^fd84b2]]
![[Pasted image 20231030192143.png]]

##### C.4) Task advisability

It concerns how far does the system provides support for all the tasks the user wants to do, and the way the user understand them
![[Pasted image 20231030192420.png]]





### D) Accesibility

Human beings are **different** and we can also use technology under **different ciscumstances**. All the user interfaces should take all these differences into account so that they can be used on an equal footing. Accesibility is therefore another of the great pillars in ngood user interface design
![[Pasted image 20231030192801.png]]

##### Examples dissabilities / Circumstances

- People with **visual difficulties**: 
	- May have difficulty with font size
- **Elders**:
	- They may present difficulties in handling the mouse
	- They may have difficulty understanding processes or navigation
- **Anyone**:
	- You can access the same application from different devices (pc, mobile, tablet...)

**A good user interface must be prepared to be used in all these cases**. To achieve this, we can use come strategies:
- Keyboard navigation
	- Control the menu with keyboard
	- Forms and links usable through keyboard navigation
- Provide text for automatic screen readers
- Colors and fonts selection
	- Allow the user to choose high contrast colors
	- Allow the user to increase fonts
	- Do not use just colors as information source

>[!User-centered design]
Designing interactive systems implies **user-focused** designs. We must involve the user as far as possible, even participating in the designing team and observe the everyday work of user. It's a good practice to build prototypes, scenarios or models in order to allow users to evaluate the design sooner the best.




## THEORY PILLS LAB 3

####  Dialog (JDialog)

Generally used to get input data from the user and to show messages. They derive from another component and the cannot have menu bar. We can distinguish two main types:
- **Modal**: Users cannot interact with the rest of the application until the dialog is close (user can still interact with other applications)
- **Unmodal**: They allow the user to keep interaction with the application even having them opened.
![[Pasted image 20231103110226.png]]

Main features:
- Title should be "Application name: dialog name"
- We have to include mnemonics for every elements but the default button
	```Java
	this.getRootPane().setDefaultButton(btnNext)
```
and the cancel button.
- When we open a dialog, the focus must be on the component that the user is expected to use first.
- The tab order should respect the reading order of the user.

Command buttons on JDialogs:

- All the buttons whose effects affect the whole dialog must be placed in a row on the **bottom of the dialog**, and **aligned to the right**.
- If Help button was used, it must be the last on the right

Default button:
- Activated whenever the user presses Intro. Executes the actions linked to the button.
- An ***unsafe option*** should never be the default button.
- Default button **does not need to have the focus** when the user presses intro
- If the dialog has default button, it must be the first on the line

Cancel button:
- Activated with the Esc key. Fires the actions associated with the cancel button. 
- This behavior must be implemented manually, there's no way to determine which is the Cancel button.

In swing, there're several standard classes supporting dialogs:
- JOptionPane
- JColorChooser
- JFileChooser
All of them are **modal**

#### JOptionPane

It allows us to create several types of dialogs, specifying:
- Icons
- Title
- Text
- Buttons text
- Location in screen

Standard icons: *question*, *information*, *warning* y *error*

Main static methods:

- *showMessageDialog*
	- Shows a modal dialog with one only OK button
	- We can customize message, icon and title
	- Examples:
	
```Java
JOptionPane.showMessageDialog(this, "Message");
JOptionPane.showMessageDialog(this, "Title", JOptionPane.WARNING_MESSAGE);
```

- *showConfirmDialog*
	- Shows modal dialogs to ask for confirmation
	- Allows us to specify message, icon, title and combination of buttons
	- Examples:
```Java
JOptionPane.showContirmDialog(this, "Message");
JOptionPane.showConfirmDialog(this, "Message", "Title", JOptionPane.YES_NO_OPTION);
```

- *showInputDialog*
	- Modal dialog that allows users to send a String to the SYSTEM
	- It must be used carefully (data validation can be only done only after closing the dialog)
	- Examples:
```Java
JOptionPane.showInputDialog(this, "Message");
JOptionPane.showInputDialog(this, "Message", "Title", JOptionPane.PLAIN_MESSAGE);
```
- *showOptionDialog*

#### Spinner (JSpinner)

Allows to select a value within a range of possible option. The values change pressing the slide-buttons, or can be also introduced directly. We must configure the maximum, minimum and increment values. Those values can be changed at runtime

### Layouts

They determine the way the components are organized inside a container, specifying size and placement. We must use the one that suits better with needs of the application.
Steps:
- Create the container
- Determine the layout
- Add the components to the container

Types:
- **FlowLayout** (By default at JPanel and JScrollPane)
- BorderLayout (By default at JFrame and JDialog)
- CardLayout
- GridLayout
- BoxLayout
- GridBagLayout

#### FlowLayout

Simplest and default in every panel. Components are placed in one or more rows starting from the top of the panel. New rows will be created if necessary. If the size of the container is replaced, components will replace themselves. We can specify **alignment** and **space between components**
## USER CENTERED DESIGN

The user centered design is a **design approach** where the procces of design is driven by the information about the users that will use the product. Defined by the [ISO 13407](https://www.iso.org/obp/ui/#iso:std:iso:13407:ed-1:v1:en) and updated in the [ISO 9241-210:2010](https://www.iso.org/obp/ui/#iso:std:iso:13407:ed-1:v1:en). **Design** must be considered as a **proccess**.

![[Pasted image 20231030203242.png]]
500 series Bell Telephones

In software development ther're three main concepts that dives the proccess of **User Centered System Design**:
- The **conceptual model**: What the designer offers to the users.
- The **User Interface**: Is what the user see.
- The **Mental Model**: Is what the user understands from the User Interface

### User Centered Design Basics

**Iterative** processes: It's is not ONE process, but a bunch of them:
- 1. Specify the context of use
- 2. Specify requirements
- 3. Create design solutions
- 4. Evaluate designs

![[Pasted image 20231030203858.png]]

##### 1. Specify the Context of Use

The **characteristics of users**, tasks and organizational, technical and phisical **enviroment** define the **context** in which the system is used. We need to **understand** that. During this phase, we need to:
- Identify the people who will use the product
- Understand what they use it for
- know under what **conditions** they will use it

A Context-of-use should include:
- **The users and other stakeholder groups**: Identify the relevant groups of potential users
- **The characteristics of the users or groups of users**: We identify the more relevant characteristics of each group.
- **The goals and tasks of the users**: How often? How they do? How long? Interference with other tasks? Consequences for health and safety? Can special users do the task?
- **The enviroment(s) of the system**: 
	- Technical environment (hardware, bandwidth, software...)
	- Physical environment too (light and noise conditions, temperature, spatial layout, ergonomics...)
	- Social and cultural environment (work practice, organizational structure, attitudes...)

###### Personas-Scenario

This technique generates a series of documents that recopile the information extracted from the audience. The information about the needs of the users must be **based on real data** extracted form portential users. The models of persons created in this process must be **contextualized with scenarios or deescriptions** of specific use situations. They should represent the largest percentage possible of the audience.

>[!Example]-
>![[Pasted image 20231031142146.png]]
>In this case, we can see an example of a ficticious character named Jaime, with his correspondent scenario of use or our application

##### 2. Specify Requirements

Identify any business rerquirements or user goals that our prodct should met to be successful, taking into account the **context of use**. Then, we need to find an equilibrium between:
- Business viability
- Technological feasability
- User needs and desires
In order to do so, we can follow some steps:
- Identifty user and stakeholdes needs
- Context of use (GPS apps must be used outdoors)
- Ergonomics or accessibility requirements
- Usability requirements and objectives (usability satisfaction criteria)
- Derivations from organizational requirements
- Resolve conflicts (trade-offs) between user requirements

##### 3. Create Design Solutions

Done in steps, from rough concept to complete design.
- Generate tons of ideas
- Identify opportunities for design
- Test and refine your solutions
Activities:
- Designing **user tasks**, **user system interaction** and **user interface** inorder to meet user requirements.
- Making the **design solutions more concrete** 
- Alteraing design solutions in response to user-centered **evaluation and feedback**
- **Communicating** the design solutions.

##### 4. Evaluate designs

Is the equivalent to testing software. The sooner a problem is found, the easiest and cheaper it'll be to solve it. The User Centered evaluation methods includes two widely used approaches:
- **User based testing**
	- Ask the user to use the prototype and observe the way they use it
- **Inspection-based evaluation** using accessibility guidelines or requirements
	- Done by **experts**, it can complement user based tests (simple, quicker and less expensive).



## THEORY PILLS LAB 4

#### Scroll Pane (JScrollPane)

They're specialized containers that provides scroll bars. The user can shift the visibke part of the content of the window. We can also force the scroll bars to be visible ALWAYS or only when NECESSARY. We can use verticalScrollBarPolicy and horizontalScrollBarPolicy to change this, but they're generally only AS_NEEDED

### Keyboard operations

We must provide an alternative interaction method to the mouse in order to:
- Help users that are used to different environments
- Help handicapped users
- Prevent mouse failures

Good practices:
- Use of mnemonics
- Shortcuts
- Keyboard navigation and activation

#### Mnemonics

The underlined character present in titles, menu options, button text, etc... It evidences the way the user can active the command: (ALT) + (underlined character)

Rules:
- Avoid conflicts
- Choose the first character of the menu
- If the first character is being used, we must choose a prominent consonant
- If both come in to conflict, we must choose a prominent consonant

#### Shortcuts

They're keys that activates a menu option. They are a combination of the *Control* key and a character or a function key. They must be consistent with the usual shortcuts in the platform

#### Keyboard focus 

Also named "input focus", points out the active windows and/or the component that will be affected by the next keystroke. The first time a window is opened, the focus must point to the component that user will interact with first (Generally, the closer to the upper-left corner)

#### Keyboard navigation and activation

It allows us to move the focus along the components of the interface using the keyboard
- *Tab* -> Moves the focus to the next component
- *Shift-Tab* -> Moves the focus to the previous component
We must ensure that every option is available through the keyboard

## EVENT HANDLING

### Events

An operating system that supports GUI use events as a way to notify the occurrence of user inputs to the applications, and it's the application who decides what to do in each case. This events can be generated by the **user** or by the **system** itself.

In Java, whenever a user do an action, an **event is produced and propagated to the application by the OS**. Java creates an **object** of the specific class of that event, and then it's **sent** to a specific **method** called ***handler***. The event model in Java is **based on *delegation***. The objects in charge of handling an event is called ***listener***. Then, the elements of the **Java Event Model** are:
- ***Event sources*
- ***Event listener*
- ***Adapter classes*

>[!Event sources]-
>They're objects that detect and notify events to the listeners.

>[!Event classes]-
>When the event is generated, it will be **represented as an instance** of *EventObject* subclass
>![[Pasted image 20231031151842.png]]

>[!Event listener]-
>Called whenever the event they're associated is generated by the source the're registered to. They are instances of a class implementing ***listener interface***. (FocusListener, ActionListener, KeyListener...)

>[!Register]-
>Once we have the source and listener objects, they need to be linked in order to declare which listeners are managing each event
>
```Java
sourceObject.addEventListener(listenerObject)
```

#### Building the listener

Generally, the listener will require access to the main class that contains the source object. It can be done in two ways:
- Creating the listener as an **inner class of the main class**. An inner class is defined **inside the container class and has access to every member**.
- Create the listener as an **external class** and send a reference to the main class in the constructor.

##### Example 1

Next, an example of an implementation of a listener class as an **inner class** will be shown. it will be an *ActionListener*, and we must implements its only method, ***public void actionPerformed(ActionEvent e)***. This method will be called every time the source component generates the event.

```Java
public class mainWindow extends JFrame{

...
	private ProcessAction pA = null;
	private JButton btAzul = null;
...
	private void changePanelColor(){
		contentPane.setBackground(Color.blue);
	}

	class ProcessAction implements ActionListener{  // <- Listener
		public void actionPerformed(ActionEvent e){
			changePanelColor();
		}
	}

	private JButton getBtAzul(){
		if(btAzul == null){
			btAzul = new JButton();
			...
			btAzul.addActionListener(pA); // <- We need to link both objects 
			// Once linked, each time the event is produced, the listener will be called and a instance of ActionEvent will be passed as a parameter
		}
		return btAzul;
	}
...
	public MainWindow(){
		pA = new ProcessAction(); // <- Listener
		
	}
}
```


Also, a listener can be implemented inside the getter of a component, and it'll be exclusive of that component. As in the following example:

```Java
public class mainWindow extends JFrame{

...
	private JButton btAzul = null;
...
	private void changePanelColor(){
		contentPane.setBackground(Color.blue);
	}

	private JButton getBtAzul(){
		if(btAzul == null){
			btAzul = new JButton();
			...
			btAzul.addActionListener(new java.awt.event.ActionListener(){
				public void actionPerformed(java.awt.event.ActionEvent e){
					changePanelColor();
				}
			});
		// In this specific case, we can see that the listener is created inside the getter of the button. This listener will be exclusive of this button and cannot be shared with any other component.
		}
		return btAzul;
	}
...
	public MainWindow(){
		pA = new ProcessAction(); // <- Listener
		
	}
}
```

##### Example 2

The following example is about the implementation of an event, specifically a FocusEvent. In this example, the goal is to chck the lenght of the user inputs on an textField whenever it loses the focus.

![[Pasted image 20231031164748.png]]

It must implement the interface *FocusListener*, that contains the methods *focusLost* and *focusGained*


```Java
public class mainWindow extends JFrame{

...
	private ProcessFocus pF = null;
	private JTextField txDNI = null;
...
	private void checkLength(){
		... //whatever
	}

	class ProcessFocus implements FocusListener{  // <- Listener
		public void focusGained(FocusEvent e){} // <- If we won't use one of the methods, then we can just leave it empty
		public void focusLost(FocusEvent e){
			checkLength();
		}
	}

	private JTextField getTxDNI(){
		if(txDNI == null){
			txDNI = new JTextField();
			...
			txDNI.addFocusListener(pF); // <- We need to link both objects 
			// Once linked, each time the event is produced, the listener will be called and a instance of ActionEvent will be passed as a parameter
		}
		return txDNI;
	}
...
	public MainWindow(){
		pF = new ProcessFocus(); // <- Listener
		
	}
}
```


#### Adapters

This classes help developers to avoid the need of implementing every method inherited from *listener interfaces*. There's one adapter **for each listener interface with more than one method**: MouseAdapter, WindowAdapter...
They implement every method as an empty method. Then, we can overwrite those that we need. In the Example 2, it can be seen that *FocusListener* has two methods, when we only need one of them. For that purpose, we can extend the FocusAdapter class.

```Java
public class mainWindow extends JFrame{

...
	private ProcessFocus pF = null;
	private JTextField txDNI = null;
...
	private void checkLength(){
		... //whatever
	}

	class ProcessFocus extends FocusAdapter{  // <- Adapter
		// We're overwritting this method of FocusAdapter
		public void focusLost(FocusEvent e){
			checkLength();
		}
	}

	private JTextField getTxDNI(){
		if(txDNI == null){
			txDNI = new JTextField();
			...
			txDNI.addFocusListener(pF); // <- pF extends FocusAdapter, but FocusAdapter is still a FocusListener, because it implements it 
		}
		return txDNI;
	}
...
	public MainWindow(){
		pF = new ProcessFocus(); // <- Listener
		
	}
}
```


In the case that several components must share the same behavior for the same event, we can use only one listener that can be connected to both elements. We just create one listener and register it to both elements.

##### Example 3

This exapmle implements a MouseAdapter for a mouse event. We're required to paint and unpaint the borders of several buttons as the mose hover over them. Then, we'll use the methods *MouseEntered* and *MouseExited*.

```Java
public class MainWindow extends JFrame{

	...
	private ProcessBorder pB = null;
	...
	
	class ProcessBorder extends MouseAdapter{
		public void MouseExited(MouseEvent e){
			changeBorder(e, false);
		}
		public void MouseEntered(MouseEvent e){
			changeBorder(e, true);
		}
	}

	private void changeBorder(MouseEvent e, boolean b){
		JButton button = (JButton) e.getSource(); //<- The e.getSource returns the object that generated the event. We need to cast it to its correspondent component. Then, we need to pass the MouseEvent generated in order to know which button does the event belong to
		button.setBorderPainted(b);
	}

	private JButton getButton1() {
		if (button1 == null ){
			button1 = new JButton();
			button1.setBorderPainted(false);
			button1.addMouseListener(pB)
		}
		return button1;
	}
	
	private JButton getButton2() {
		if (button2 == null ){
			button2 = new JButton();
			button2.setBorderPainted(false);
			button2.addMouseListener(pB)
		}
		return button2;
	}

	public MainWindow(){
		pB = new ProccessBorder();
	}
}
```


#### Consume events

Sometimes, we need to stop an event based on its content. For that purpose, we can use the consume method. 

```Java
if(!Character.isDigit( e.getKeyChar() )){
	e.consume();
}
```

If the key pressed does not correspond to a digit, the event will be consume, so it won't be typed

#### Unregistering a listener

The process of removing a listener from an Object is called unregistering. 
If to add a listener to an object we use:
```Java
sourceObject.addActionListener(listener);
```
Then, in order to get rid of it, we can use:
```Java
sourceObject.removeActionListener(listener);
```

![[Pasted image 20231031172732.png]]
![[Pasted image 20231031172655.png]]
![[Pasted image 20231031172755.png]]



## THEORY PILLS LAB 5

### Menus

They show a set of options. They can be:
- Drop-down
- Submenu
- Context menu

#### Menu bars (JMenuBar)

At the upper side of a main window, contains menu titles that describe the contents of each menu. They're generally text, but the can contain graphics or both too. Mnemonics must be included to each title, and they should be formed by **simple words**.

#### Drop-down Menus

Shows whenever the user selects a menu item from the menu bar. They're all contained by menu bars

#### Submenus

Menus that the users open clicking or slipping  the mouse on a menu element. They also include **mnemonics** and **shortcuts**. **Second submenu levels should be avoided**.

#### Context Menus (JPopupMenu)

They're pop-up menus that provides menu elements that can be applied to the object or region pointed by the mouse. Mnemonics and shortcuts must be defined and consistent. We must ensure that every option available through the context menu are also accessible by means of a more visible alternative.

#### Menu Items (MenuItems)

They represent a command or option to be done. They must be **brief and take up just one line**. Mnemonics must be included and shortcuts must be offered at least on the most frequently used options. 
If the command requires **more information** to be executed, we must add "..." at the and, but we can't use it to mean that a secondary window will be shown.
If an option is not current available but might be available after some users actions, we must show it as **disabled**. Even if all the options are disabled, the menu **must be enabled** in order to allow the user to see the options. 
We use separators in order to let the user to understand and localize the different options. We can use a grid layout to show all the options in multiple columns if the number of items is too big.

#### Checkbox Menu Items

We use them to show non-exclusive options

#### Radio Button Menu Items

We use them to show exclusive options. Separators must be used in order to group the radio buttons. 
## THE HUMAN FACTOR

The differences between users requires special attention during the design of the user interfaces, we need to take into account the **human factor**. It's necessary to include the **widest** possible spectrum of users.
Some practices as having a font size bigger or equal 11, proportional interline spaces, avoid complicated fonts and don't write in capital letters are very recommended.

##### Colors

![[Pasted image 20231102104111.png]]

We've to take into account some rules when choosing colors for our interface, such as:
- Use only compatible color combinations
- Avoid red-green, blue-yellow, green-blue, red-blue
- Avoid bright colors in big areas of the screen
- **Use redundant codes** given that several diseases affect the visual system [Info](https://color.mediaandme.be/es)


### User Modeling

The user model is a **generalization** of an abstract representation of the information that is known about a certain user. It includes a description of the user's mental model, language, motor precision, expected reaction times, etc. Knowing the user model allows us to:
- Make the system adaptive
- Customize different aspects, based on preferences and needs of each user
- Implement or improve the accessibility of various environments, products or services as for example:
	- Expand the size of the font or buttons for older users
	- Simplify information
- Customize the sales catalog to the user's profile

#### Behavior classification

>[!Culture based models(≈ Local)]
>- Languages
>- Image processing
>- Color meaning
>- Reading direction

>[!Biology based models(≈ Universal)]
>- Typing speed
>- Movement precision
>- Learning speed


#### Culture based models

Analysis of *Personas*
Pros:
- Simplifies the design process by focusing on users rather marketing
- It makes easy to meet interaction requirements.
- Provides human face for designers
Cons:
- No way to determine how many users are represented by a given persona
- It's not possible to prove their validity
- They're not **scientific tools**

#### Biology based models

Attempts to model users based on their biological traits. It can **predict** certain aspects of their interaction.

#### *Human Processor Model*

**Cognitive** method to estimate the time it takes for a subject to perform a certain task. It's based on three subsystems:
- **Perceptual system**: Handles sensory stimuli from the outside world
- **Motor system**: Controls the action
- **Cognitive system**: Connects both of them

**Processor Features**:

- Each processor operates independently. Sometimes they can operate in parallel and in others sequentially.
- Based on clock cycles
- Performance varies from user to user and will often depend on the task at hand![[Pasted image 20231102151028.png]]
- Average reaction time: **240 ms**, but could range from 105 to 470 ms

**Perceptual System**

- Input output channels: The user receives information from a computer output and responds providing an input
- The entrance into the human being occurs through senses (view, ear, touch, smell and taste)
- Output is implemented through movement of the fingers, limbs, eyes, head and vocal system. Perceptual processor has two memories:![[Pasted image 20231102151516.png]]

**Cognitive System**

Human memory is important since it participates in all the acts of the person's interaction with the computer. Three types of memory:
- **Sensorial** memory:
	- One per **sense**
	- Continuously updated
	- Information received without paying attention
	- If it motivates more attention, goes to the short-term
	- Continuous and repeated stimulation leads to **habituation** (It should be avoid)

- **Short-term** memory:
	- It's the *work memory*
	- Features:
		- **Time and size limited**
		- High access speed
	 - STM stimulation techniques:
		 - *To Essay* (repeat an ID)
		 - *To Split up* or *Cut up* information
	Short-term memory also has some limitations:
	- Don't force the user to remember information from the previous screen
	- Provide elements that lighten the work of the SMT:
		- Redo and undo
		- Remember the last introduced data
		- Cut, copy and paste

- **Long-term** memory:
	- Features:
		- Unlimited capacity and life
		- **Slow access**
	- Main purpose: Recover the stored information
	- Simulation techniques for the LTM:
		- Recognition (You cannot remember a face but if you see it, you recognize it)
	Long-term memory also has some limitations. We can follow the strategy of lean on the recognition:
	- Print shortcuts close to the options to execute
	- Use lists and menus to select instead of forcing the user to write
	- Use tooltips and context help.
	- Possibility of returning to the initial default state

![[Pasted image 20231102154445.png]]

### Modeling techniques

They provide ***objective*** estimates on the user interaction for evaluation:
- **Fitts Law
- **Hicks Law
- **The Power Law of Practice**
- **GOMS**

#### Fitts Law

Related to human movement, applied in ergonomics, interaction design and psychomotor skills 

>[!Note]
>"The time it takes to hit a target with a quick movement is a function of the size of the target and the distance to travel to it." 
>~ Paul Fitts in the 50's

It predicts the time required to perform a pointing movement with the hand or arm:

>[!Fitts' Law equation]
>T = Im log2(D/A + 1)
>- T: Average time to do the movement
>- Im: Empirical constant 100 [70 ~ 120] Msec
>- D: Distance from the initial point to the target
>- A: Target's width / height (same movement direction

Fitts' Law is used to predict the time required to drag objects, click, etc. When we expect the user to click on an interaction element, the width of the element and its position relative to the starting point of the cursor matter. [About](http://simonwallner.at/ext/fitts/)

![[Pasted image 20231102163347.png]]


Size matters. We need to consider the movement direction. The width or height will be determined by the direction of the movement (vertical movement -> height++, horizontal movement -> width++).
Same applies to the menus. We must ensure that the submenu options **appear as close as possible** to the initial position of the mouse.

![[Pasted image 20231102170333.png]]

#### Hick's Law

*Principle of uncertainity*. How much time do we need to make a decision?

>[!Hick's Law equation]
>**T = Ic H**
>**H = log2( n+1 )**
>- Ic = 150[0 ~ 157] Msec/bit
>- H = amount of information needed to make decisions (measured in bits)
>- n = number of choices

Hick's law can be used to estimate the time we need to select a menu item

#### Law of Practice

*The Power Law of Practice:*
- If the same action is repeated over time, performance tends to improve
- If an operation takes **T1** seconds to be done first time, it'll need **Tn** the **nth** attempt

>[!Time needed for the nth attempt]
>Tn = T1 n^-a
>- Where a = 0.4[0.2 ~0.6]
	
- We use it to tell between novice and expert users

#### GOMS

GOMS (Goals, Operators, Methods and Selection Rules) (AKA *The Keystroke Model*)

- Prediction model with a 20% precission
- **The model assumes that...**
	- Users know how to perform tasks
	- Users do not make mistakes
	- User interaction parameters are known
	- The response time is known

Estimates the time required to perform a task on a specific interface. Rapid evaluation of design alternatives.
- Examines the method used to perform a task based on a set of basic operators
	
	- **K** (Key stroking): Press a key on the keyboard, mouse, etc
		**Tk ≈ 0.2 seconds**
		
	- **H** (Homing): Move hands for one device to another
		**Th ≈ 0.4 seconds**
	
	- **P** (Pointing): Aim at an area on the screen
		**Tp  ≈ Tpos = 0.1 log2( 2D/S + 1 ) seconds (Fitts' Law)**
		Whenever D or S are **unknown**, we use:
			**Tp ≈ 1.1 seconds**
			
	- **M** (Mental): Decide what to do next
		**Tm ≈1.35 seconds or Tm = 0.15 log2( n + 1 )**
		
	- **D** (Drawing): Use the mouse to draw gestures
		**Td ≈ 0.9nd + 0.16ld**
		Where:
		- nd = Number of segments
		- ld = Total length of the segments
		
	- **R** (System Response): Time used by the software to respond
		It depends on the algorithms, connection to the network, etc. It is recommended:
		**Tr ≈ 0.15 seconds**
		
- Determine the time required to complete the operation of each group of operators
- TK = Time required to press keys

#### Summary

- Pros:
	- Framework to evaluate design alternatives
	- High accuracy (error <= 20%)
	- Scientific method
	
- Cons:
	- Average times are used instead of the specifics of the users
	- Special users are not considered during the modeling
