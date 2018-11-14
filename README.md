# IIT-sim-game
/* main program start here */
Program.java
import javax.swing.JFrame;
public class Program {
	public static void main(String[] args){
		JFrame f = new JFrame();
		Second s = new Second();
		f.add(s);
		f.setVisible(true);
		f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		f.setSize(800, 600);
	}
}

/* classes start here */
Second.java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.awt.geom.*;

public class Second extends JPanel implements ActionListener, KeyListener {
	
	Timer t = new Timer(5, this);
	double x = 0, y = 0, velx = 0, vely = 0;
	
	public Second(){
			t.start();
			addKeyListener(this);
			setFocusable(true);
			setFocusTraversalKeysEnabled(false);
	}
	
	public void paintComponent(Graphics g){
		super.paintComponent(g);
		Graphics2D g2 = (Graphics2D) g;
		g2.fill(new Ellipse2D.Double(x, y, 40, 40));
	}
	
	public void actionPerformed(ActionEvent e){
		repaint();
		x += velx;
		y += vely;
	}
	
	public void up(){
		vely = -2;
		velx = 0;
	}
	public void down(){
		vely = 2;
		velx = 0;
	}
	public void left(){
		vely = 0;
		velx = -2;
	}
	public void right(){
		vely = 0;
		velx = 2;
	}
	public void stop(){
		vely = 0;
		velx = 0;
	}
	
	public void keyPressed(KeyEvent e){
		int code = e.getKeyCode();
		if (code == KeyEvent.VK_UP){
			up();
		}
		if (code == KeyEvent.VK_DOWN){
			down();
		}
		if (code == KeyEvent.VK_LEFT){
			left();
		}
		if (code == KeyEvent.VK_RIGHT){
			right();
		}
	}
	
	public void keyTyped(KeyEvent e){
		
	}
	public void keyReleased(KeyEvent e){
		int code = e.getKeyCode();
		if (code == KeyEvent.VK_UP ||
			code == KeyEvent.VK_DOWN ||
			code == KeyEvent.VK_LEFT ||
			code == KeyEvent.VK_RIGHT ){
			stop();
		}
	}
}
