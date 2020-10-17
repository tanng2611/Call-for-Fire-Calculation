# Call for Fire Calculation
import java.awt.Color;
import java.awt.EventQueue;
import java.awt.Font;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.text.DecimalFormat;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JScrollPane;
import javax.swing.JTable;
import javax.swing.JTextField;
import javax.swing.table.DefaultTableModel;

/* New layout
 *  fixed warning textfield: show nothing if not danger close 
 *  history list included
 *  add function for m777 button
 */

public class CFF {

	JFrame frame;
	JTable table;
	JButton btnM119;
	JButton btnM777;
	JLabel lblArtilleryLocation;
	JLabel lblTargetLocation;
	JTextField textALocation;
	JTextField textTLocation;
	JLabel label;
	JButton btnCalculate;
	JLabel lblArtilleryHeight;
	JTextField textArtHeight;
	JLabel lblTargetDist;
	JTextField textTargetDist;
	JLabel lblDistImpact;
	JTextField textRange;
	JLabel lblDegree;
	JTextField textDegree;
	JLabel lblDirection;
	JTextField textDirection;
	JLabel lblMaxHeight;
	JTextField textMaxHeight;
	JLabel lblTimeImpact;
	JTextField textTimeImpact;
	JLabel lblWarning;
	JTextField textWarning;
	JLabel lblAllyLocation;
	JTextField textAllyLocaction;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					CFF window = new CFF();
					window.frame.setVisible(true);

				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the application.
	 */
	public CFF() {
		initialize();
	}

	/**
	 * Initialize the contents of the frame.
	 */
	private void initialize() {
		frame = new JFrame();
		frame.setTitle("Call for Fire by Eric Nguyen v1.4");
		frame.setBounds(100, 100, 1326, 765);
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.getContentPane().setLayout(null);

		btnM119 = new JButton("M119");
		btnM119.setFont(new Font("Tahoma", Font.PLAIN, 14));
		btnM119.addActionListener(new BtnM119ActionListener());
		btnM119.setBounds(10, 191, 120, 30);
		frame.getContentPane().add(btnM119);

		btnM777 = new JButton("M777");
		btnM777.addActionListener(new BtnM777ActionListener());
		btnM777.setFont(new Font("Tahoma", Font.PLAIN, 14));
		btnM777.setBounds(140, 191, 120, 30);
		frame.getContentPane().add(btnM777);

		lblArtilleryLocation = new JLabel("Artillery Location (6 Digits)");
		lblArtilleryLocation.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblArtilleryLocation.setBounds(10, 11, 167, 30);
		frame.getContentPane().add(lblArtilleryLocation);

		textALocation = new JTextField();
		textALocation.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textALocation.setBounds(180, 12, 140, 30);
		frame.getContentPane().add(textALocation);
		textALocation.setColumns(10);

		textTLocation = new JTextField();
		textTLocation.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textTLocation.setColumns(10);
		textTLocation.setBounds(180, 52, 140, 30);
		frame.getContentPane().add(textTLocation);

		lblTargetLocation = new JLabel("Target Location (6 Digits)");
		lblTargetLocation.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblTargetLocation.setBounds(10, 51, 167, 30);
		frame.getContentPane().add(lblTargetLocation);

		lblArtilleryHeight = new JLabel("Artillery Height (meter)");
		lblArtilleryHeight.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblArtilleryHeight.setBounds(10, 92, 145, 30);
		frame.getContentPane().add(lblArtilleryHeight);

		textArtHeight = new JTextField();
		textArtHeight.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textArtHeight.setBounds(180, 93, 140, 30);
		frame.getContentPane().add(textArtHeight);
		textArtHeight.setColumns(10);

		lblTargetDist = new JLabel("Distance of Target (meter)");
		lblTargetDist.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblTargetDist.setBounds(10, 579, 160, 30);
		frame.getContentPane().add(lblTargetDist);

		textTargetDist = new JTextField();
		textTargetDist.setEditable(false);
		textTargetDist.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textTargetDist.setText("");
		textTargetDist.setBounds(10, 620, 140, 30);
		frame.getContentPane().add(textTargetDist);
		textTargetDist.setColumns(10);

		lblDistImpact = new JLabel("Distance Impact (meter)");
		lblDistImpact.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblDistImpact.setBounds(355, 463, 160, 30);
		frame.getContentPane().add(lblDistImpact);

		textRange = new JTextField();
		textRange.setEditable(false);
		textRange.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textRange.setBounds(355, 498, 140, 30);
		frame.getContentPane().add(textRange);
		textRange.setColumns(10);

		lblDegree = new JLabel("Degree");
		lblDegree.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblDegree.setBounds(10, 463, 160, 30);
		frame.getContentPane().add(lblDegree);

		textDegree = new JTextField();
		textDegree.setEditable(false);
		textDegree.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textDegree.setColumns(10);
		textDegree.setBounds(10, 498, 140, 30);
		frame.getContentPane().add(textDegree);

		lblDirection = new JLabel("Direction");
		lblDirection.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblDirection.setBounds(187, 463, 160, 30);
		frame.getContentPane().add(lblDirection);

		textDirection = new JTextField();
		textDirection.setEditable(false);
		textDirection.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textDirection.setColumns(10);
		textDirection.setBounds(187, 498, 140, 30);
		frame.getContentPane().add(textDirection);

		lblMaxHeight = new JLabel("Max Height (meter)");
		lblMaxHeight.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblMaxHeight.setBounds(187, 579, 160, 30);
		frame.getContentPane().add(lblMaxHeight);

		textMaxHeight = new JTextField();
		textMaxHeight.setEditable(false);
		textMaxHeight.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textMaxHeight.setColumns(10);
		textMaxHeight.setBounds(187, 620, 140, 30);
		frame.getContentPane().add(textMaxHeight);

		lblTimeImpact = new JLabel("Time Impact (seconds)");
		lblTimeImpact.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblTimeImpact.setBounds(355, 579, 160, 30);
		frame.getContentPane().add(lblTimeImpact);

		textTimeImpact = new JTextField();
		textTimeImpact.setEditable(false);
		textTimeImpact.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textTimeImpact.setColumns(10);
		textTimeImpact.setBounds(355, 620, 140, 30);
		frame.getContentPane().add(textTimeImpact);

		lblWarning = new JLabel("WARNING");
		lblWarning.setForeground(Color.RED);
		lblWarning.setBackground(Color.RED);
		lblWarning.setFont(new Font("Tahoma", Font.PLAIN, 17));
		lblWarning.setBounds(10, 422, 160, 30);
		frame.getContentPane().add(lblWarning);

		textWarning = new JTextField();
		textWarning.setFont(new Font("Tahoma", Font.PLAIN, 20));
		textWarning.setEditable(false);
		textWarning.setForeground(Color.RED);
		textWarning.setBounds(115, 417, 180, 40);
		frame.getContentPane().add(textWarning);
		textWarning.setColumns(10);

		lblAllyLocation = new JLabel("Ally Location (6 Digits)");
		lblAllyLocation.setFont(new Font("Tahoma", Font.PLAIN, 14));
		lblAllyLocation.setBounds(10, 136, 160, 30);
		frame.getContentPane().add(lblAllyLocation);

		textAllyLocaction = new JTextField();
		textAllyLocaction.setFont(new Font("Tahoma", Font.PLAIN, 14));
		textAllyLocaction.setColumns(10);
		textAllyLocaction.setBounds(180, 137, 140, 30);
		frame.getContentPane().add(textAllyLocaction);

		table = new JTable();
		table.setModel(new DefaultTableModel(new Object[][] {},
				new String[] { "Artillery Loc", "Target Loc", "Location Height (m)", "Friendly Trp Loc", "Degree",
						"Direction (m)", "Dist Impact (m)", "Dist of Target (m)", "Max Height (m)",
						"Time Impact (s)" }));
		table.setFont(new Font("Tahoma", Font.PLAIN, 13));
		table.setBounds(636, 11, 477, 338);
		frame.getContentPane().add(table);

		JScrollPane sp = new JScrollPane(table);
		frame.getContentPane().add(sp);
		sp.setBounds(325, 11, 987, 438);
	}

	public void actionPerformed(ActionEvent event) {
		if (event.getSource() == btnM119) {
			btnM119.setEnabled(false);
			btnM777.setEnabled(true);
		}
		if (event.getSource() == btnM777) {
			btnM777.setEnabled(false);
			btnM119.setEnabled(true);
		}

	}

	private class BtnM119ActionListener implements ActionListener {
		public void actionPerformed(ActionEvent e) {

			double v = 708;
			double maxrange = 17500;

			String a1 = textALocation.getText(); // Receive input
			String b1 = textTLocation.getText();
			String c1 = textArtHeight.getText();
			String d1 = textAllyLocaction.getText();

			double loc1 = Double.parseDouble(a1);
			double loc2 = Double.parseDouble(b1);
			double h = Double.parseDouble(c1);
			double loc3 = Double.parseDouble(d1);

			int grid1 = (int) loc1;
			int grid2 = (int) loc2;
			int grid3 = (int) loc3;

			// convert int grid to string
			String g1_str = Integer.toString(grid1);
			String g2_str = Integer.toString(grid2);

			// take out specific number and convert back to int
			int x1 = Integer.parseInt(g1_str.substring(0, 3));
			int x2 = Integer.parseInt(g2_str.substring(0, 3));
			int y1 = Integer.parseInt(g1_str.substring(3));
			int y2 = Integer.parseInt(g2_str.substring(3));

			// calculate target distance
			double x = Math.abs(x1 - x2) * 100;
			double y = Math.abs(y1 - y2) * 100;
			Double d = Math.hypot(x, y) + Math.hypot(x, y) * 0.04;

			// calculate distance b/w allied troops and target
			String g3_str = Integer.toString(grid3);
			int ax = Integer.parseInt(g3_str.substring(0, 3));
			int ay = Integer.parseInt(g3_str.substring(3));

			double axx = Math.abs(ax - x1) * 100;
			double ayy = Math.abs(ay - y1) * 100;
			Double allydist = Math.hypot(axx, ayy) + Math.hypot(axx, ayy) * 0.04;

			DecimalFormat df = new DecimalFormat("#.##");

			if (d > maxrange) {
				System.out.println("Out of Range");
				System.out.println("Max Range: " + df.format(maxrange) + " meters");
				System.out.println("Distance of Target: " + df.format(d) + " meters");
				textWarning.setText("" + "OUT OF RANGE");
			}
			// find a in rad
			double aValue = Math.asin(d * 9.81 / (v * v)) / 2;
			// double cosValue = Math.cos(radians);

			// degree up and down
			double an = Math.toDegrees(aValue);

			// sin() method to get the sine value
			double sina = Math.sin(aValue);
			double cosa = Math.cos(aValue);

			// get triangle side by x1 and y2 point
			int x3 = x1;
			int y3 = y2;
			double xx = Math.abs(x1 - x3) * 100;
			double yy = Math.abs(y1 - y3) * 100;
			Double dist2 = Math.hypot(xx, yy) + Math.hypot(xx, yy) * 0.04;

			// Calculate angle beta to shift in rad
			double beta = Math.acos(dist2 / d);

			// convert rad to mil
			double betamil = beta * 1000;

			// convert mil to meter
			double betameter = betamil * 0.0000254;

			// Cal: vy, vx
			double vy = v * sina;
			double vx = v * cosa;

			// Max Height
			double hm = vy * vy / (2 * 9.81) + h;

			// Time flight
			double tr = vy / 9.81;
			double tf = Math.sqrt(2 * hm / 9.81);

			double tfl = tr + tf;

			// Range
			double range = vx * tfl;

			// danger close
			double dangerclose = range - allydist;

			if (dangerclose <= 600 && dangerclose >= -600) {
				System.out.println("DANGER CLOSE");
				textWarning.setText("" + "DANGER CLOSE");
			} else {
				textWarning.setText("");
			}

			System.out.println("Degree " + df.format(an) + "*");

			// move left or right
			if (x1 > x2) {
				System.out.println("Left " + df.format(betameter) + " meter");
				textDirection.setText("" + "Left " + df.format(betameter) + " m");
			}
			if (x1 < x2) {
				System.out.println("Right " + df.format(betameter) + " meter");
				textDirection.setText("" + "Right " + df.format(betameter) + " m");
			}

			// add row to table
			Object[] row = { a1, b1, c1, d1, an, betameter, range, d, hm, tfl };

			DefaultTableModel model = (DefaultTableModel) table.getModel();

			model.addRow(row);

			System.out.println("Distance Impact: " + df.format(range) + " meters");
			System.out.println("Distance of Target: " + df.format(d) + " meters");
			System.out.println("Max Height: " + df.format(hm) + " meters");
			System.out.println("Time Flight: " + df.format(tfl) + " seconds");
			System.out.println("Distance b/w allied troops and artLoc: " + df.format(allydist) + " meters");

			textDegree.setText("" + df.format(an) + "*");

			textRange.setText("" + df.format(range) + " m");
			textTargetDist.setText("" + df.format(d) + " m");
			textMaxHeight.setText("" + df.format(hm) + " m");
			textTimeImpact.setText("" + df.format(tfl) + " s");

		}
	}

	private class BtnM777ActionListener implements ActionListener {
		public void actionPerformed(ActionEvent e) {
			double v = 827;
			double maxrange = 24700;

			String a1 = textALocation.getText(); // Receive input
			String b1 = textTLocation.getText();
			String c1 = textArtHeight.getText();
			String d1 = textAllyLocaction.getText();

			double loc1 = Double.parseDouble(a1);
			double loc2 = Double.parseDouble(b1);
			double h = Double.parseDouble(c1);
			double loc3 = Double.parseDouble(d1);

			int grid1 = (int) loc1;
			int grid2 = (int) loc2;
			int grid3 = (int) loc3;

			// convert int grid to string
			String g1_str = Integer.toString(grid1);
			String g2_str = Integer.toString(grid2);

			// take out specific number and convert back to int
			int x1 = Integer.parseInt(g1_str.substring(0, 3));
			int x2 = Integer.parseInt(g2_str.substring(0, 3));
			int y1 = Integer.parseInt(g1_str.substring(3));
			int y2 = Integer.parseInt(g2_str.substring(3));

			// calculate target distance
			double x = Math.abs(x1 - x2) * 100;
			double y = Math.abs(y1 - y2) * 100;
			Double d = Math.hypot(x, y) + Math.hypot(x, y) * 0.04;

			// calculate distance b/w allied troops and target
			String g3_str = Integer.toString(grid3);
			int ax = Integer.parseInt(g3_str.substring(0, 3));
			int ay = Integer.parseInt(g3_str.substring(3));

			double axx = Math.abs(ax - x1) * 100;
			double ayy = Math.abs(ay - y1) * 100;
			Double allydist = Math.hypot(axx, ayy) + Math.hypot(axx, ayy) * 0.04;

			DecimalFormat df = new DecimalFormat("#.##");

			if (d > maxrange) {
				System.out.println("Out of Range");
				System.out.println("Max Range: " + df.format(maxrange) + " meters");
				System.out.println("Distance of Target: " + df.format(d) + " meters");
				textWarning.setText("" + "OUT OF RANGE");
			}
			// find a in rad
			double aValue = Math.asin(d * 9.81 / (v * v)) / 2;
			// double cosValue = Math.cos(radians);

			// degree up and down
			double an = Math.toDegrees(aValue);

			// sin() method to get the sine value
			double sina = Math.sin(aValue);
			double cosa = Math.cos(aValue);

			// get triangle side by x1 and y2 point
			int x3 = x1;
			int y3 = y2;
			double xx = Math.abs(x1 - x3) * 100;
			double yy = Math.abs(y1 - y3) * 100;
			Double dist2 = Math.hypot(xx, yy) + Math.hypot(xx, yy) * 0.04;

			// Calculate angle beta to shift in rad
			double beta = Math.acos(dist2 / d);

			// convert rad to mil
			double betamil = beta * 1000;

			// convert mil to meter
			double betameter = betamil * 0.0000254;

			// Cal: vy, vx
			double vy = v * sina;
			double vx = v * cosa;

			// Max Height
			double hm = vy * vy / (2 * 9.81) + h;

			// Time flight
			double tr = vy / 9.81;
			double tf = Math.sqrt(2 * hm / 9.81);

			double tfl = tr + tf;

			// Range
			double range = vx * tfl;

			// danger close
			double dangerclose = range - allydist;

			if (dangerclose <= 600 && dangerclose >= -600) {
				System.out.println("DANGER CLOSE");
				textWarning.setText("" + "DANGER CLOSE");
			}

			System.out.println("Degree " + df.format(an) + "*");

			// move left or right
			if (x1 > x2) {
				System.out.println("Left " + df.format(betameter) + " meter");
				textDirection.setText("" + "Left " + df.format(betameter) + " m");
			}
			if (x1 < x2) {
				System.out.println("Right " + df.format(betameter) + " meter");
				textDirection.setText("" + "Right " + df.format(betameter) + " m");
			}

			// add row to table
			Object[] row = { a1, b1, c1, d1, an, betameter, range, d, hm, tfl };

			DefaultTableModel model = (DefaultTableModel) table.getModel();

			model.addRow(row);

			System.out.println("Distance Impact: " + df.format(range) + " meters");
			System.out.println("Distance of Target: " + df.format(d) + " meters");
			System.out.println("Max Height: " + df.format(hm) + " meters");
			System.out.println("Time Flight: " + df.format(tfl) + " seconds");
			System.out.println("Distance b/w allied troops and artLoc: " + df.format(allydist) + " meters");

			textDegree.setText("" + df.format(an) + "*");

			textRange.setText("" + df.format(range) + " m");
			textTargetDist.setText("" + df.format(d) + " m");
			textMaxHeight.setText("" + df.format(hm) + " m");
			textTimeImpact.setText("" + df.format(tfl) + " s");

		}
	}
}
