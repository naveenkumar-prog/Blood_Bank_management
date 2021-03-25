# Blood_Bank_management

LOGIN FORM:
package login1;
import register.*;
import user.*;
import admin.*;
import javax.swing.*;
import java.awt.Font;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import java.sql.*;
public class Login1a extends JFrame{
    JLabel l1,l2,l3,l4,l11;
    JTextField t1,t11;
    JPasswordField t2;
    JButton b1,b2;
    Login1()
    {
        Font f=new Font("Arial",Font.BOLD,24);
        setTitle("Login Form");
        l1=new JLabel("LOGIN PAGE");
        l1.setFont(f);
        l11=new JLabel("USERID:");
        t11=new JTextField();
        l2=new JLabel("USERNAME:");
        t1=new JTextField();
        l3=new JLabel("PASSWORD:");
        t2=new JPasswordField();
        b1=new JButton("LOGIN");
        b2=new JButton("REGISTER");
        l4=new JLabel("*Register if You Do not Have a account");
        l1.setBounds(200,40,200,40);
        l11.setBounds(200,80,100,20);
        t11.setBounds(200,100,200,30);
        l2.setBounds(200,140,100,20);
        t1.setBounds(200,160,200,30);
        l3.setBounds(200,190,100,20);
        t2.setBounds(200,210,200,30);
        b1.setBounds(200,260,100,30);
        b2.setBounds(400,260,100,30);
        l4.setBounds(200,300,300, 30);
        add(l1);
        add(l11);
        add(t11);
        add(l2);
        add(t1);
        add(l3);
        add(t2);
        add(b1);
        add(b2);
        add(l4);
        setLayout(null);
        setVisible(true);
        setSize(600,600);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        b1.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
                String i1 =  t11.getText();
                String s1 = t1.getText();  
                String s2 = t2.getText();
                try
                {
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3307/login","root","");
                    String sql = "Select * from userdetail where user_id=? and username=? and password=? ";
                    PreparedStatement st = con.prepareStatement(sql);
                    st.setString(1, i1);
                    st.setString(2, s1);
                    st.setString(3, s2);
                    ResultSet rs = st.executeQuery();
                    if(rs.next())
                    {
                        JOptionPane.showMessageDialog(null, "AcessGranted-welcome");
                    }
                    else
                    {
                        JOptionPane.showMessageDialog(null, "AcessDenied-userid or username or password donot matches");
                        t11.setText("");
                        t1.setText("");
                        t2.setText("");
                    }
                    String name = rs.getString("username");
                    if("admin".equals(name))
                    {
                        Admin ob = new Admin();
                    }
                    else
                    {
                        User ob1 = new User();
                    }
                    st.close();
                    con.close();
                }
                catch(Exception e1)
                {
                    System.out.println(e1);
                }
            }
        });
        b2.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
               register ob = new register();
            }
        });
    }
    public static void main(String[] args) {
        Login1 obj = new Login1();
        
    }
    
}

REGISTER FORM:
package register;
import javax.swing.*;  
import java.awt.*;   
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.*;
    public class register extends JFrame 
    {  
        JLabel l1, l2, l3, l4, l5, l6, l7, l8,il1;  
        JTextField tf1, tf2,tf5 , tf7,it1;
        JRadioButton r1,r2;
        Choice c5,c6;
        JButton btn1, btn2;  
        JPasswordField p1,p2;  
        public register()  
        {  
            setVisible(true);  
            setSize(700, 700);  
            setLayout(null);  
            setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);  
            setTitle("Registration Form For New user");  
            l1 = new JLabel("Registration Form");  
            Font f=new Font("Arial",Font.BOLD,24); 
            l1.setFont(f);
            il1 = new JLabel("UserId:");
            l2 = new JLabel("UserName:");  
            l3 = new JLabel("Email-ID:");  
            l4 = new JLabel("Create Passowrd:");  
            l5 = new JLabel("Confirm Password:");  
            l6 = new JLabel("Date of birth:");  
            l7 = new JLabel("Gender:");  
            l8 = new JLabel("Phone No:");  
            it1 = new JTextField();
            tf1 = new JTextField();  
            tf2 = new JTextField();  
            p1 = new JPasswordField();  
            p2 = new JPasswordField();  
            c5 = new Choice();
            c6 = new Choice(); 
            tf5 = new JTextField();
            r1 = new JRadioButton("Male");  
            r2 = new JRadioButton("Female");  
            tf7 = new JTextField();  
            btn1 = new JButton("Submit");  
            btn2 = new JButton("Clear"); 
            l1.setBounds(80, 30, 400, 30);
            il1.setBounds(80,70,200,30);
            l2.setBounds(80, 110, 200, 30);  
            l3.setBounds(80, 150, 200, 30);  
            l4.setBounds(80, 190, 200, 30);  
            l5.setBounds(80, 230, 200, 30);  
            l6.setBounds(80, 270, 200, 30);  
            l7.setBounds(80, 310, 200, 30);  
            l8.setBounds(80, 350, 200, 30);  
            it1.setBounds(300,70,200,30);
            tf1.setBounds(300, 110, 200, 30);  
            tf2.setBounds(300, 150, 200, 30);  
            p1.setBounds(300, 190, 200, 30);  
            p2.setBounds(300, 230, 200, 30);  
            c5.setBounds(300, 270, 40, 30); 
            c5.add("1");c5.add("2");c5.add("1");c5.add("3");c5.add("4");c5.add("5");c5.add("6");c5.add("7");c5.add("8");c5.add("9");c5.add("10");
            c5.add("11");c5.add("12");c5.add("13");c5.add("14");c5.add("15");c5.add("16");c5.add("17");c5.add("18");c5.add("19");c5.add("20");c5.add("21");
            c5.add("21");c5.add("22");c5.add("23");c5.add("24");c5.add("25");c5.add("26");c5.add("27");c5.add("28");c5.add("29");c5.add("30");c5.add("31");
            c6.setBounds(350, 270, 40, 30);
            c6.add("Jan");c6.add("Feb");c6.add("Mar");c6.add("Apr");c6.add("May");c6.add("Jun");c6.add("Jul");c6.add("Aug");c6.add("Sep");c6.add("Oct");c6.add("Nov");c6.add("Dec");
            tf5.setBounds(400, 270, 60, 22);
            r1.setBounds(300, 310, 100, 30);
            r2.setBounds(400, 310, 200, 30);
            tf7.setBounds(300, 350, 200, 30);  
            btn1.setBounds(50, 390, 100, 30);  
            btn2.setBounds(170, 390, 100, 30);  
            add(l1); 
            add(il1);
            add(it1);
            add(l2);  
            add(tf1);  
            add(l3);  
            add(tf2);  
            add(l4);  
            add(p1);  
            add(l5);  
            add(p2);  
            add(l6);  
            add(c5);
            add(c6);
            add(tf5);
            add(l7);  
            add(r1);
            add(r2);  
            add(l8);  
            add(tf7);  
            add(btn1);  
            add(btn2); 
            btn1.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
               String id=it1.getText();
               String uname=tf1.getText();
               String email=tf2.getText();
               String pd=p1.getText();
               String cpd=p2.getText();
               String pno=tf7.getText();
               int check=1; 
               if(id.equals(""))
               {
                    JOptionPane.showMessageDialog(null, "ID-cannot be empty");
                    check=0;
               }
               if(uname.equals(""))
               {
                   JOptionPane.showMessageDialog(null, "USERNAME-cannot be empty");
                   check=0;
               }
               String eid1="^[A-Z0-9a-z._%+-]+@[A-Z0-9a-z.-]+\\.[a-z]{2,30}$";
               if(email.matches(eid1))
               {
               }
               else
               {
                   JOptionPane.showMessageDialog(null, "INVALID-Email");
                   tf2.setText("");
                   check=0;
               }
               if(pd.equals(""))
               {
                   JOptionPane.showMessageDialog(null, "PASSWORD-cannot be empty");
                   check=0;
               }
               String pd1="^[a-z0-9]{8}$";
               if(pd.matches(pd1))
               {
                   JOptionPane.showMessageDialog(null, "PASSWORD-IS STRONG");
               }
               else
               {
                   JOptionPane.showMessageDialog(null, "WEAK PASSWORD");
                   p1.setText("");
                   p2.setText("");
                   check=0;
               }
               if(cpd.equals(pd))
               {
                   
               }
               else
               {
                   JOptionPane.showMessageDialog(null, "PASSWORD DO NOT MATCH");
                   p2.setText("");
                   check=0;
               }
               String mb1="[0-9]{9}";
               if(pno.matches(mb1))
               {
                           
               } 
               else 
               {
                  JOptionPane.showMessageDialog(null, "INVAILD-PHONE NUMBER");
                  tf7.setText("");
                  check=0;
               }
               if(check==1)
               {
                try
                {
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection con= DriverManager.getConnection("jdbc:mysql://localhost:3307/login","root","");
                    String sql = "insert into  userdetail values(?,?,?)";
                    String sql1 ="insert into  register values(?,?,?,?,?)";
                    PreparedStatement st = con.prepareStatement(sql);
                    PreparedStatement st1 = con.prepareStatement(sql1);
                    st.setString(1, id);
                    st.setString(2, uname);
                    st.setString(3, pd);
                    st1.setString(1, id);
                    st1.setString(2, uname);
                    st1.setString(3, email);
                    st1.setString(4, pd);
                    st1.setString(5, pno);
                    st.executeUpdate();
                    st1.executeUpdate();
                    JOptionPane.showMessageDialog(null, "REGISTERED SUCCESSFULLY");
                    st.close();
                    st1.close();
                    con.close();
                }
                catch(Exception e1)
                {
                    System.out.println(e1);
                }
               }
            }
            });
            btn2.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
               it1.setText("");
               tf1.setText("");
               tf2.setText("");
               p1.setText("");
               p2.setText("");
               tf7.setText("");
            }
        });
        }      
    }
      
USER PORTAL:
package user;
import donate.*;
import get.*;
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
public class User extends JFrame
{
    JLabel l1,l2,l3;
    JButton b1,b2;
    public User()
    {
        Font f=new Font("Arial",Font.BOLD,24);
        Font f1=new Font("Arial",Font.BOLD, 18);
        setTitle("User Portal");
        l1=new JLabel("USERPORTAL-BLOOD BANK MANAGEMENT SYSTEM");
        l1.setFont(f);
        l1.setBounds(80,40,1000,40);
        l2=new JLabel("*Would you like to donate blood? ");
        l2.setFont(f1);
        l2.setBounds(80,150,1000,40);
        l3=new JLabel("*Would you like to get blood? ");
        l3.setFont(f1);
        l3.setBounds(80,320,1000,40);
        b1=new JButton("DONATE BLOOD");
        b2=new JButton("RECEIVE BLOOD");
        b1.setBounds(80,200,200,40);
        b2.setBounds(80,370,200,40);
        add(l1);
        add(l2);
        add(l3);
        add(b1);
        add(b2);
        setLayout(null);
        setVisible(true);
        setSize(800,800);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        b1.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
                Donate obj = new Donate();
            }
        });
        b2.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
               Get obj1 = new Get();
            }
        });

    }
}
RECEIVER FORM:
package get;
import  bloodmain.*;
import java.awt.*;
import java.util.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.*;
import javax.swing.*;
public class Get extends JFrame {
    public Get()
    {
        JLabel lt1,lb1,lb2,lb3,lb4,lb5;
        JTextField t1,t2,t3,t4,t5;
        JButton bt1,bt2,b1;
        setTitle("Receive portal");
        lt1 = new JLabel("RECEIVE PORTAL");  
        Font f=new Font("Arial",Font.BOLD,24); 
        lt1.setFont(f);
        lb1=new JLabel("USERNAME:");
        t1 = new JTextField();
        lb2=new JLabel("BLOODGROUP:");
        t2=new JTextField();
        lb3=new JLabel("OUANTITY(ML):");
        t3=new JTextField();
        lb4=new JLabel("GENDER:");
        t4=new JTextField();
        lb5=new JLabel("AGE:");
        t5=new JTextField();
        bt1=new JButton("RECIVE");
        bt2=new JButton("CLEAR");
        b1=new JButton("WOULD YOU LIKE TO SEE BLOOD AVILABLE IN BANK");
        b1.setBounds(100,40,400,30);
        lt1.setBounds(100,80,300,20);
        lb1.setBounds(100,120,100,20);
        t1.setBounds(200,120,200,30);
        lb2.setBounds(100,160,100,20);
        t2.setBounds(200,160,200,30);
        lb3.setBounds(100,200,200,20);
        t3.setBounds(220,200,200,30);
        lb4.setBounds(100,240,100,20);
        t4.setBounds(200,240,200,30);
        lb5.setBounds(100,280,100,20);
        t5.setBounds(200,280,200,30);
        bt1.setBounds(100,330,100,30);
        bt2.setBounds(300,330,100,30);
        add(b1);
        add(lt1);
        add(lb1);
        add(t1);
        add(lb2);
        add(t2);
        add(lb3);
        add(t3);
        add(lb4);
        add(t4);
        add(lb5);
        add(t5);
        add(bt1);
        add(bt2);
        setLayout(null);
        setVisible(true);
        setSize(600,600);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
         bt1.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
               String uname=t1.getText();
               String bgrp=t2.getText();
               String qty=t3.getText();
               String g=t4.getText();
               String age=t5.getText();
               int check=1;
               if(uname.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Username Cannot Be empty");
                   check=0;
               }
               if(bgrp.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Blood Group Cannot Be empty");
                   check=0;
               }
               if(bgrp.equals("A+")||bgrp.equals("B+")||bgrp.equals("O+")||bgrp.equals("AB+")||bgrp.equals("AB-")||bgrp.equals("A-")||bgrp.equals("B-")||bgrp.equals("O-"))
               {
                   check=1;
               }
               else
               {
                   JOptionPane.showMessageDialog(null,"Invaild Blood Group");
                   check=0;
                   t2.setText("");
               }
               if(qty.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Quantity Cannot Be empty");
                   check=0;
               }
               if(g.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Gender Cannot Be empty");
                   check=0;
               }
               if(age.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Age Cannot Be empty");
                   check=0;
               }
               if(check==1)
               {
                   try
                {
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection con= DriverManager.getConnection("jdbc:mysql://localhost:3307/login","root","");
                    String sql = "insert into bloodget values(?,?,?,?,?)";
                    PreparedStatement st = con.prepareStatement(sql);
                    st.setString(1, uname);
                    st.setString(2, bgrp);
                    st.setString(3, qty);
                    st.setString(4, g);
                    st.setString(5, age);
                    st.executeUpdate();
                    JOptionPane.showMessageDialog(null, "RECEIVED-We Are Always Here To Serve You");
                    st.close();
                    con.close();
                }
                catch(Exception e1)
                {
                    System.out.println(e1);
                }
               }
            }
         });
         bt2.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
              t1.setText("");
              t2.setText("");
              t3.setText("");
              t4.setText("");
              t5.setText("");
            }
         });
         b1.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
                Bloodmain ob = new Bloodmain();
            }     
           });
    }
 }

DONOR FORM:
package donate;
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.*;
public class Donate extends JFrame {
    public Donate()
    {
        JLabel lt1,lb1,lb2,lb3,lb4,lb5,lb6,lb7;
        JTextField t1,t2,t3,t4,t5,t6,t7;
        JButton bt1,bt2;
        setTitle("Donation portal");
        lt1 = new JLabel("DONATION PORTAL");  
        Font f=new Font("Arial",Font.BOLD,24); 
        lt1.setFont(f);
        lb1=new JLabel("USERNAME:");
        t1 = new JTextField();
        lb2=new JLabel("BLOODGROUP:");
        t2=new JTextField();
        lb3=new JLabel("OUANTITY(ML):");
        t3=new JTextField();
        lb4=new JLabel("GENDER(M/F):");
        t4=new JTextField();
        lb5=new JLabel("AGE:");
        t5=new JTextField();
        lb6=new JLabel("ARE YOU A DRUGGIE(Y/N)?");
        t6=new JTextField();
        lb7=new JLabel("DO YOU HAVE BLOOD DISEASE(Y/N)?");
        t7=new JTextField();
        bt1=new JButton("DONATE");
        bt2=new JButton("CLEAR");
        lt1.setBounds(100,80,300,20);
        lb1.setBounds(100,120,100,20);
        t1.setBounds(200,120,200,30);
        lb2.setBounds(100,160,100,20);
        t2.setBounds(200,160,200,30);
        lb3.setBounds(100,200,100,20);
        t3.setBounds(200,200,200,30);
        lb4.setBounds(100,240,100,20);
        t4.setBounds(200,240,200,30);
        lb5.setBounds(100,280,100,20);
        t5.setBounds(200,280,200,30);
        lb6.setBounds(100,320,200,20);
        t6.setBounds(250,320,200,30);
        lb7.setBounds(100,370,280,20);
        t7.setBounds(320,370,200,30);
        bt1.setBounds(100,420,100,30);
        bt2.setBounds(300,420,100,30);
        add(lt1);
        add(lb1);
        add(t1);
        add(lb2);
        add(t2);
        add(lb3);
        add(t3);
        add(lb4);
        add(t4);
        add(lb5);
        add(t5);
        add(lb6);
        add(t6);
        add(lb7);
        add(t7);
        add(bt1);
        add(bt2);
        setLayout(null);
        setVisible(true);
        setSize(600,600);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
         bt1.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
               String uname=t1.getText();
               String bgrp=t2.getText();
               String qty=t3.getText();
               String g=t4.getText();
               String age=t5.getText();
               String d=t6.getText();
               String d1=t7.getText();
               int check=1;
               if(uname.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Username Cannot Be empty");
                   check=0;
               }
               if(bgrp.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Blood Group Cannot Be empty");
                   check=0;
               }
               if(bgrp.equals("A+")||bgrp.equals("B+")||bgrp.equals("O+")||bgrp.equals("AB+")||bgrp.equals("AB-")||bgrp.equals("A-")||bgrp.equals("B-")||bgrp.equals("O-"))
               {
                   check=1;
               }
               else
               {
                   JOptionPane.showMessageDialog(null,"Invaild Blood Group");
                   check=0;
                   t2.setText("");
               }
               if(qty.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Quantity Cannot Be empty");
                   check=0;
               }
               if(g.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Gender Cannot Be empty");
                   check=0;
               }
               if(age.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Age Cannot Be empty");
                   check=0;
               }
               if(d.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"This Field Cannot Be empty");
                   check=0;
               }
               if(d.equals("yes")||d.equals("YES"))
               {
                   JOptionPane.showMessageDialog(null,"Sorry,You Cannot donate blood");
                   check=0;
               }
               if(d.equals("no")||d.equals("NO"))
               {
                   check=1;
               }
               if(d1.equals("yes")||d1.equals("YES"))
               {
                   JOptionPane.showMessageDialog(null,"Sorry,You Cannot donate blood");
                   check=0;
               }
               if(d1.equals("no")||d1.equals("NO"))
               {
                   check=1;
               }
               if(check==1)
               {
                try
                {
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection con= DriverManager.getConnection("jdbc:mysql://localhost:3307/login","root","");
                    String sql = "insert into blooddonate values(?,?,?,?,?)";
                    PreparedStatement st = con.prepareStatement(sql);
                    st.setString(1, uname);
                    st.setString(2, bgrp);
                    st.setString(3, qty);
                    st.setString(4, g);
                    st.setString(5, age);
                    st.executeUpdate();
                    JOptionPane.showMessageDialog(null, "DONATED-Thank You For Your contribution");
                    st.close();
                    con.close();
                }
                catch(Exception e1)
                {
                    System.out.println(e1);
                }
               }
               
            }
         });
         bt2.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
              t1.setText("");
              t2.setText("");
              t3.setText("");
              t4.setText("");
              t5.setText("");
            }
         });
    }
}
JTABLE CODE:
package bloodmain;
import javax.swing.*;  
public class Bloodmain extends JFrame { 
    JFrame f;    
    public Bloodmain(){    
    f=new JFrame();    
    String data[][]={ {"A1","A+","20000"},    
                          {"B1","B+","20000"},    
                          {"O1","O+","20000"},
                          {"AB1","AB+","20000"},    
                          {"AB2","AB-","20000"},
                          {"A2","A-","20000"},
                          {"B2","B-","20000"},
                          {"O2","O-","20000"}};    
    String column[]={"BLOOD-ID","BLOOD-GROUP","QUANTITY(ML)"};         
    JTable jt=new JTable(data,column);    
    jt.setBounds(30,40,200,300);          
    JScrollPane sp=new JScrollPane(jt);    
    f.add(sp);          
    f.setSize(300,400);    
    f.setVisible(true);    
}     
}  

ADMIN PORTAL:
package admin;
import bloodmain.*;
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.*;
public class Admin extends JFrame{
    JLabel l1,l2,l3,l4,l5,l6;
    JButton b1,b2,b3,b4,b5;
    JTextField t1,t2;
    public Admin()
    {
        Font f=new Font("Arial",Font.BOLD,24);
        setTitle("Admin Portal");
        Font f1=new Font("Arial",Font.BOLD, 18);
        l1=new JLabel("ADMIN PORTAL-BLOOD BANK MANAGEMENT SYSTEM");
        l1.setFont(f);
        l1.setBounds(80,30,1000,40);
        l2=new JLabel("*view blood avilable in the blood bank? ");
        l2.setFont(f1);
        l2.setBounds(80,100,1000,40);
        b1=new JButton("VIEW");
        b1.setBounds(80,150,200,40);
        l3=new JLabel("*blood donated into blood bank? ");
        t1=new JTextField();
        l5=new JLabel();
        l3.setFont(f1);
        l3.setBounds(80,250,1000,40);
        b2=new JButton("VIEW");
        b4=new JButton("CLEAR");
        b5=new JButton("CLEAR");
        t1.setBounds(80,300,150,30);
        l5.setBounds(80,350,800,40);
        b2.setBounds(80,390,200,40);
        b4.setBounds(300,390,200,40);
        l4=new JLabel("*blood recived from blood bank? ");
        t2=new JTextField();
        l6=new JLabel();
        l4.setFont(f1);
        l4.setBounds(80,450,1000,40);
        b3=new JButton("VIEW");
        t2.setBounds(80,490,150,30);
        l6.setBounds(80,530,800,40);
        b3.setBounds(80,570,200,40);
        b5.setBounds(300,570,200,40);
        add(l1);
        add(l2);
        add(b1);
        add(l3);
        add(t1);
        add(l5);
        add(b2);
        add(b4);
        add(l4);
        add(t2);
        add(l6);
        add(b3);
        add(b5);
        setLayout(null);
        setVisible(true);
        setSize(800,800);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        b1.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
                Bloodmain ob = new Bloodmain();
            }     
           });
        b2.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
                String bgrp=t1.getText();
                int qty=0;
                int check=1;
                if(bgrp.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Blood Group Cannot Be empty");
                   check=0;
               }
               if(bgrp.equals("A+")||bgrp.equals("B+")||bgrp.equals("O+")||bgrp.equals("AB+")||bgrp.equals("AB-")||bgrp.equals("A-")||bgrp.equals("B-")||bgrp.equals("O-"))
               {
                   check=1;
               }
               else
               {
                   JOptionPane.showMessageDialog(null,"Invaild Blood Group");
                   check=0;
                   t1.setText("");
               }
               if(check==1)
               {
                try
                {
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection con= DriverManager.getConnection("jdbc:mysql://localhost:3307/login","root","");
                    String sql="select * from blooddonate";
                    Statement st = con.createStatement();
                    ResultSet rs = st.executeQuery(sql);
                    while(rs.next())
                    {
                    String bgrp1=rs.getString(2);
                    if(bgrp1.equals(bgrp))
                        {
                            qty+=Integer.parseInt(rs.getString(3));
                        }
                    }
                    l5.setText(String.valueOf(qty)+"ml of "+bgrp+" blood is donated to blood bank");
                    st.close();
                    con.close();
                }
                catch(Exception e1)
                {
                    System.out.println(e1);
                }
               }
                
            }     
           });
        b3.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
                String bgrp=t2.getText();
                int qty=0;
                int check=1;
                if(bgrp.equals(""))
               {
                   JOptionPane.showMessageDialog(null,"Blood Group Cannot Be empty");
                   check=0;
               }
               if(bgrp.equals("A+")||bgrp.equals("B+")||bgrp.equals("O+")||bgrp.equals("AB+")||bgrp.equals("AB-")||bgrp.equals("A-")||bgrp.equals("B-")||bgrp.equals("O-"))
               {
                   check=1;
               }
               else
               {
                   JOptionPane.showMessageDialog(null,"Invaild Blood Group");
                   check=0;
                   t2.setText("");
               }
               if(check==1)
               {
                try
                {
                    Class.forName("com.mysql.jdbc.Driver");
                    Connection con= DriverManager.getConnection("jdbc:mysql://localhost:3307/login","root","");
                    String sql="select * from bloodget";
                    Statement st = con.createStatement();
                    ResultSet rs = st.executeQuery(sql);
                    while(rs.next())
                    {
                    String bgrp1=rs.getString(2);
                    if(bgrp1.equals(bgrp))
                        {
                            qty+=Integer.parseInt(rs.getString(3));
                        }
                    }
                    l6.setText(String.valueOf(qty)+"ml of "+bgrp+" blood is received from blood bank");
                    st.close();
                    con.close();
                }
                catch(Exception e1)
                {
                    System.out.println(e1);
                }
            } 
            }
           });
        b4.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
                t1.setText("");
                l5.setText("");
            }     
           });
        b5.addActionListener(new ActionListener(){
            @Override
            public void actionPerformed(ActionEvent e) {
                t2.setText("");
                l6.setText("");
            }     
           });
    }
