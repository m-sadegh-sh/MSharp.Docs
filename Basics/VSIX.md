# M# Visual Studio Extensions

(todo: intro)

(todo: for each single feature in this extension, add a section here with screenshots, etc. Also provide a CLI alternative tip for doing the same thing in CMD)

## VS Ext: MSharp.AddNew

MSharp.AddNew VSIX provides a set of functionality and project template wizards to make projects from scratch and create M# project items easily. You can create 3 different M# project types (**M# ASP.NET Core - MVC**, **M# ASP.NET Core - Microservice** and **M# Class Library**) using this extension.

![alt text](images/NewProjectTemplates.png "New Project Templates")

## ![Image](images/MSharp.png) ASP.NET Core - MVC Project

---

Using **_M# MVC Project Template Wizard_** you can create a standard M# project from scratch. Each M# ASP.NET MVC Application should consist of at least 4 different projects.

- #Model _(Standard .Net Core 2.1)_
- #UI _(Standard .Net Core 2.1)_
- Domain _(Standard .Net Core 2.1)_
- Website _(Standard ASP.Net Core App 2.1)_
- _[Docker-compose]_ _(Docker Container)_

Developers should specify the _Name_, _Location_ and _Solution name_ of new project and hit the **OK** button. Then the project wizard popup window gets custom **M#** project options from user in the **M# MVC Project Wizard** window.

![alt text](images/NewMSharpMVCProjectWizard.png "M# MVC Project Wizard")

In **M# MVC Project Wizard** window developers should specify a **M# Project Name** and choose a **Database Type** provider, such as _Sql Server_, _MySQL_, _PostgreSQL_, _Sqlite_ as the Database Management System for new M# Application. Developers should also specify related **Connections String** according to selected **Database Type**.

![alt text](images/NewMSharpMVCProjectWizard_DB.png "M# MVC Project Wizard DB Select")

Then the M# project wizard tries to download a fresh new copy of **M# MVC Project** template from web server.

![alt text](images/DownloadProgressWindow.png "Downloading Window")

After the template has downloaded successfully, **Initialize.bat** of the downloaded package runs automatically. It initializes the M# solution by updating projects references and all required website packages.

![alt text](images/SolutionInitialization.png "Downloading Window")

## ![Image](images/MSharp.png) ASP.NET Core - MVC Microservice Project

---

Using **_M# ASP.NET Core MVC Microservice Project_** you can create a standard M# Microservice project from scratch. Each M# ASP.NET Microservice Application should consist of at least 4 different projects.

- #Model _(Standard .Net Core 2.1)_
- #UI _(Standard .Net Core 2.1)_
- Domain _(Standard .Net Core 2.1)_
- Website _(Standard ASP.Net Core App 2.1)_

Developers should specify the _Name_, _Location_ and _Solution name_ of new project and hit the **OK** button. A project wizard then gets custom **M# Microservice** project options from the user in the **M# Microservice Project Wizard** window.

![alt text](images/NewMSharpMiscroserviceProjectWizard.png "M# Microservice Project Wizard")

In **M# Microservice Project Wizard** window developers should specify a **M# Microservice Project Name** and choose a **Database Type** provider such as _Sql Server_, _MySQL_, _PostgreSQL_, _Sqlite_ as Database Management System for new M# Microservice Application. Developers should also specify related **Connections String** according to selected **Database Type**.

![alt text](images/NewMSharpMicroserviceProjectWizard_DB.png "M# MVC Project Wizard DB Select")

Then M# project wizard tries to download a fresh new copy of **M# MVC Microservice Project** template from web server.

![alt text](images/DownloadProgressWindow.png "Downloading Window")

## ![Image](images/MSharp.png) Class Library Template

---

We have produced a **Custom Project Sub Type** called the "M# Class Library Template", which developers can use as a standard class library in their .NET framework projects.

![Image](images/NewMSharpClassLibraryTemplate.png)

## ![Image](images/MSharp.png) New Entity Project Item

![Image](images/NewItemEntity.PNG)

You can create a new Entity class from the simple class template by selecting the M# Entity item from *Add new Item* panel.

> You can also can create new Entity or SubType< Entity > classes by selecting the context menu item in solution explorer over the M# Model project or project folder. (You can read more about this item later in this document)
![Image](images/AddNewEntity.PNG)

## Solution Explorer Context Menu Commands

### Build All

-=***=- Build all is a useful M# build task. You can use by it by selecting the first context menu item of the solution node in the __Solution Explorer__ window.

![Image](images/BuildAllMenuItem.PNG)

### Run Fast

-=***=- Compiling, building and running every project is a time-consuming task. In the __Website__ node context menu there is an item called __Run Fast__ which you can use to run your website project without needing solution builds.

![Image](images/RunFastMenuItem.PNG)

## Generate Project Items

Depending on the type of project you are working on, you can create/add custom project requirements using the M# context menu under solution explorer node.

## Create a New Entity

In each M# project, the first thing a developer needs to do is build a concrete business domain model. This consists of entities often referred to as business objects. To do this, select a node (Project root node/Folder) from the solution explorer tree in the **#Model** project. Right click on it and choose the **"Add Entity ..."** item from the path "Add > M# > Add Entity ...".

![Image](images/AddNewEntity.PNG)

M# then shows a window where you can select an _Entity/**Type Name**_ with an optional **Base Type**, to generate a plain **M# Entity** class, or a generic **M# Entity SubType** class under selected node.

![Image](images/CreateNewEntityWindow.png)

If you only specify a **Type Name**,  M# creates a plain Entity type class. If you select a **Base Type**, M# will generate an Entity **SubType<_Base Type_>** class depending on selected item.

> Note : Only compiled Entity Types are available to select as the Base Type in all Create pages.
> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md#user-content-MSharpexe-addtype-nametypename-basebasetypename-foldercontainerfolder) :
>
> MSharp.exe /add:type /name:"Person" [/base:"Administrator"][/folder:"containerfolder"]
>
> - _Person is a sample entity name_
> - _Administrator is a sample entity base type_ (optional)
> - _ContainerFolder is a sample folder_ (optional)

## Create a CRUD

![Image](images/CreateCRUD.PNG)
![Image](images/CreateCRUDWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md) :
>
> MSharp.exe /add:Crud /page:"Admin.cs" /type:"ContentBlock" [/menu:"MainMenu"]
>
> - _Admin.cs is a sample page name_
> - _ContentBlock is a sample entity base type_
> - _MainMenu is a sample menu module name_ (optional)

## Create Partial Class

In many cases, you may want to have partial classes in the Domain project, in order to separate your concern into two partial files. To do this, go to the Solution explorer window and select *Create Partial Class ...* from the context menu of entity classes. Then a new partial file will be created in the Domain\Logic folder.

![Image](images/CreatePartialClass.PNG)

## Create a Form

![Image](images/AddFormMenu.PNG)
![Image](images/AddFormWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md#user-content-MSharpexe-addform-onentitytypename-namemyformname-foldercontainerfolder) :
>
> MSharp.exe /add:form /on:"EntityTypeName" /name:"MyFormName" [/folder:"ContainerFolder"]
>
> - _EntityTypeName is a sample entity name_
> - _MyFormName is a sample form module name_
> - _ContainerFolder is a sample folder_ (optional)

## Create a List

![Image](images/AddListMenu.PNG)
![Image](images/AddListWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md#user-content-MSharpexe-addlist-onentitytypename-namemyformname-foldercontainerfolder) :
>
> MSharp.exe /add:list /on:"EntityTypeName" /name:"MyListName" [/folder:"ContainerFolder"]
>
> - _EntityTypeName is a sample entity name_
> - _MyListName is a sample list module name_
> - _ContainerFolder is sample folder_ (optional)

## Create a View

![Image](images/AddViewMenu.PNG)
![Image](images/AddViewWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md#user-content-MSharpexe-addview-onentitytypename-namemyformname-foldercontainerfolder) :
>
> MSharp.exe /add:view /on:"EntityTypeName" /name:"MyViewName" [/folder:"ContainerFolder"]
>
> - _EntityTypeName is a sample entity name_
> - _MyViewName is a sample view module name_
> - _ContainerFolder is a sample folder_ (optional)

## Create a Menu

![Image](images/AddMenuMenu.PNG)
![Image](images/AddMenuWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md) :
>
> MSharp.exe /add:menu /name:"MyMenuName" [/folder:"ContainerFolder"]
>
> - _MyMenuName is a sample menu module name_
> - _ContainerFolder is a sample folder_ (optional)

## Create a Generic Module

![Image](images/AddGenericModuleMenu.PNG)
![Image](images/AddGenericModuleWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md) :
>
> /add:Custom /name:MyCustomModule /folder:"C:\..\MSharp.Mvc\M#\UI\Modules"
>
> - _MyCustomModule is a sample generic module name_
> - _C:\..\MSharp.Mvc\M#\UI\Modules is a sample folder path that module should create there_ (optional)

## Create a Root Page

![Image](images/AddPageMenu.PNG)
![Image](images/AddPageWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md) :
>
> MSharp.exe /add:page /name:"PageName" [/parent:"FullPathToParentFolderOrFile"]
>
> - _PageName isa  sample page or sub-page module name_
> - _FullPathToParentFolderOrFile is a sample folder or Page Module file name_

## Create a Sub-Page

![Image](images/AddSubPageMenu.PNG)
![Image](images/AddSubPageWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md) :
>
> MSharp.exe /add:Page /name:MySubAdmin /parent:"C:\...\MSharp.Mvc73\MSharp.Mvc\M#\UI\Pages\Admin.cs"
>
> - _MySubAdmin is a sample Sub Page name_
> - _C:\..\MSharp.Mvc73\MSharp.Mvc\M#\UI\Pages\Admin.cs is sample Parent Page full path_

## Create CRUD by Page

![Image](images/PageCreateCRUDMenu.PNG)
![Image](images/PageCreateCRUDWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md) :
>
> MSharp.exe /add:Crud /page:"Admin.cs" /type:"Administrator" [/menu:"AdminSettingsMenu"]
>
> - _Admin.cs is a sample page name_
> - _Admin.cs is a sample page name_
> - _Administrator is a sample entity base type_
> - _AdminSettingsMenu is a sample menu module name_ (optional)

## Create an API Proxy

![Image](images/GenerateApiProxyMenu.PNG)
![Image](images/GenerateApiProxyWindow.PNG)

> [![Image](images/CLI.png "M# Command Line Interface")CLI Command](CLI.md):
>
> MSharp.exe /add:type /name:"Person" [/base:"Administrator"][/folder:"containerfolder"]
>
> - _Person is a sample entity name_
> - _Administrator is a sample entity base type_
> - _ContainerFolder is a sample folder_

## VS Ext: MSharp.Colorize

![Image](images/MSharp.png) The **MSharp.Colorize** extension gives all M# Projects (MVC, MVC Microservice and Class Library) a specific UI layout in solution explorer window. In "M# ASP.NET - MVC" and "M# ASP.NET - MVC Microservice" projects, the Model and UI projects are shown as a simple custom M# purple icon (see below). In "M# Class Library", the project root has this icon.
![Image](images/MSharpMVCSolutionExplorer.PNG)

Depending on a C# class file's contents and it's base class in the #Model and #UI projects, its icon will be as follows:

- ![Image](images/CsType.png) : Plain **C#** files

- ![Image](images/EntityType.png) : M# **Entity** Type and Entity **SubType< _base_ >**

- ![Image](images/FormModule.png) : M# **Form Module**

- ![Image](images/ListModule.png) : M# **List Module**

- ![Image](images/MenuModule.png) : M# **Menu Type** and **Menu Module**

- ![Image](images/ViewModule.png) : M# **View Module**

- ![Image](images/RootPage.png) : M# **Root Page** and **SubPage**

- ![Image](images/GenericModule.png) : M# **Generic Module**

  > These icons are shown in the top right corner M# class modules in code editor window. For example, an M# Entity file it will look like this:

  ![Image](images/EntityTextEditorSample.PNG)

## Vs Ext: Geeks.StylishCode

__Geeks Stylish Code__ has been developed specially to decorate C# source code with colour and text styles just like CSS rules.
You can make all class members coloured by decorating them with special Stylish code attributes : _MethodColorAttribute_ and _MemberStyleAttribute_

## M# Code Highlighting

MSharp.Colorize VSIX provides attribute classes to apply colouring rules to M# methods, so developers can work better with M# code.

### MethodColorAttribute, MethodStyleAttribute classes

MSharp.Colorize VSIX provides a set of Classifiers to highlight M# code. The M# framework team have used this attribute class to decorate their methods with some styling features like color.

Using "MSharp.Colorize VSIX code highlighter" is very simple. To colour a method you should create a class with the name "MethodColorAttribute" inheriting from the Attribute class, and a constructor with at least one string parameter in your project, like this :

```C#
    public class MethodColorAttribute : Attribute
    {
        public MethodColorAttribute(string colorHexString/*like: "#8fdd24" */)
        {

        }
    }
```

In this case you can decorate all your methods with this newly created attribute like this :

```C#
        [MethodColor("#8fdd24")]
        public StringProperty String(string displayName, int maxCapacity = 200){
          // Code
        }
```

Whenever developers use your decorated method, they will see the method name coloured like this :

![Colorize_SampleCode1](images/Colorize_SampleCode1.PNG)

Depending on the current color theme of Visual Studio and the background color of the code editor window, the specified color can vary. Your decorated method will be displayed in the specified color if the colour of the code editor background is dark (as in the previous screenshot). Otherwise, the decorated method will be displayed in the opposite colour.

![Colorize_SampleCode2](images/Colorize_SampleCode2.PNG)

MethodColorAttribute class constructor can also be implemented with a second string parameter. In this case, the first parameter is the specified method color for the dark theme and second is the specified method color for the light theme.

> You can test live colouring functionalities by implementing a **MethodColorAttribute** class in your project, and then decorating a method with this attribute. Colour changes for the decorated method will reflected in real time.

## In Dark Theme

![Image](images/Colorize_SampleCode4.PNG)

## In Light Theme

![Image](images/Colorize_SampleCode3.PNG)

> Note : The background color of the M# code editor windows are modified to dark brown in **Dark Theme** and light blue in **Light Theme**.

## _MemberStyle[Attribute]_

There is an attribute in Geeks.StylishCode that does more than simply colour code called _MemberStyleAttribute_. As you know we apply attributes without using the __attribute__ postfix, we can add the _MemberStyle_ attribute instead of __MethodColor__. 

![Image](images/StylishCode_ForeColor.PNG)

Using _MemberStyle_ instead of _MethodColor_ has many benefits :

  * _MemberStyle_ works just like _MethodColor_ with one or two simple string parameters (the first for for colour in Dark theme, and the second for color in the Light theme).
  * _MemberStyle_ can be used for styling any part of the C# code. For instance, Classes, Properties, Methods, Events and etc.
  * _MemberStyle_ now supports 14 options to decorate the C# code :
  1. __ForeColor__ (*): (_[string property] hex web color [example:"#aabbcc"]_) - Changes the ForeColor in  _Dark_ themes.  
  
  ![Image](images/StylishCode_ForeColor2.PNG)

> Note : If you do not specify the __ForeColorLight__ for light themes, it will be changed to the _Inverse_  colour of the colour value when you see this member in light themes.
>
>![Image](images/StylishCode_ForeColor3.jpg)

  2. __ForeColorLight__ (*): (_[string property] hex web color [example:"#aabbcc"]_) - Changes the ForeColor in  _Light_ themes.

  ![Image](images/StylishCode_ForeColorLight.PNG)

> Note : If you do not specify the __ForeColor__ for dark themes, it will be changed to the _Inverse_ colour of the colour value when you see this member in dark themes.
>
>![Image](images/StylishCode_ForeColorLight2.jpg)

  3. __ForeColorOpacity__ : (_[double property] floating point number between 0 and 1 [example: 0.5]_) - Changes the opacity of the ForeColor in both _Dark_ and _Light_ themes. 0 is fully transparent and 1 is solid colour.  
   ![Image](images/StylishCode_ForeColorOpacity.PNG)
   >Note : Opacity will be applied for both _Dark_ and _Light_ fore colour themes.

  4. __BackColor__ (*): (_[string property] hex web color [example:"#aabbcc"]_) - Changes the background colour in _Dark_ theme.
   
  ![Image](images/StylishCode_BackColor.PNG)

> Note : If you do not specify the __BackColorLight__ for light themes, this will be changed to the _Inverse_ of the colour value you see in the dark theme.
>
>![Image](images/StylishCode_BackColorInversLight.PNG)

  5. __BackColorLight__ (*): (_[string property] hex web color [example:"#aabbcc"]_) - Changes the Background color in the _Light_ theme.

  ![Image](images/StylishCode_BackColorLight.PNG)

> Note : If you do not specify the __BackColor__ for dark themes this will be changed to the _Inverse_ of the color value you see in the light theme.
>
>![Image](images/StylishCode_BackColorLightInversDark.PNG)

  6. __BackColorOpacity__ : (_[double property] floating point number between 0 and 1 [example: 0.5]_) - Changes the opacity of the Background Color in both _Dark_ and _Light_ themes. 0 is fully transparent and 1 is solid color.
   
  ![Image](images/StylishCode_BackColorOpacity.PNG)
   
  7. __Bold__ : (_[boolean property] a boolean variable with true/false value_) - Changes the text style to __bold__ when it's value is true and false for regular style.

![Image](images/StylishCode_Bold.PNG)

  8. __Italic__ :(_[boolean property] a boolean variable with true/false value_) - Changes the text style to _italic_ when it's value is true and false for regular style.
  
  ![Image](images/StylishCode_BoldItalic.PNG)
  
  9.  __Underline__ : (_[boolean property] a boolean variable with true/false value_) - Underlines the text when it's value is true and clears the underline when it's value is not set or false.
  
  ![Image](images/StylishCode_Underline.PNG)

  10. __Overline__ : (_[boolean property] a boolean variable with true/false value_) - Places a line over the text when it's value is true and clears the overline when it's value is not set or false.

  ![Image](images/StylishCode_Overline.PNG)

  11. __Line_Color__ :(_[string property] hex web color [example:"#aabbcc"]_) - Changes the line color (underline or overline) in both color themes.
  
  ![Image](images/StylishCode_line_color.PNG)
  
  12. __Line_Offset__ : (_[double property] floating point number [default: 0.3]_)- Changes the line offset of the under-line and over-line from the text base line. This property will only take effect when you set underline, overline, or both to true.
  
  ![Image](images/StylishCode_line_offset.PNG)

  13. __Line_Thikness__ :(_[double property] floating point number [default: 1]_) - Changes the line thickness of the underline or overline. This property will only take effect when you set underline, overline, or both to true.
  
  ![Image](images/StylishCode_line_tickness.PNG)
  
  14. __FontSize__ :(_[int property] integer number [example: 16]_) - Changes the font size of the text.

  ![Image](images/StylishCode_FontSize.PNG)

  >(*) : _The Color can be in a gradient style as well. We will explain how to use this in the next section._
  >
  >Note : There is a built-in Color Picker Panel to help you choose your desired colours easily. Whenever you write hex colour strings (like "#aabbcc"), a small coloured box with the specified color will be placed on the left side of the string literal. You can click the box and a StylishCode Color Picker Panel will be displayed. You can then pick the color in 4 different ways :
  >1. Change the color string text interactively using the color text editor.
  >2. Pick the colour (Select Colour Range) from saturation gradient colour levels.
  >3. Pick the colour from hue colour area.
  >4. Select the color transparency.
  >
  >![Image](images/StylishCode_ColorPickerInputs.jpg)

### Attribute Decoration, Color values and Gradient Styles

Here are some tips you can use to further stylize your code using the GeeksStylishCode extension:

1. You can decorate your attributes separately, refer to some of the sections above for examples like __FontSize__.

2. You can use the string literal html colour names with the (>) prefix (greater than sign) instead of colour code hex values, like this:

  ![Image](images/StylishCode_ColorNames.PNG)

3. You can define gradient colours instead of solid colours in both ForeColor and BackColor properties.
   
   ![Image](images/StylishCode_ColorGradient1.PNG)
  > Note 1: You can separate your stop colours with the (-)_Dash_ or the (|)_Pipe_ signs.
  >
  > Note 2: You can define the offset value using a numeric value in front of the colour - with or without a _percent_ (__%__) sign, you must then separate the colour with a _space_ to change the length of the colours in the gradient.  
  >![Image](images/StylishCode_ColorGradient2.PNG)
  >
  > Note 3: You can change the orientation of the linear colour gradient with an integer parameter in front of each color gradient separated by a _Dash_ or _Pipe_ sign.
  >
  >![Image](images/StylishCode_ColorGradient3.PNG)
  
## VS Ext: MSharp.CodePreview

CodePreview VSIX is a useful extension developed to help M# programmers rapidly observe code generated by the M# engine in real-time. After the whole project is built, the preview is displayed within a tool-window on the right hand side of code editor window.
You can open the Code Preview too-window by selecting **"Show Generated Code"** from the currently open code editor window menu.

![Image](images/CodePreview4.PNG)

There will be 3 tabs in the _Preview Generated Code_ window with different titles. If you invoke this command in M# UI modules, the Preview Generated Code window will appear with the following tabs :
_Preview_, _Controller_, _Cshtml_.

![Image](images/CodePreview1.PNG)

![Image](images/CodePreview2.PNG)

![Image](images/CodePreview3.PNG)

If you invoke this command in M# Entity classes, you will see the Preview Generated Code window with the following tabs :
_Sql_, _DAL_, _Structure_.

![Image](images/CodePreview5.PNG)

![Image](images/CodePreview6.PNG)

![Image](images/CodePreview7.PNG)

## VS Ext: MSharp.Goto

In many cases developers need to switch to definitions and references throughout the solution, for example between the Model and generated code when using M# Entities. Using MSharp.Goto, you can go to the declared classes and all its references.
Using MSharp GoTo VSIX, you can switch to the declaration of generated classes or its properties faster and more effectively.
In C#, generated classes are in the Gen-Entities folder in the Domain project, you can toggle the context-based suggestion menu in the editor by pressing [CTRL+.] over the class identifier name (Class Name) or property identifier name (Property Name). A light-bulb pops up with a custom suggestion "Goto Definition.".If you select this, you will navigate to the declaration class in the Model project.

![Image](images/Goto1.JPG)

You can also navigate to the generated class by invoking the suggestion menu (Ctrl+.) over class name identifier. You will then see 2 custom suggestions; "Where is {ClassName} used?" and "Show generated class for {ClassName}.".

![Image](images/Goto2.JPG)

If you select "Where is {ClassName} used?", you can navigate to any of the references in the references toolbox panel by selecting an item.

![Image](images/Goto3.JPG)

Also you can navigate to the generated class in the Domain project by selecting the "Show generated class fo {ClassName}." item.

Often when you're working with code, for every concept there are multiple code files, which are effectively sister files all related to that concept.

With this extension, when you open a M# class file that has sister files, all of the related files will be displayed as navigation buttons in right corner of code editor window. By pressing each one you can jump to the related file in Visual Studio. When there are multiple sister files in the same category, all other files will be shown in the drop-down list you can navigate to.

![Image](images/SisterButtons.PNG)

These buttons are shown in different colors, so you can navigate better across sister files. There are 3 types of buttons available to navigate to sister files (and 1 other button if you installed CodePreview VSIX) categorized by these 4 colors :

> ![Image](images/Purple.PNG) Pink  : Currently opened document button will be displayed as Pink, with the title of current file type.
> 
> ![Image](images/Magenta.PNG) Purple : Other sister files will be shown as purple buttons, with the title of sister type.
> 
> ![Image](images/Green.PNG) Cyan : Cyan buttons are not really sister files. This buttons shows files that are related to currently open file, so that you can navigate to these files.
> 
>> ![Image](images/Preview.PNG) Orange : If you have installed the **CodePreview VSIX** and you open an M# UI class, an additional Orange button with the M# icon will appear at the end of navigation buttons list. If you click this button, you can see the HTML preview of your current UI class.

## VS Ext: MSharp.Intellisense

Writing C# in M# modules can be a pain. For example, writing the below bit of code in a string can be annoying with no intellisense and visual studio features.

![Image](images/Intellisens1.jpeg)

This is where the Intellisense VSIX comes in! We can work with code in fast and easy way.

![Image](images/Intellisens3.jpeg)

When the cursor is under calling method or its string literal parameter, you can open a code peeker just below the current line by the right clicking on the method name or its string parameter. Then select "Show Intellisense For String Parameter Alt+ I" item from the context menu.

![Image](images/Intellisens4.jpeg)

or pressing [ALT + I] shortcut key or by invoking the light-bulb command when it's suggested or hitting the [CTRL + .] key combination on the proper line and select the "Show Intellisense for string parameter" command.

![Image](images/Intellisens5.jpeg)

The Intellisense VSIX uses MSharp.exe to generate a temporary intellisense C# file. The peeker loads that temporary file and developers can manipulate their code in the right C# code context. When hitting [CTRL + S] it will close the peeker menu and add the code as a string.

### Technical Tip 1

Sometimes it may take a while to show the peeker with the C# context. This depends on the project size and system performance, because a temporary C# (with name **IntellisenseTemp.cs**) file will be populated and created in the \_M#\_TEMP folder under the WebSite project.

![Image](images/Intellisens6.jpeg)

Then Intellisense VSIX shows the code file in the peeker, while the file is being generated, you can see a progress bar on top of displayed empty peeker.

![Image](images/Intellisens2.jpeg)

### Technical Tip 2

(**Troubleshooting**) If you can't see the peeker panel after a while, or you get a "No Result or "We did not find any result." message,  MSharp.exe might have returned an error and the intellisense temporary file has not been generated correctly in \_M#\_TEMP. In this case check the following :

- Make sure the solution is fully compiled without any errors.
- Make sure #UI.dll, #Model.dll, MSharp.exe and MSharp.DLS.exe exist in the "[Solution Path]\M#\Lib\".
- Run MSharp.exe from command line with some sample parameters to ensure everything works well.

> [![Image](images/CLI.png "M# Command Line Interface") CLI Command](CLI.md) :
> MSharp.exe /intellisense {Switch} /file:{FullFileName} /setting:{Setting} /line:{line number} /text:{C# code}
>
> Sample CLI command :
> MSharp.exe /intellisense /ExpectsCSharpStatement /file:"C:\Geeks\SampleApp\M#\UI\Modules-Custom\Header.cs" /setting:Code /line:39 /text:"var i = Math.Cos(90)"
> _*Switch* : all attributes that in ExpectsCSharp category like /ExpectsCSharpStatement
> \_\_FullFileName_ : C# file with full path containing Method calling like C:\Geeks\SampleApp\M#\UI\Modules-Custom\Header.cs
> _*Setting* : Method name that we would like to have C# context of its code.
> \_\_Line Number_ : Line number of the method(_Setting_) in _FullFileName_. \*_Text_ : C# code or constant that is currently in parameter of the method(_Setting_).

![Image](images/Intellisens8.jpeg)

### Technical Note

C# code file that opened by Intellisense Peeker Panel, is used only for specific manner, So developers can not make changes (and they do not need to do this) in top and bottom code area that wraps the original code/text, so those parts of code are read-only.

### **Debugging** Tip

If you the set "DEBUG:" prefix in start of code in a string literal, an error log file will be created in Lib folder in this location : "[Solution Path]\M#\Lib\Intellisense.log".

![Image](images/Intellisens9.jpeg)

You can close peeker panel with or without saving code. If you have made changes and you try to close the peeker, a messages box appears  asking you about saving changes by reflecting them to the main code or not. Otherwise peeker panel will simply close.

![Image](images/Intellisens7.jpeg)

You can also close the peeker by pressing the CTRL + S key. All changes will be saved and will be reflect to the main code.

## VS Ext: MSharp.Snippet

Development with M# always is fun! This work is more simple and fun if you use our custom Visual Studio extensions.

 A snippet is a programming term for a small region of re-usable source code. Ordinarily, these are formally defined operative units to incorporate into larger programming modules.

MSharp Snippet is custom Visual Studio extension that contains many useful small parts of code. These are useful when you want to write UI code. Snippets are defined in MSharp.Snippet extension, and each one are declared in simple XML file. After Visual Studio loads this package, you can call their shortcut name to put the template inside your code. This example is a button create snippet :

```XML
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippet Format="1.0.0" xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <Header>
    <Title>Button</Title>
    <Author>Geeks Ltd</Author>
    <Shortcut>Button</Shortcut>
    <Description>Code snippet for simple button.</Description>
    <SnippetTypes>
      <SnippetType>Expansion</SnippetType>
    </SnippetTypes>
  </Header>
  <Snippet>
    <Declarations>
      <Literal>
        <ID>name</ID>
        <ToolTip>Button name</ToolTip>
        <Default>ButtonName</Default>
      </Literal>
      <Literal>
        <ID>action</ID>
        <ToolTip>The action</ToolTip>
        <Default>...</Default>
      </Literal>
    </Declarations>
    <Code Language="csharp">
      <![CDATA[Button("$name$")
                .Action(x => $action$);$end$]]>
    </Code>
  </Snippet>
</CodeSnippet>
```

Each Snippet contains in 2 parts, Header and Snippet. You can use them by writing their shortcut name and pressing the TAB key.
In this example shortcut name is "Button" and template code is :

![Image](images/Snippet1.JPG)

```C#
    Button("$name$")
      .Action(x => $action$);
```

![Image](images/Snippet2.JPG)

For greater simplicity and usefulness there are place holders in some snippets, you just need to fill in the blanks. This will help you write code faster, and make it more robust. In our example, $name$ and $action$ are code placeholders and $end$ is defined the end cursor location after snippet completion. Also you can see every Snippet have metadata in it's definition point. This metadata can be used in Visual Studio Snippet Manager Window.

In general it is better that you know Snippets, their shortcut names and functionality.
Here is the list of all Snippets that supported in the latest extension version :

> - Shortcut name : _Button_
> - M# Code:
> - **Button("$name$").Action(x => $action$);**
> - Description: Code snippet for simple button.

> - Shortcut name : _ButtonAddNew_
> - M# Code:
> - \*\*Button("$name$").Icon($icon$)

            .Action(x => x.Go<$page$>()
            $sendReturnUrl$);**

> - Description: Code snippet for a adding new button.

> - Shortcut name : _ButtonBack_
> - M# Code:
> - \*\*Button("$name$")

            .Action(x => $back$);**

> - Description: Code snippet for a back button.

> - Shortcut name : _ButtonCancel_
> - M# Code:
> - \*\*Button("$name$").CausesValidation(value: false)

            .Action(x => $close$);**

> - Description: Code snippet for a cancel button.

> - Shortcut name : _ButtonDelete_
> - M# Code:
> - \*\*ButtonColumn("$name$").Icon($icon$)

            .Action(x =>
            {
               $delete$
               $reload$
            });**

> - Description: Code snippet for a delete button.

> - Shortcut name : _ButtonEdit_
> - M# Code:
> - \*\*ButtonColumn("$name$").Icon($icon$)

            .Action(x => x.Go<$page$>()
            $sendReturnUrl$$send$);**

> - Description: Code snippet for an edit button.

> - Shortcut name : _ButtonExportToCsv_
> - M# Code:
> - \*\*CButton("$name$").Icon($icon$)

            .Action(x => $action$);**

> - Description: Code snippet for an export-to-csv button.

> - Shortcut name : _ButtonExportToExcel_
> - M# Code:
> - \*\*Button("$name$").Icon($icon$)

            .Action(x => $action$);**

> - Description: Code snippet for an export-to-excel button.

> - Shortcut name : _ButtonSave_
> - M# Code:
> - \*\*Button("$name$").IsDefault().Icon($icon$)

            .Action(x =>
            {
                $saveAction$
                $showMessage$
                $close$
            });**

> - Description: Code snippet for a save button.

> - Shortcut name : _ButtonSearch_
> - M# Code:
> - \*\*Button("$name$").Icon($icon$)

            .Action(x => $action$);**

> - Description: Code snippet for a search button.

> - Shortcut name : _ButtonSort_
> - M# Code:
> - \*\*Button("$name$")

            .Action(x => $action$);**

> - Description: Code snippet for a sort button.

## VS Ext: MSharp.Warnings

When you are developing M# project, you might write some code that produces warnings when complied with MSharp.dsl.
According to the Olive compatibility change log (3th Jan), in normal M# projects (Model and UI sub-project) you should at least have an after build target task to participate M# build to your projects, so your _Model.csproject_ and _UI.csproject_ files should contain theses section in the project structure node like this:

```XML
<Target Name="Generate code" AfterTargets="AfterBuild">
    <Exec Condition="'$(MSHARP_BUILD)' != 'FULL'" WorkingDirectory="$(TargetDir)" 
	  Command="dotnet msharp.dsl.dll /build /model /warn" />
</Target>
```
for _M# Model project_ And :

```XML
<Target Name="Generate code" AfterTargets="AfterBuild">
    <Exec Condition="'$(MSHARP_BUILD)' != 'FULL'" WorkingDirectory="$(TargetDir)" 
	  Command="dotnet msharp.dsl.dll /build /ui /warn" />
</Target>
```
for _M# UI project_. In fact you can run the M# build command from the command line as a CLI command in this style :

```
...\M#\lib> dotnet msharp.dsl.dll /build [/model|/ui] [/warn]
or
...\M#\lib> msharp.dsl.exe /build [/model|/ui] [/warn]
```

So when you build your M# projects with **/WARN** switch, if any projects have warnings an XML file should be placed in the __obj__ folder of each project :

```
...\M#\Model\Obj\MSharp.Warnings.xml
and/or
...\M#\UI\Obj\MSharp.Warnings.xml
```
These are simple XML files containing valuable information about M# coding styles. As you may know, M# warnings are notices about best practices or some M# development designing patterns. They exist to help M# developers write better, more maintainable code, and are displayed in the Visual Studio Standard Error Window. 

For example this is a simple **UI** warning file :
```XML
<Warnings>
  <Warning Type="ViewElement" Property="LabelText" Source="UI\Modules\..abc.cs:line 115">As this module is using a custom Markup, this column will be ignored, so remove it to prevent confusion.</Warning>
  <Warning Type="ApplicationPage" Property="Name" Source="UI\Pages\...xyz.cs:line 13">This page seems to be orphand. There is no standard Navigate Activity pointing to it.</Warning>
    <Warning Type="ModuleCodeExtension" Property="Code" Source="UI\Modules\..ijk.cs:line 44">Custom code is too long. Do you really need it? Can you reuse some M# alternatives?
If not, you should still break it into smaller methods with well defined, self-explanatory names.</Warning>
  <Warning Type="GenericFormElement" Property="ControlMarkup" Source="UI\Modules\...qwe.cs:line 30">There is too much custom code here. Refactor it, break it down, move logic to Model project, etc.</Warning>
</Warnings>
```

And this is a simple **Model** warning file :

```XML
<Warnings>
  <Warning Type="Association" Property="DatabaseIndex" Source="Model\...abc.cs:line 9">This association is referenced in its inverse association. So it's likely to get frequent queries on this column. Consider putting an index on it.</Warning>
  <Warning Type="BooleanProperty" Property="Title" Source="Model\...ijk.cs:line 71">Property title should be « Proper case ».</Warning>
</Warnings>
```

![Image](images/WarningsErrorsList.PNG)

When you double click on a warning row in the Error List window, you will navigate to the exact line of code that produced the warning.

![Image](images/WarningsMSharpCode.PNG)

As you can see in the code editor window, an exclamation triangle icon is displayed in front of each line that has a warning. A purple squiggle line is drawn under each of the warning lines, so you can see a brief description of the warning as a meta tooltip window.

>Technical Note: Exclamation icon and squiggle lines are displayed in the code window by implementing Visual Studio Adornment Tagger. So when we populate warnings from warning file, after inserting each one into the error window, a C# regional standard comment will be placed in front of code line that describes warning information for the tagger in this reqular expression style :

```regex
\/\*M#:(?<type>\w)\[(?<line>\d+)\](?<show>[ |-|H|T])-Prop:(?<prp>\w*)-Type:(?<typ>\w*)-(?<txt>.*)?\*\/
```

So decorated M# line will be something like this :

```c#
/*M#:w[25]T-Prop:Title-Type:BooleanProperty-Property title should be « Proper case ».*/Bool("ToClientContractors").Mandatory();
```

__it should be displayed as :__  ![Image](images/WarningsMSharpCode2.PNG) and the warning text will be placed in the tooltip window after a mouse hover on the icon/squiggles.

> __Hidden feature (1)__: Currently Warning VSIX is supported 5 different types of notifications : 
> * ![Image](images/Warning16.png) Warning (type : __w__)
> * ![Image](images/Info16.png) Information (type : __i__)
> * ![Image](images/Error16.png) Error (type : __e__)
> * ![Image](images/Event16.png) Event (type : __v__)
> * ![Image](images/MSharp16.png) MSharp (type : __m__)
>
> So if you write a regional comment in pre-defined format with special type, like the one of the notification style above, you can have a notification icon in your code ;) like this :

```C#
            /*M#:w[15]T-Prop:Title-Type:Custom-Custom Notification Warning Text*/ // Warning
            /*M#:i[16]T-Prop:Title-Type:Custom-Custom Notification Information Text*/ // Information
            /*M#:e[17]T-Prop:Title-Type:Custom-Custom Notification Error Text*/ // Error
            /*M#:v[18]T-Prop:Title-Type:Custom-Custom Notification Event Text*/ // Event
            /*M#:m[19]T-Prop:Title-Type:Custom-Custom Notification MSharp Text*/ // MSharp
```

![Image](images/WarningsMSharpCode3.PNG)
> _Line-Number_, _Prop_ and _Type_ sections can be fill with temp data in these cases.

> __Hidden Feature (2)__: Descriptive text will be displayed whenever you hover your mouse cursor over the icons or squiggles, but it is possible to show text notifications just beside of the icon :
> * By put a " "_(SPACE)_ after close bracket of line number (**[xx]**) and before __"-prop:"__
> ```c#
> /*M#:w[15] -Prop:Title-Type:Custom-Custom Notification Warning Text*/ // Warning
> ```
> * By put an __H__ character after close bracket of line number (**[xx]**) and before __"-prop:"__
> ```c#
> /*M#:i[16]H-Prop:Title-Type:Custom-Custom Notification Information Text*/ // Information
> ```
> 
> in these cases a  button will be displayed after each icon so you can collapse or expand the descriptions interactively in your code.
>
> ![Image](images/WarningsMSharpCode4.PNG)
>
> Descriptions with " "_(SPACE)_ should be displayed expanded in front of icons by default and __H__ means they have to be shown after pressing the expand button (hidden by default).
