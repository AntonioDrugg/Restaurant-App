# Restaurant-App
Part of the final project to Java Course
GUI for the app and the logic to calculate the bill, working with hard coded values.

package BillCaltulator;

//this imports AWT containers and components
import java.awt.*;
import java.awt.event.*;
import javax.*;

//this imports the Swing library so the class "RestaurantApp" can extend all the methods from Swing
import javax.swing.*;


// this is the main class, where the object "app" is declared and some basic information is added
public class MainTest {
	public static void main(String[] args) {
		RestaurantApp app = new RestaurantApp(); // creates the object (GUI)
		app.setSize(400, 600); // set the size of the graphic object
		app.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // determine that the program ends whenever the graphic object is closed
		app.setVisible(true); // determine that the object is visible
		app.setTitle("Restaurant Bill Calculator"); // determine the title text of the GUI
	}
}

class RestaurantApp extends JFrame {
	
	public int beveragefinalprice;
	public int apetizerfinalprice;
	public int maincoursefinalprice;
	public int dessertfinalprice;
	
	public int getBeveragefinalprice() {
		return beveragefinalprice;
	}

	public void setBeveragefinalprice(int beveragefinalprice) {
		this.beveragefinalprice = beveragefinalprice;
	}

	public int getApetizerfinalprice() {
		return apetizerfinalprice;
	}

	public void setApetizerfinalprice(int apetizerfinalprice) {
		this.apetizerfinalprice = apetizerfinalprice;
	}

	public int getMaincoursefinalprice() {
		return maincoursefinalprice;
	}

	public void setMaincoursefinalprice(int maincoursefinalprice) {
		this.maincoursefinalprice = maincoursefinalprice;
	}

	public int getDessertfinalprice() {
		return dessertfinalprice;
	}

	public void setDessertfinalprice(int dessertfinalprice) {
		this.dessertfinalprice = dessertfinalprice;
	}

	public RestaurantApp() {
		setLayout (null); // declare the GUI not to use a layout manager
		
		// Adds a label to the GUI
		JLabel restaurant = new JLabel("Restaurant"); // creates the label
		restaurant.setBounds(140, 2, 150, 50); // positioning the label
		restaurant.setFont(restaurant.getFont().deriveFont(20.0f)); // setting the font size
		add (restaurant); // adding the label, for it to be visible
		
		// Adds the first panel to the GUI, regarding the Waiter Information
		JPanel waiter = new JPanel (); // this adds an object that is a panel
		waiter.setBounds (20, 50, 340, 100); // setting the location of the panel
		waiter.setBorder(BorderFactory.createTitledBorder("Waiter Information")); // creating a border with a title to this panel
		add (waiter); // adding the panel, for it to be visible
		waiter.setLayout(null);
		JLabel tableNumber = new JLabel("Table Number:");
		tableNumber.setBounds (55, 25, 100, 25);
		waiter.add(tableNumber);
		JTextField table = new JTextField();
		table.setBounds(155, 25, 100, 25);
        waiter.add(table);
        JLabel waiterName = new JLabel("Waiter Name:");
		waiterName.setBounds (60, 55, 100, 25);
		waiter.add(waiterName);
		JTextField waiter2 = new JTextField();
		waiter2.setBounds(155, 55, 100, 25);
		waiter.add(waiter2);
        		
		// Adds the second panel to the GUI, regarding the Menu Information
		JPanel menu = new JPanel (); // this adds an object that is a panel
		menu.setBounds (20, 160, 340, 200); // setting the location of the panel
		menu.setBorder(BorderFactory.createTitledBorder("Menu Items")); // creating a border with a title to this panel
		add (menu);
		menu.setLayout(null);
		JLabel beverage = new JLabel("Beverage:");
		beverage.setBounds (40, 35, 100, 25);
		menu.add(beverage);
		String[] beverage3 = { "7 Up", "Beer", "Wine", "Juice"};
		int [] beverageprice1 = {4,5,6,4,5,0};
		JComboBox beverage2 = new JComboBox(beverage3);
		beverage2.setSelectedIndex(-1);
		beverage2.setBounds (140, 35, 150, 25);
		menu.add(beverage2);
		JLabel appetizer = new JLabel("Appetizer:");
		appetizer.setBounds (40, 75, 100, 25);
		menu.add(appetizer);
		String[] appetizer3 = {"Combo Plater", "Nachos", "Pan Fried Cheese", "Quesadilla" };
		int [] appetizerprice1 = {0,5,6,4,5,0};
		JComboBox appetizer2 = new JComboBox(appetizer3);
		appetizer2.setSelectedIndex(-1);
		appetizer2.setBounds (140, 75, 150, 25);
		menu.add(appetizer2);
		JLabel mainCourse = new JLabel("Main Course:");
		mainCourse.setBounds (40, 115, 100, 25);
		menu.add(mainCourse);
		String[] mainCourse3 = {"T-Bone Steak", "Pizza", "Chicken and Veg", "Salmon with Spinach"};
		int [] maincourseprice1 = {0,15,16,14,15,0};
		JComboBox mainCourse2 = new JComboBox(mainCourse3);
		mainCourse2.setSelectedIndex(-1);
		mainCourse2.setBounds (140, 115, 150, 25);
		menu.add(mainCourse2);
		JLabel dessert = new JLabel("Dessert:");
		dessert.setBounds (40, 155, 100, 25);
		menu.add(dessert);
		String[] dessert3 = {"Lava Cake", "Ice Cream", "Fruits", "Carrot Cake"};
		int [] dessertprince1 = {0,9,10,8,7,0};
		JComboBox dessert2 = new JComboBox(dessert3);
		dessert2.setSelectedIndex(-1);
		dessert2.setBounds (140, 155, 150, 25);
		menu.add(dessert2);
		
			
		//Adds calculations fields
        JLabel subtotal = new JLabel("Subtotal:");
		subtotal.setBounds (70, 425, 100, 25);
		add(subtotal);
		JTextField subtotal2 = new JTextField();
		subtotal2.setBounds (140, 425, 100, 25);
		subtotal2.setEditable(false);
		add(subtotal2);
		JLabel tax = new JLabel("Tax:");
		tax.setBounds (70, 455, 100, 25);
		add(tax);
		JTextField tax2 = new JTextField();
		tax2.setBounds (140, 455, 100, 25);
		tax2.setEditable(false);
		add(tax2);
		JLabel total = new JLabel("Total:");
		total.setBounds (70, 485, 100, 25);
		add(total);
		JTextField total2 = new JTextField();
		total2.setBounds (140, 485, 100, 25);
		total2.setEditable(false);
		add(total2);
		

		//Adds the button to calculate the bill
				JButton calculate = new JButton("Calculate Bill");
				calculate.setBounds(135,375,110,25);
		        add(calculate);
		        
		        
		        beverage2.addItemListener(new ItemListener() {
		            public void itemStateChanged(ItemEvent e) {
		                if(e.getStateChange() == ItemEvent.SELECTED){
		                	if (e.getItem() == "Beer"){
		                		setBeveragefinalprice(5);
		                	} else if (e.getItem() == "Wine"){
		                		setBeveragefinalprice(6);
		                	} else if (e.getItem()== "7 Up"){
		                		setBeveragefinalprice(4);
		                	} else if (e.getItem()== "Juice"){
		                		setBeveragefinalprice(5);
		                	} else {
		                		setBeveragefinalprice(0);
		                	}
		                }  	
		            }
		        });
		        mainCourse2.addItemListener(new ItemListener() {
		            public void itemStateChanged(ItemEvent e) {
		                if(e.getStateChange() == ItemEvent.SELECTED){
		                	if (e.getItem() == "T-Bone Steak"){
		                		setMaincoursefinalprice(22);
		                	} else if (e.getItem() == "Pizza"){
		                		setMaincoursefinalprice(16);
		                	} else if (e.getItem()== "Chicken and Veg"){
		                		setMaincoursefinalprice(18);
		                	} else if (e.getItem()== "Salmon with Spinach"){
		                		setMaincoursefinalprice(19);
		                	} else {
		                		setMaincoursefinalprice(0);
		                	}
		                }  	
		            }
		        });
		        appetizer2.addItemListener(new ItemListener() {
		            public void itemStateChanged(ItemEvent e) {
		                if(e.getStateChange() == ItemEvent.SELECTED){
		                	if (e.getItem() == "Combo Plater"){
		                		setApetizerfinalprice(14);
		                	} else if (e.getItem() == "Nachos"){
		                		setApetizerfinalprice(12);
		                	} else if (e.getItem()== "Pan Fried Cheese"){
		                		setApetizerfinalprice(9);
		                	} else if (e.getItem()== "Quesadilla"){
		                		setApetizerfinalprice(10);
		                	} else {
		                		setApetizerfinalprice(0);
		                	}
		                }  	
		            }
		        });
		        dessert2.addItemListener(new ItemListener() {
		            public void itemStateChanged(ItemEvent e) {
		                if(e.getStateChange() == ItemEvent.SELECTED){
		                	if (e.getItem() == "Lava Cake"){
		                		setDessertfinalprice(22);
		                	} else if (e.getItem() == "Ice Cream"){
		                		setDessertfinalprice(16);
		                	} else if (e.getItem()== "Fruits"){
		                		setDessertfinalprice(18);
		                	} else if (e.getItem()== "Carrot Cake"){
		                		setDessertfinalprice(19);
		                	} else {
		                		setDessertfinalprice(0);
		                	}
		                }  	
		            }
		        });
		        
		        

            setVisible(true);
		    }     		


public void actionPerformed(ActionEvent e){  

  
    }  
}  


