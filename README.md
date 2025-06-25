import java.lang.*;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class VendingMachineFrame extends JFrame implements MouseListener, ActionListener {
   ImageIcon img;
    JLabel userLabel, pinLabel, totalPriceLabel, quantityLabel;
    JTextField userTF, quantityTF;
    JPasswordField pinPF;
    JComboBox<String> categoryBox;
    JCheckBox sodaCB, chipsCB, candyCB, sandwichCB, juiceCB, cookiesCB;
    JCheckBox iceCB, giftCB, couponCB;
    JButton buyBtn, exitBtn, totalBtn;
    JPanel panel;
    Font myFont;

    double totalPrice = 0.0;

    final double PRICE_SODA = 2.0;
    final double PRICE_CHIPS = 3.0;
    final double PRICE_CANDY = 1.5;
    final double PRICE_SANDWICH = 4.0;
    final double PRICE_JUICE = 2.5;
    final double PRICE_COOKIES = 3.5;

    public VendingMachineFrame() {
        super("Vending Machine");

        this.setSize(950, 600);
        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        this.setLocationRelativeTo(null);

        myFont = new Font("Arial", Font.BOLD, 22);

        panel = new JPanel();
        panel.setLayout(null);
        panel.setBackground(new Color(207, 240, 255)); // Light sky blue
        this.add(panel);

        JLabel titleLabel = new JLabel("VENDING MACHINE SYSTEM", JLabel.CENTER);
        titleLabel.setBounds(250, 10, 400, 40);
        titleLabel.setFont(new Font("Arial", Font.BOLD, 24));
        panel.add(titleLabel);

        String[] categories = {"Cash", "Credit Card", "Mobile Payment"};
        categoryBox = new JComboBox<>(categories);
        categoryBox.setBounds(90, 70, 150, 25);
        panel.add(categoryBox);

        userLabel = new JLabel("User Name :");
        userLabel.setBounds(100, 120, 200, 30);
        userLabel.setFont(myFont);
        userLabel.setOpaque(true);
        userLabel.setBackground(Color.PINK);
        panel.add(userLabel);

        userTF = new JTextField();
        userTF.setBounds(310, 120, 100, 30);
        userTF.setBackground(Color.CYAN);
        panel.add(userTF);

        pinLabel = new JLabel("PIN Number :");
        pinLabel.setBounds(120, 170, 200, 30);
        panel.add(pinLabel);

        pinPF = new JPasswordField();
        pinPF.setBounds(310, 170, 100, 30);
        panel.add(pinPF);

        quantityLabel = new JLabel("Quantity (each item):");
        quantityLabel.setBounds(120, 210, 180, 30);
        panel.add(quantityLabel);

        quantityTF = new JTextField("1");
        quantityTF.setBounds(310, 210, 100, 30);
        panel.add(quantityTF);

        sodaCB = new JCheckBox("Soda ($2.00)");
        sodaCB.setBounds(450, 70, 150, 30);
        sodaCB.setBackground(Color.ORANGE);
        panel.add(sodaCB);

        chipsCB = new JCheckBox("Chips ($3.00)");
        chipsCB.setBounds(450, 110, 150, 30);
        chipsCB.setBackground(Color.ORANGE);
        panel.add(chipsCB);

        candyCB = new JCheckBox("Candy ($1.50)");
        candyCB.setBounds(450, 150, 150, 30);
        candyCB.setBackground(Color.ORANGE);
        panel.add(candyCB);

        sandwichCB = new JCheckBox("Sandwich ($4.00)");
        sandwichCB.setBounds(450, 190, 150, 30);
        sandwichCB.setBackground(Color.ORANGE);
        panel.add(sandwichCB);

        juiceCB = new JCheckBox("Juice ($2.50)");
        juiceCB.setBounds(450, 230, 150, 30);
        juiceCB.setBackground(Color.ORANGE);
        panel.add(juiceCB);

        cookiesCB = new JCheckBox("Cookies ($3.50)");
        cookiesCB.setBounds(450, 270, 150, 30);
        cookiesCB.setBackground(Color.ORANGE);
        panel.add(cookiesCB);

        iceCB = new JCheckBox("Extra Ice");
        iceCB.setBounds(620, 70, 100, 30);
        panel.add(iceCB);

        giftCB = new JCheckBox("Gift Wrap");
        giftCB.setBounds(620, 110, 100, 30);
        giftCB.setSelected(true);
        panel.add(giftCB);

        couponCB = new JCheckBox("Use Coupon");
        couponCB.setBounds(620, 150, 120, 30);
        couponCB.setSelected(true);
        panel.add(couponCB);

        buyBtn = new JButton("Buy");
        buyBtn.setBounds(150, 280, 100, 35);
        buyBtn.setBackground(new Color(0, 128, 255));
        buyBtn.setForeground(Color.WHITE);
        buyBtn.setFont(new Font("Arial", Font.BOLD, 14));
        buyBtn.setFocusPainted(false);
        buyBtn.setBorder(BorderFactory.createLineBorder(new Color(0, 102, 204), 2));
        buyBtn.addMouseListener(this);
        buyBtn.addActionListener(this);
        panel.add(buyBtn);

        exitBtn = new JButton("Exit");
        exitBtn.setBounds(270, 280, 100, 35);
        exitBtn.setBackground(new Color(255, 87, 87));
        exitBtn.setForeground(Color.WHITE);
        exitBtn.setFont(new Font("Arial", Font.BOLD, 14));
        exitBtn.setFocusPainted(false);
        exitBtn.setBorder(BorderFactory.createLineBorder(new Color(204, 0, 0), 2));
        exitBtn.addMouseListener(this);
        exitBtn.addActionListener(this);
        panel.add(exitBtn);

        totalBtn = new JButton("Total");
        totalBtn.setBounds(580, 330, 100, 35);
        totalBtn.setBackground(new Color(0, 180, 120));
        totalBtn.setForeground(Color.WHITE);
        totalBtn.setFont(new Font("Arial", Font.BOLD, 14));
        totalBtn.setFocusPainted(false);
        totalBtn.setBorder(BorderFactory.createLineBorder(new Color(0, 153, 102), 2));
        totalBtn.addActionListener(this);
        panel.add(totalBtn);

        totalPriceLabel = new JLabel("Total Price: $0.00");
        totalPriceLabel.setBounds(580, 290, 250, 30);
        totalPriceLabel.setFont(new Font("Arial", Font.BOLD, 16));
        totalPriceLabel.setForeground(Color.BLUE);
        panel.add(totalPriceLabel);

        img = new ImageIcon("Image/XYZ.jpg");
        JLabel imgLabel = new JLabel(img);
        imgLabel.setBounds(612, 612, 200, 112);
        panel.add(imgLabel);
    }

    public void mouseClicked(MouseEvent me) {}
    public void mousePressed(MouseEvent me) {}
    public void mouseReleased(MouseEvent me) {}

    public void mouseEntered(MouseEvent me) {
        if (me.getSource() == buyBtn) {
            buyBtn.setBackground(new Color(30, 144, 255)); // Dodger blue
            buyBtn.setCursor(new Cursor(Cursor.HAND_CURSOR));
        } else if (me.getSource() == exitBtn) {
            exitBtn.setBackground(new Color(220, 20, 60)); // Crimson
            exitBtn.setCursor(new Cursor(Cursor.HAND_CURSOR));
        }
    }

    public void mouseExited(MouseEvent me) {
        if (me.getSource() == buyBtn) {
            buyBtn.setBackground(new Color(0, 128, 255));
        } else if (me.getSource() == exitBtn) {
            exitBtn.setBackground(new Color(255, 87, 87));
        }
    }

    public void actionPerformed(ActionEvent ae) {
        String command = ae.getActionCommand();

        if (command.equals("Total")) {
            calculateTotal();
        } else if (command.equals("Buy")) {
            processPurchase();
        } else if (command.equals("Exit")) {
            System.exit(0);
        }
    }

    private void calculateTotal() {
        int quantity;
        try {
            quantity = Integer.parseInt(quantityTF.getText().trim());
            if (quantity <= 0) throw new NumberFormatException();
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Enter a valid positive quantity.");
            return;
        }

        totalPrice = 0.0;

        if (sodaCB.isSelected()) totalPrice += PRICE_SODA * quantity;
        if (chipsCB.isSelected()) totalPrice += PRICE_CHIPS * quantity;
        if (candyCB.isSelected()) totalPrice += PRICE_CANDY * quantity;
        if (sandwichCB.isSelected()) totalPrice += PRICE_SANDWICH * quantity;
        if (juiceCB.isSelected()) totalPrice += PRICE_JUICE * quantity;
        if (cookiesCB.isSelected()) totalPrice += PRICE_COOKIES * quantity;

        totalPriceLabel.setText(String.format("Total Price: $%.2f", totalPrice));
    }

    private void processPurchase() {
        String name = userTF.getText().trim();
        String pin = new String(pinPF.getPassword());

        if (name.isEmpty() || pin.isEmpty()) {
            JOptionPane.showMessageDialog(this, "Please fill in your name and PIN.");
            return;
        }

        if (totalPrice == 0.0) {
            JOptionPane.showMessageDialog(this, "Click 'Total' first to calculate price.");
            return;
        }

        StringBuilder selectedItems = new StringBuilder();
        if (sodaCB.isSelected()) selectedItems.append("Soda ");
        if (chipsCB.isSelected()) selectedItems.append("Chips ");
        if (candyCB.isSelected()) selectedItems.append("Candy ");
        if (sandwichCB.isSelected()) selectedItems.append("Sandwich ");
        if (juiceCB.isSelected()) selectedItems.append("Juice ");
        if (cookiesCB.isSelected()) selectedItems.append("Cookies ");

        String extras = "";
        if (iceCB.isSelected()) extras += "Extra Ice ";
        if (giftCB.isSelected()) extras += "Gift Wrap ";
        if (couponCB.isSelected()) extras += "Coupon ";

        JOptionPane.showMessageDialog(this,
                "✅ Purchase Successful!\n" +
                        "👤 User: " + name +
                        "\n🔒 PIN: " + pin +
                        "\n🛒 Items: " + selectedItems.toString() +
                        "\n➕ Extras: " + extras +
                        "\n💰 Total Paid: $" + String.format("%.2f", totalPrice));

        totalPrice = 0.0;
        totalPriceLabel.setText("Total Price: $0.00");
    }

    public static void main(String[] args) {
        new VendingMachineFrame().setVisible(true);
    }
}

