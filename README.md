# Digital_Clock
import javax.swing.*;
import java.awt.*;
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Date;

public class DigitalClock extends JFrame {

    private JLabel timeLabel;
    private SimpleDateFormat timeFormat;

    public DigitalClock() {
        setTitle("Digital Clock");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(300, 100);
        setLayout(new FlowLayout());
        setLocationRelativeTo(null); // Center the frame

        timeLabel = new JLabel();
        timeLabel.setFont(new Font("Arial", Font.BOLD, 48));
        add(timeLabel);

        timeFormat = new SimpleDateFormat("HH:mm:ss"); // You can change the format

        updateTime();

        // Update the time every second
        Timer timer = new Timer(1000, e -> updateTime());
        timer.start();
    }

    private void updateTime() {
        Date now = Calendar.getInstance().getTime();
        String formattedTime = timeFormat.format(now);
        timeLabel.setText(formattedTime);
    }

    public static void main(String[] args) {
        // Use SwingUtilities.invokeLater to ensure thread safety for GUI updates
        SwingUtilities.invokeLater(() -> {
            new DigitalClock().setVisible(true);
        });
    }
}
