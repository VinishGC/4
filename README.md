import java.io.*;
import java.util.*;

class ReportGeneration {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        List<String> reportData = new ArrayList<>();

        System.out.println("Enter report entries (type 'done' to finish):");
        while (true) {
            String line = sc.nextLine();
            if (line.equalsIgnoreCase("done")) break;
            reportData.add(line);
        }

        try {
            FileWriter fw = new FileWriter("report.txt");
            for (String entry : reportData) {
                fw.write(entry + "\n");
            }
            fw.close();
            System.out.println("Report saved to report.txt");

            BufferedReader br = new BufferedReader(new FileReader("report.txt"));
            System.out.println("\n--- Generated Report ---");
            String line;
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
            br.close();
        } catch (IOException e) {
            System.out.println("Error: " + e.getMessage());
        }
        sc.close();
    }
}
