# GUI Addition - Instructions

For this assignment, you are going to pick one of your previous assignments and add a GUI to it. You can pick Homework 03/04, 05/06, or 07/08, and you will revamp the assignment to follow the MVC design pattern. 

"Living with your code" is a common expression used in computer science. It means when you write code you should expect to have to come back to it and work with it again. This assignment is meant to give you a sense of that by having you use the code from your previous assignment, while adding more features to that code base. 


## Learning Objectives
* Understand the process of adding a GUI to an existing program
* Modify existing code to work with multiple types of views / adding new features.


## Instructions

You will need to take a previous assignment (03/04, 05/06, or 07/08) and convert it into the MVC design pattern. Additionally, you will need to add a GUI to the program, which means this assignment is a culmination of everything you learned up until this point. 

Suggested Parts:
1. Copy your code from the previous assignment into this repository  
2. Modify your application making sure you take steps to test each modification *AS YOU MODIFY*. 
3. Work on designing your GUI. Grading for the GUI will be based on screenshots and the TAs running your program if they don't see obvious tests/clarity in what you are providing. 


> [!TIP]
> We have once again provided a sample working program, that includes both the console and GUI version. This is a very basic GUI for DNInfo, you do not (nor should you) copy the design, but instead use it as a reference for minimum functionality. The weird X and . characters are just because it is a demo version.
>
> From the sample_working directory. 
>
> To run the GUI version, you can use the following command
> 
> ```
>  bin/DNInfoGUI -g
> ```
> or if on windows
> ```
> bin\DNInfoGUI.bat -g
> ```
>  To run the console version, you can use the following command
> ```
> bin/DNInfoGUI -c
> ```
> or if on windows
> ```
>   bin\DNInfoGUI.bat -c
> ```
> as with before you can run help by doing
> ```
> bin/DNInfoGUI -h
> ```
> or if on windows
> ```
> bin\DNInfoGUI.bat -h
> ```
> It is worth noting the old DNINfo app functionality (command line arguments) are
> all still there. We only added the views in this assignment. 

### :fire: Task 1: Design 

Before you start writing, it is important to think about design. You DO NOT have to be perfect in your design, so we will come back to this step a few times. 


1. Go to [DesignDocument.md](../DesignDocument.md) and fill out (ONLY) the initial design sections. Make sure to start with the end design of whatever assignment you are modifying! 

> [!TIP]
> You are free  to use mermaid or any other UML tools you want, just make sure if you are using another UML tool, you properly link the image in the Markdown file. See the resources page, for a list of [UML tools](https://github.com/CS5004-khoury-oak-monge/Resources?tab=readme-ov-file#uml-design-tools).


### :fire: Task 2: Implement by Test Driven Development

After your initial design, you should seek to follow the TDD process. This means you should write tests first, and then implement the code to pass those tests. Or better stated, you should write *ONE* test first, implement, and repeat until you have written all your tests. 

1. Figure out a number of tests by brainstorming (done in design)
2. Write **one** test
3. Write **just enough** code to make that test pass
4. Refactor/update  as you go along
5. Repeat steps 2-4 until you have all the tests passing/fully built program

Note: you often don't know all the tests as you write. As such, it is alright to continue to expand your list. This is where people get stuck on TDD. They think they have to know **all** the tests before they start. You don't. You just need to know the next test, and then at the end you double-check you have covered all code paths and have full coverage. 

> [!CAUTION]
> Make sure to commit as you development. The bare minimum commits would be after every test, but you probably will have additional commits especially at the beginning. 


#### Testing GUIs
When it comes to testing GUIs you often have to document how you tested, and what you did. Use the [GuiTestingHistory.md](../GuiTestingHistory.md) document to document including screenshots of your testing.

#### :raising_hand: Implementation Tips
Here are a few tips to help you out.
* The GUI is *always* easier to write in parts and test those parts. For example, we created the JFrame, ran the program, and slowly started adding components. After we had the look at feel we wanted, we then added the functionality (the listeners).
* For a file chooser/dialog, you can use the JFileChooser. This is a common component in Java Swing. Here is an example of our FileChooser.
```java
   JFileChooser fileChooser = new JFileChooser();
   fileChooser.setAcceptAllFileFilterUsed(false);
   fileChooser.setCurrentDirectory(new File(System.getProperty("user.dir")));
   fileChooser.setDialogTitle("Export List");
   fileChooser.setFileFilter(new FileNameExtensionFilter("XML (*.xml)", "xml"));
   fileChooser.addChoosableFileFilter(new FileNameExtensionFilter("JSON (*.json)", "json"));
   fileChooser.addChoosableFileFilter(new FileNameExtensionFilter("CSV (*.csv)", "csv"));
   fileChooser.addChoosableFileFilter(new FileNameExtensionFilter("Text (*.txt)", "txt"));

   int userSelection = fileChooser.showSaveDialog(this);

   if (userSelection == JFileChooser.APPROVE_OPTION) {
   // do something
   }
```

### IMPORTANT! 
HAVE FUN! You can play with features. Maybe you want to use the latitude/ longitude to display a location on a map. You are not limited to the bare minimum for this GUI. While we will only grade making sure you have all the minimum features, you can add more. If you go above and beyond, make sure to document it in the final design document - so that the TAs (and thus instructor) can see it! We also encourage sharing some of your final screenshots in Teams if you add a neat feature you want to share (after the "available until date")

 
### :fire: Task 3: Finish Design Document

By this point, your design has probably changed (very few people have perfect designs the first iteration). Update your design document with the final design in the "final design" section. We want to see the history of your first design to your final design. That is a good thing. 


### :fire: Task 4: Build a Manual 

Inside of [Manual](../manual) You will need to build a 'manual' for your application. It presents screenshots of the GUI, and explains how to use the program in a logical manner. Reading this manual one should have a sense of the full features of the program. 


## 🤖 Use of LLMs

You may use LLMs extensively for this assignment since GUI layout code is tedious boilerplate. However, **your event handling logic and integration with existing classes must be your own design**.

### What's Different This Time

You will be adding a GUI to an existing application (make sure to copy over the old application code first, commit, and then work on the gui). LLMs excel at generating Swing/AWT layout code, but you need to understand what they generate and integrate it properly with your backend logic.

### Recommended LLM Usage

#### ✅ **Good Uses:**
1. **Generating GUI layout code** (panels, labels, buttons, text fields)
2. **Learning Swing/AWT components** and layout managers
3. **Troubleshooting layout issues** (components not appearing, sizing problems)
4. **Understanding event listeners** (ActionListener, MouseListener, etc.)
5. **Generating unit tests** for your GUI components

#### ❌ **Avoid:**
- Having AI design how your GUI connects to your backend
- Copying layout code without understanding it
- Using AI to write your report or design rationale
- Letting AI make architectural decisions about MVC structure

### Smart Prompting for This Assignment

#### **For Creating Basic Layouts**

````
Create a class that extends JPanel. Inside that panel, I want:
- A label that says 'hostname'
- A text field that is 20 characters long
- A button that says 'search'

Layout requirements:
- The search button should be the same length as the text field
- The button sits directly under the text field
- The label should be above the text field
- The panel should be 200x200 pixels
- All components should be centered
- Each component should have a 10 pixel margin

Use appropriate layout managers to achieve this spacing.
````

**⚠️ IMPORTANT:** This prompt will give you a starting point, but **often has errors**. You MUST:
- Test the generated code
- Understand what each line does
- Modify spacing/sizing to match your needs
- Fix any layout issues yourself

#### **For Understanding Swing Components**

````
I'm new to Java Swing and need to understand basic components.

Please explain:
1. What's the difference between JFrame, JPanel, and JDialog?
2. When should I use JTextField vs JTextArea?
3. What are the main layout managers (FlowLayout, BorderLayout, GridLayout, etc.) and when to use each?
4. How do I add components to a panel?
5. Show me a minimal example of a window with one button

Keep it simple - I want to understand the basics first.
````

#### **For Event Handling**

````
I have a button in my GUI that should trigger an action when clicked. 

Please explain:
1. What is an ActionListener and how does it work?
2. How do I attach an ActionListener to a button?
3. Should I use an anonymous inner class, lambda, or separate class?
4. How do I get text from a JTextField when the button is clicked?
5. Show me a simple example of a button that prints text field contents

I want to understand the event-driven programming model.
````

#### **For Integrating GUI with Existing Code**

````
I have existing backend classes from previous assignments that handle data processing. Now I need to connect my GUI to them.

My backend has:
```java
[paste relevant method signatures]
```

My GUI has:
- A text field for user input
- A button to trigger processing
- An area to display results

Please explain:
1. Should my GUI classes directly instantiate backend classes, or use dependency injection?
2. Where should I handle exceptions from backend methods (GUI layer or backend)?
3. How do I update GUI components from backend results?
4. Should GUI event handlers call backend methods directly, or use a controller?
5. Show me a simple example structure (not full implementation)

Help me understand the architecture, not just write the code.
````

#### **For Layout Troubleshooting**

````
I'm having layout issues with my Swing GUI. Here's my code:

```java
[paste your layout code]
```

Problems I'm experiencing:
- [describe what's not working: components not appearing, wrong size, wrong position, etc.]

Please:
1. Identify what's causing the layout problem
2. Explain why the current approach isn't working
3. Suggest what layout manager or constraints to use instead
4. Show me the corrected code with explanations

Help me understand the layout system, not just fix this instance.
````

#### **For Making GUIs Responsive**

````
My GUI works but doesn't resize properly or feels unresponsive.

Please explain:
1. How do I make components resize appropriately when the window resizes?
2. Should I use SwingWorker for long-running operations? When?
3. How do I update GUI components from background threads safely?
4. What's the Event Dispatch Thread (EDT) and why does it matter?
5. Show me an example of proper threading for a button that triggers slow processing

I want to understand GUI responsiveness and threading.
````

#### **For Testing GUI Components**

````
I need to write tests for my GUI components.

Please explain:
1. What parts of a GUI should be unit tested vs. manually tested?
2. How do I test that a button click calls the correct method?
3. Can I test layout without visually inspecting it?
4. Show me an example of testing a simple panel with one button
5. What testing limitations exist for Swing GUIs?

I want realistic expectations about GUI testing.
````

### Critical Reminders for GUI Code

**NEVER trust AI-generated layout code blindly:**
- Always run it and see what it produces
- Component sizing is often wrong
- Layout managers may not be optimal
- Spacing/margins need adjustment
- Colors and fonts may not match your needs

**Common AI mistakes in GUI code:**
- Using absolute positioning (setLayout(null)) - avoid this!
- Incorrect layout manager choices
- Missing pack() or setVisible(true) calls
- Poor component organization
- Not handling window closing properly

**Your responsibility:**
- Understand every line of GUI code
- Choose appropriate layout managers yourself
- Ensure your GUI integrates cleanly with backend
- Handle all edge cases (empty inputs, errors, etc.)
- Make design decisions about user experience

### GUI Development Workflow

1. **Sketch your GUI on paper** - Know what you want before prompting
2. **Generate basic layout** - Use AI to create component structure
3. **Test immediately** - Run and see what it looks like
4. **Modify and refine** - Fix sizing, spacing, and layout issues
5. **Add event handling** - Connect buttons/fields to actions
6. **Integrate with backend** - Connect to your existing classes
7. **Test edge cases** - Empty inputs, errors, invalid data
8. **Polish** - Improve look and feel

### Pre-Submission Checklist

- [ ] I understand all GUI layout code (not just copied)
- [ ] I tested my GUI with various window sizes
- [ ] I connected GUI properly to my existing backend classes
- [ ] I handle errors gracefully (show error messages in GUI)
- [ ] I designed the user experience flow myself
- [ ] Event handlers connect properly to backend logic
- [ ] My GUI is responsive (no freezing during operations)
- [ ] I documented my LLM usage with specific examples

### LLM Disclosure Requirements

Include in your submission:
1. **What you used AI for** (e.g., "generating initial JPanel layout," "learning ActionListener syntax")
2. **Example prompts** showing how you used AI
3. **What you changed** from AI suggestions (this will be significant for GUI code)
4. **Design decisions AI didn't make** for you (UX flow, backend integration)

**Remember:** AI is great for GUI boilerplate, but the integration architecture and user experience design must be yours. This assignment tests your ability to build a complete application - the GUI is just the front door to your existing design. Also, it is worth noting, AI tends to try to generate the GUI in one giant file. You should not have this! Break up the files into smaller controlled components. 


## Submission

When you are completed, you need to submit your code to Gradescope. Go back to Canvas, and click through the link that takes you to the Gradescope assignment. When you submit, you will actually need to pull from your GitHub repository in the dialog that appears. It only pulls the most recent submission, and if you make an update to the repository after you submit, you will need to resubmit to get the latest version in Gradescope. 


## 📝 Grading Rubric

1. Learning (MG)
   * Code is fully documented using JavaDoc commenting style
   * Code has tests well organized for model layer, controller
2. Approaching (MG)
   * Follows style guidelines (suggestion run style check locally)
   * GuiTestingHistory.md - View has evidence of testing (via screenshots, and documentation on how you tested)
3. Meets (MG)
   * README.md is filled out (name, GitHub repo, etc) 
      * Without the link to your repo, the TAs won't grade the rest!
   * DesignDocument (INITIAL) sections are filled out 
   * Manual is so someone can easily use the program, showing screenshots of features.
4. Exceeds (MG)
   * Code is DRY (Don't Repeat Yourself)
      * Including making use of helping/utility classes to reduce duplication.
   * Student uses proper inheritance without duplication 
   * Methods include tests for edge cases in addition to happy path
   * Design document (FINAL) sections are filled out 
     * The notation needs to be correct, and the TAs will double-check the final design
     matches the final implementation.

Legend:
* AG - Auto-graded
* MG - Manually graded

### Submission Reminder 🚨
For manually graded elements, we only guarantee time to submit for a regrade IF you submit by the DUE DATE. Submitting late may mean it isn't possible for the MG to be graded before the AVAILABLE UNTIL DATE, removing any windows for you to resubmit in time. While it will be graded, it is always best to submit by the due date, so you have full opportunity to improve your grade.

If you need a reminder about the grading policy, please review the syllabus and the canvas page on 'formative/summative' grading. This class uses a unique grading system that will allow you to be flexible with due dates and multiple resubmissions (if you submit with time for TAs to give feedback), but we also ask that you continue to work on the assignment until you get a full grade.

> [!CAUTION]
> As this is the last assignment, your submission window between due date and available until date may be shorter! Please take that into account. 

### No Autograder - Still submit to Gradescope
This assignment has no autograder. As such, you will need to make sure you are following the rubric and the instructions. If you have questions, please ask in the Teams channel. The TAs will grade them as they see them, giving feedback as they go.
