# JAVAC-PROJECT-1
The Life Reminder Application is a Java-based project that helps users manage tasks and events by setting reminders with title, date, time, and notes. Users can add, view, update, or delete reminders easily. It improves time management, prevents missed deadlines, and can be enhanced with database storage and notifications.
import java.util.*;

class Reminder {
    String title;
    String date; // format: yyyy-mm-dd
    String time; // format: HH:mm
    String note;

    Reminder(String title, String date, String time, String note) {
        this.title = title;
        this.date = date;
        this.time = time;
        this.note = note;
    }

    @Override
    public String toString() {
        return title + " on " + date + " at " + time + " - " + note;
    }
}

class ReminderManager {
    private List<Reminder> reminders = new ArrayList<>();

    public void addReminder(Reminder r) {
        reminders.add(r);
        System.out.println("✅ Reminder added successfully!");
    }

    public void viewReminders() {
        if (reminders.isEmpty()) {
            System.out.println("No reminders found.");
        } else {
            for (int i = 0; i < reminders.size(); i++) {
                System.out.println((i+1) + ". " + reminders.get(i));
            }
        }
    }

    public void deleteReminder(int index) {
        if (index >= 0 && index < reminders.size()) {
            reminders.remove(index);
            System.out.println("🗑 Reminder deleted!");
        } else {
            System.out.println("Invalid reminder index.");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ReminderManager manager = new ReminderManager();
        int choice;

        do {
            System.out.println("\n--- Life Reminder Application ---");
            System.out.println("1. Add Reminder");
            System.out.println("2. View Reminders");
            System.out.println("3. Delete Reminder");
            System.out.println("4. Exit");
            System.out.print("Enter choice: ");
            choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {
                case 1:
                    System.out.print("Enter Title: ");
                    String title = sc.nextLine();
                    System.out.print("Enter Date (yyyy-mm-dd): ");
                    String date = sc.nextLine();
                    System.out.print("Enter Time (HH:mm): ");
                    String time = sc.nextLine();
                    System.out.print("Enter Note: ");
                    String note = sc.nextLine();
                    manager.addReminder(new Reminder(title, date, time, note));
                    break;

                case 2:
                    manager.viewReminders();
                    break;

                case 3:
                    manager.viewReminders();
                    System.out.print("Enter reminder number to delete: ");
                    int idx = sc.nextInt() - 1;
                    manager.deleteReminder(idx);
                    break;

                case 4:
                    System.out.println("👋 Exiting...");
                    break;

                default:
                    System.out.println("Invalid choice. Try again!");
            }
        } while (choice != 4);

        sc.close();
    }
}
