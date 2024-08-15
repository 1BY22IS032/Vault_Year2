# Swing Questions

## TO DO 
 
1. FLowChart of JavaSwing ```JRadioButton```


## Difference between AWT and Swing

![AWTvsSWING](https://cdn.imgchest.com/files/w7pjc2jgxe7.jpg)

## MVC Architecture

- Model:Data
- Veiw : Visual Representation
- Controller : takes input from user and reflects in data
- In swing; model is separate while veiw and controller are clubbed together in User Interface elements

![MVC](https://cdn.imgchest.com/files/j7mmc6xbxp7.png)

- model corresponds to the state information associated with the component
- Veiw determines the components's view and feel
- Controller determines how the gui reacts to the user

## Components and Containers

- A component is an independent visual control, such as push button or slider
- A container holds a group of components
- if a component need to be displayed, it must be held within a container

### Components

- Derived from JComponent class
- JComponent inherits AWT's Container and components
- All are present inside javax.swing
- Examples:

```java
    JButton button = new JButton("Click Me");
    JLabel label = new JLabel("Hello, World!");
    JTextField textField = new JTextField(20);
    JCheckBox checkBox = new JCheckBox("Accept Terms");
```

### Containers

- 2 Types : Top level, Lightweight
- Top Level : JFrame, JApplet etc. 
  - Do not inherit Jcomponent but inherit AWT's Containers&Component
  - Top of containment heirachy
  - JFrame for applications, JApplet for Applets
- Leightweight:
  - Inherit JComponent
  - often used to organize and manage groups of related components

## Painting

- Swing also lets you write directly into the display area of a frame, panel, or one of Swing’s other components
- To write output directly to the surface of a component, you will use one or more drawing methods defined by the AWT, such as drawLine() or drawRect()
- The AWT class Component defines a method called paint( ) that is used to draw output directly to the surface of a component
- paint( ) is called by the run-time system whenever a component must be rendered
- Swings uses three distinct methods: paintComponent( ), paintBorder( ), and paintChildren( )
- protected void paintComponent(Graphics g)// g is the graphics context to which output is written

Here is the content from the image formatted in Markdown:

### Compute the Paintable Area

- Swing automatically clips any output that will exceed the boundaries of a component, it is still possible to paint into the border, which will then get overwritten when the border is drawn.
- The area defined by the current size of the component minus the space used by the border.
- To obtain the border width, call `getInsets()`, shown here:
  - `Insets getInsets()` method is defined by `Container` and overridden by `JComponent`.
  - It returns an `Insets` object that contains the dimensions of the border.
  - **inset values** can be obtained by using `(int top; int bottom; int left; int right;)`
  - Obtain the width and height of the component by calling `getWidth()` and `getHeight()` on the component.
- By subtracting the value of the insets, you can compute the usable width and height of the component.


```java
import java.awt.*;
import java.util.*;
import javax.swing.*;

class PaintPanel extends JPanel {
    Insets ins;
    Random rand;

    PaintPanel() {
        setBorder(BorderFactory.createLineBorder(Color.RED, 5));
        rand = new Random();
    }

    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        int x, y, x2, y2;
        int height = getHeight();
        int width = getWidth();
        ins = getInsets();
        for (int i = 0; i < 10; i++) {
            x = rand.nextInt(width - ins.left);
            y = rand.nextInt(height - ins.bottom);
            x2 = rand.nextInt(width - ins.left);
            y2 = rand.nextInt(height - ins.bottom);
            g.drawLine(x, y, x2, y2);
        }
    }
}

class PaintDemo {
    JLabel jlab;
    PaintPanel pp;

    PaintDemo() {
        JFrame jfrm = new JFrame("Paint Demo");
        jfrm.setSize(200, 150);
        jfrm.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        pp = new PaintPanel();
        jfrm.add(pp);
        jfrm.setVisible(true);
    }

    public static void main(String args[]) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new PaintDemo();
            }
        });
    }
}

```

## JList

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class SimpleListDemo extends JFrame {
    private DefaultListModel<String> listModel;
    private JList<String> itemList;
    private JTextField itemTextField;
    private JButton addButton;
    private JButton removeButton;

    public SimpleListDemo() {
        setTitle("Simple JList Demo");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        listModel = new DefaultListModel<>();
        itemList = new JList<>(listModel);

        itemTextField = new JTextField(10);
        addButton = new JButton("Add");
        removeButton = new JButton("Remove");

        JPanel inputPanel = new JPanel();
        inputPanel.add(itemTextField);
        inputPanel.add(addButton);
        inputPanel.add(removeButton);

        add(new JScrollPane(itemList), BorderLayout.CENTER);
        add(inputPanel, BorderLayout.SOUTH);

        addButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String item = itemTextField.getText();
                if (!item.isEmpty()) {
                    listModel.addElement(item);
                    itemTextField.setText("");
                }
            }
        });

        removeButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                int selectedIndex = itemList.getSelectedIndex();
                if (selectedIndex != -1) {
                    listModel.remove(selectedIndex);
                }
            }
        });

        setVisible(true);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new SimpleListDemo();
            }
        });
    }
}
```


1. **Add an Item**
   - `listModel.addElement(item)`
   - Adds the specified item to the end of the list.

2. **Remove an Item**
   - `listModel.remove(index)`
   - Removes the item at the specified index from the list.

3. **Get Item Count**
   - `listModel.getSize()`
   - Returns the number of elements in the list.

4. **Get Item at a Specific Index**
   - `listModel.getElementAt(index)`
   - Returns the item at the specified index.

5. **Clear All Items**
   - `listModel.clear()`
   - Removes all elements from the list.
