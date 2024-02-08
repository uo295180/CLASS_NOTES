## DESIGN TECHNIQUES

### Design Phases

Once we have determined the requirements and modeled the target audience, the following stages are considered in the stage of creating a design solution:
- Create a **Wireframe**
- Draft the **mockup**
- Develop a **prototype**

#### Wireframe

It's a two-dimensional illustration of the application interface that focuses on:
- **Space allocation** and **prioritization of content**.
- Representation of **available functionalities**
- Desired **behaviors**

Wireframes **lack** typographic style, color or graphic applications. Their main objective is to represent **functionality, behavior** and **hierarchy of content**. 
Good tool for the development team to focus on outlining the fundamentals of the application and deciding on its structure. Their goals are:
- Determine the expected functionality in the interface
- Determine the location of each element of the user interface
- Show connections between the different views of the application

#### Mockup

Complete graphic composition that uses the wireframe as a template. It's the representation of the appearance of the product including the visual details (color palettes, typography, icons...). Their goals are:
- Have a **good idea of what the final product will look like** and a rough idea of **how it will work**.
- Used to **demonstrate and test a design** to the client.
- Adjustments and improvements can still be made with relative little effort
- A **style guide** can be derived from it.
- Mockups **don't work**, they're **static**.

#### Prototype

Is an **operational** version of a solution. Easily expandable and modifiable model of an application. Usually, a prototype includes:
- Navigation systems
- Color palette
- Iconography
- Description of the interaction
- **User experience**
The creation of the prototype supports the **evaluation of the interaction**. It's goals are several:
- Perform usability tests with real users
- Get interaction data to refine your application
- **Avoiding problems and saving costs** before the product launch
- Savings in development hours (/fewer versions of the application required)

We can use user-testing whatever we want, but we should integrate it in **each of the design stages**. They will help to **validate design decisions** and we can obtain reports and metrics from them.

#### Card Sorting

It's a user experience design technique that's used to **design, organize, rank and evaluate** the information structure of an application and its contents. The goal is to **find a logical and simple way to order** the elements of an application. We aim to predict where the user will expect to have things. It consists on providing users with cards with different concepts and **observing their behavior** and the **classification** they consider.
Its goals are several:
- Highlight which content is **most important** to the user
- Provides information about the thought process of the user during navigation
- Helps to tag **categories** and **navigation**
- Allows to answer the **doubts** of the designers
- Very useful in applications that may require many categories and subcategories.

#### Standards and Style Guides

GUI design is supported in *principles and rules*.

**Principles**:
- Based in high abstraction level ideas and with a very open approach
- Usually, highly ethereal

**Rules**:
- More specific and easy to apply and understood
- They can be classified into **Standards** (Mandatory rules) and **Style guides** (Suggested practices)

##### Standards

Is a requirement, rule or recommendation **based on tested principles or in the experience**. They mean an agreement of an **expert commission**. They aim to make tasks easier defining features of objects and systems that are usually used. They can cover aspects in software or hardware. Some committees are:
- **ISO** (Internationals Organization for Standardization)
- **ANSI** (American National Standards Institute)
- **IEEE** (Institute of Electrical and Electronics)
- **CEN** (Comité Européen de Normalisation)
- **W3C** (World Wide Web Consortium)

##### Style guides

A good style guide must be efficiently integrable in the development process, offering criteria and guiding in every aspect related to the interface design. They determine when **widgets** should be used, how they should be organized and the interaction techniques.
They assure a better usability by enforcing consistency. Style guides can be:
- **Commercial**, designed by software development companies
- **Corporative**, designed for internal use

###### Java Style Guide

The guide "*Java Look and Feel Design Guidelines*" was developed by *Sun micro-systems*. 

## INTERNATIONALIZATION

The goal is to reach new international markets with our product. Users can be different in many ways, like language, cultural aspects, formats, symbols....

#### Internationalization (i18n)

*Design and development of a product, application or document that allows an easy localization for the **different cultures, regions or languages** of the targeted audiences*.
*Process of designing a software application so that it can be **adapted** to **various languages and regions** without engineering changes*.
- An internationalized application has **no elements** that depends on the language or cultural context **in the source code**.
- Textual elements are not **hardcoded** and will be **loaded dynamically**.
##### Benefits

If we consider internationalization during the design instead of doing it when we have the product finished, we can save time and money bc:
- New localized versions will be created easily and quickly.
- The same application can be distributed to the hole world (No need to create a version for each culture)
- It **does not require recompilation**.
- More efficient resource management
- Source maintenance and new localisations are cheaper (Only one version)
- Market is bigger

#### Localization (l10n)

Is the process of adapting internationalized software for a specific region or language by adding locale-specific components and translating text. Each country is a unique localization, but one language can be spoken in more than one country, so we need to take into account their differences (like currency).

##### Specific elements

We must consider:
- Text messages that must be translated
- Calendars, date formats, time format, etc
- Numbers and currency formats
- Measure units
- Icons, colors, etc
- Titles and forms of address
- Addresses
- In some cultures, they write from right to left. 

##### Furthermore

When changing localization we must consider:

- A word could be enlarged or shorted
- It could be necessary to swap variables in compound messages
- The order of the navigation can vary. *Ordering* is important

Different cultures can have different prioritization criteria for their interests. Some content could be misunderstood or offensive. Different legal restrictions/aspects
#### Internationalization process

The goal is to decouple the **source code** from the **data**, defining source code as the part that implements the domain logic and won't change in different countries and data as all the elements that will change depending on the localization. Then, we will have:
- **A unique block of code**, the source code that will always be the same
- **Several resource bundles**, one per localization

![[Pasted image 20231210113903.png]]

#### Internationalization in Java

We will consider two types of data:

- **Dates, numbers, currency, etc**: They will be formatted by means of Java code according the localization
- **Texts**: They will be retrieved from a resource bundle file.

>[!Main classes involved in internationalization (java.util.*)]-
>- Locale
>- ResourceBundle
>- NumberFormat
>- DateFormat

- **Locale Class**:
	Identifies a specific language and country
	
-  **ResourceBundle Class**
	Contains localization specific objects
	
- **NumberFormat Class**
	It allows to format numbers based on the localization
	
- **DateFormat Class**
	It allow to format dates and timestamps based on the localization

##### Example 1 (Saludo.java)

We want to internationalize the following class to show messages in Spanish, English and French:

```java
public class Saludo{
	public static void main(String[] args){
		Systen.out.println("Hola a todos");
		Systen.out.println("Escuela de Ingeniería Informática");
		Systen.out.println("Universidad de Oviedo");
	}
}
```

The steps to follow in order to achieve the correct internationalization are:
- Identify the elements to be localized (In this example, the messages)
- Create the resource bundles (files).
	This are text files, one for each localization we need, and they must have an specific name **filename**_es.properties 
	
	![[Pasted image 20231210115632.png]]

- Adapt the class to select the corresponding file according to the localization specified in the system

```Java
Locale localization = Locale.getDefault(Locale.Category.FORMAT); // Grab the default localization
localization = new Locale("es"); // Determining an specific localization

ResourceBundle messages = ResourceBundle.getBundle("Textos", localization); // Loading the properties file corresponding to the specified localization
System.out.println(mensajes.getString("texto1")); // Extracting each string looking for them using the key provided in the properties file
System.out.println(mensajes.getString("texto2"));
System.out.println(mensajes.getString("texto3"));
```

Finished class:
```Java
import java util.*;

public class Saludo2 {
	public static void main(String[] args) {
		
		Locale localization = Locale,getDefault(Locale.Category.FORMAT);
		ResourceBundle messages = ResourceBundle.getBundle("Textos", localization)
		
		System.out.println(mensajes.getString("texto1")); 
		System.out.println(mensajes.getString("texto2"));
		System.out.println(mensajes.getString("texto3"));
	}
}
```

Now, if we want to include a new localization, the only thing we need to do is create a new properties file.

##### Resource files example:

![[Pasted image 20231210121142.png]]

##### Example 2 (FechaHoraNumero.java)

```Java
import java.util.*;
import java.text.*;


public class FechaHoraNumero{
	public static void main(String [] args){
		Locale localization = Locale.getDefault(Locale.Category.FORMAT);
		Date fechaHora = new Date();
		DateFormat formatoFecha = DateFormat.getDateInstance(DateFormat.LONG,localization);
		DateFormat formatoHora = DateFormat.getTimeInstance(DateFormat.LONG,localization)
		System.out.println(formatoFecha.format (fechaHora));
		System.out.println(formatoHora.format (fechaHora));
		System.out.println(NumberFormat.getNumberInstance ().format(123456.78));
	}
}
```
## THEORY PILLS LAB 9

### Lists (JList)

Used to show a set of textual and/or graphical items. Items must be capitalized and ordered. We can use different selection modes:
- Simple item
- Simple range
- Multiple ranges
 ![[Pasted image 20231211134641.png]]

>[!Properties]-
>- ***selectionMode***(SINGLE_SELECTION, SINGLE_INTERVAL_SELECTION, MULTIPLE_INTERVAL_SELECTION)

>[!Methods]-
>- ***getSelectedValue***
>- ***getSelectedIndex***
>- ***getSelectedValues***
>- ***getSelectedIndexes***
>- ***getModel***

### Sliders (JSlider)

Allows us to select a **numeric number** within a **continuous or discontinuous** range of values. Pointer position points to the current value. If the *slider* represents a continuous or a huge number of discrete values, be careful, the selected value must be exact (we can use a text field to show the current value).

>[!Example]-
>- ***txVolumen.setText(Integer.toString(slVolumen.getValue()))***;

### BorderLayout

Uses 5 areas to place elements: North, South, East, West and Center, with the following properties:

- North and South modifies their width if the frame is resized, but they keep the height fixed.
- East and West modifies their height if the frame is resized, but they keep the width fixed.
- Center adapts to the resultant space available. 

The position of the components is given by the property *constraints*. 

>[!Properties]-
>- ***hgap***: horizontal distance
>- ***vgap***: vertical distance

###  JFileChooser

It's a file selection dialog. It only manages the selection of the file. The application must face with its processing. We can use it as:
- ***showDialog***
- ***showOpenDialog***
- ***showSaveDialog***
If we enable the ***multiSelectionEnabled*** property we'll be able to select several files. For example:

```Java
private JFileChooser selectorFicheros = new JFileChooser();
....
if(selectorFicheros.showopenDialog(this) == selectorFicheros.APROVE_OOPTION)
	{
		txtOpcion.setText("open selected");
		txtFichero.setText(selectorFicheros.getSelectedFile().getName());
	}
	else
		txtOpcion.setText("cancel selected");
```

## THEORY PILLS LAB 11

### Tabbed Pane (JTabbedPane)

It's a container that can contain several components sharing the same space. The user will select what component he wants to see by selecting their tab. Tabs usually contains text, but they can also contain images.
Tabs ara located by default at the top, but they can be located anywhere(***tabPlacement***). If they don't fit in a single row, a new one will be created. Tabs **must have mnemonics**. Used when many information must be shown in a small space.

>[!Methods]
>- ***addTab*** // Adds a tab to the pane
>- ***getSelectedIndex*** // Returns the index of the currently selected tab.
>- ***getSelectedComponent*** // returns the component currently selected inside the pane
>- ***setToolTipTextAt* (int, String)** // Links a tooltip to the tab indexed by “int”.
>- ***setIconAt* (int, Icon)** // Adds an icon to he tab indexed by “int”
>- ***setTitleAt* (int, String)** // Adds a title to the tab indexed by “int”
>- ***setEnabledAt* (int, boolean)** // Enables or disables the tab.


### CardLayout

It shows just one of many components contained in the container. Components fill all the available space in the container. They're very useful when we need panels that modify their content in runtime.

>[!Methods]
>- ***first*()**
>- ***last*()**
>- ***next*()**
>- ***previous*()**
>- ***show*()**
## USER SUPPORT

The documentation of a product is part of its user interface, therefore, it must be considered during the design of usability tests. Documentation includes:
- Installation information
- Online help
- Messages
- Tutorials
- Any other product support

#### Basic documentation

- **Quick reference guide**
	Reminder of the most common actions and tools the user is already used to

- **Online help**
	Used whenever the user finds a problem while doing a task

- **Manual**
	Complete and detailed guide about a tool

- **Tutorial**
	Specially useful for new users. Provides step by step instructions about the use of the tool

#### *Help support* features

- **Availability**
	Help support must be available from every point of interaction with the system without having to leave the application

- **Precision and detail**
	Help support must correspond with the current version of the product. It must cover the **whole system**

- **Consistency**
	Every section of *Help* must be consistent in terms of contents, terminology and style

- **Robustness**
	We must provide a good user support, **even when the application is not working fine**

- **Flexibility**
	Sometimes it's **rigid**: Same message is shown independently of the user experience.
	We must allow 

- **Not obstructive**
	It must **never determine** the normal use of the application

#### Online help

Online help design must consider:

- Application audience
- Topics or epigraphs to be covered
- Topics contents
- Structure:
	- Cross references
	- Terms definition
- Context sensitive help

##### Application audience

The target users determine the information that must be shown in the help support, and the way it must be presented

- Novice users and application novice users need help support to learn tasks and term definitions
- Intermediate users will use help to remind orders and functions
- Expert users help support only for syntax aspects, accelerators or shortcuts

#### Help structure

In this point the **hierarchical structure**(table of contents and index), the **sequential navigation**, the **cross-references** and the **search** topics will be covered.

##### Hierarchical structure - Table of contents

It provides a list of every available topic
![[Pasted image 20231211102145.png]]

##### Hierarchical structure - Index

It must be alphabetically ordered
![[Pasted image 20231211102217.png]]

##### Sequential navigation

It provides a vision of the **functionalities** of the system. Useful for **novice users**.
![[Pasted image 20231211102330.png]]

##### Cross references

It includes hypertext with links to different pages, making easier to the user to access specific information quickly
![[Pasted image 20231211102548.png]]

##### Search

![[Pasted image 20231211102621.png]]

#### Text organization

- **Language**
	Clear and concise

- **Extension**
	Not excessive. Reading speed is 30% slower on the screen that on paper. Short paragraphs 

- **White spaces**
	They're critical for text readability

- **Text highlighting**
	Using different fonts, sizes, colors, etc to highlight concepts

- **Graphics**
	Useful, they allow an effective transmission information

- **Consistent design**
	Same colors in similar tiles, same fonts, etc


### JavaHelp

*JavaHelp* are Java extensions that supports the online help development. They're platform independent. Their windows are configured by means of **XML** files, whether their help text files must be written in **HTML**

#### Basic Features

- Help viewer
	- Contents panel
	- Navigation panel
- Different views of the information
	- Table of contents
	- Index
	- Search

#### Tools

- **hsviewer**:  It's in charge of rendering *HelpSet* files. Can be invoked from the command line or from windows.
- **jhindexer**: Command line application that creates the search database
- **jhsearch**: Command line application that searches in the database created with jhindexer

#### Libraries

- **jh.jar**: Standard library that includes everything needed by the help viewer and browsers
- **jhbasic.jar**: Subset of the previous one that do not support searches
- **jhtools.jar**: Includes the tools for building and searching in the database
- **jhall.jar**: All JavaHelp classes
