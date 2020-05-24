import java.io.*;
import java.util.Scanner;
public class FileSplitter {
    public static void main(String args[]) {
        try {
            // Reading file and getting no. of files to be generated  
			Scanner sc = new Scanner(System.in);
			System.out.println("Enter input file path(D:/Folder/FileName):-");
			String inputfilePath = sc.nextLine();
            //String inputfilePath = "D:/Java/split"; //  Source File Name.  
			System.out.println("Enter minimum number of lines for each file:-");
			int linesToSplit = sc.nextInt();
           // double linesToSplit = 300000.0; //  No. of lines to be split and saved in each output file.  
            File file = new File(inputfilePath);
            Scanner scanner = new Scanner(file);
            int countLines = 0;
            while (scanner.hasNextLine()) {
                scanner.nextLine();
                countLines++;
            }
            System.out.println("Lines in the file: " + countLines); // Displays no. of lines in the input file.  

            double temp = (countLines / linesToSplit);
            int temp1 = (int) temp;
            int numberOfFiles = 0;
            if (temp1 == temp) {
                numberOfFiles = temp1;
            } else {
                numberOfFiles = temp1 + 1;
            }
            System.out.println("No. of files to be generated :" + numberOfFiles); // Displays no. of files to be generated.  

            //---------------------------------------------------------------------------------------------------------  

            // Actual splitting of file into smaller files  

            FileInputStream fstream = new FileInputStream(inputfilePath);
            DataInputStream in = new DataInputStream(fstream);

            BufferedReader br = new BufferedReader(new InputStreamReader( in ));
            String strLine;

            for (int j = 1; j <= numberOfFiles; j++) {
                FileWriter fstream1 = new FileWriter("D:/Java/Split_Files/File" + j + ".txt"); // Destination File Location  
                BufferedWriter out = new BufferedWriter(fstream1);
                for (int i = 1; i <= linesToSplit; i++) {
                    strLine = br.readLine();
                    if (strLine != null) {
                        out.write(strLine);
                        if (i != linesToSplit) {
                            out.newLine();
                        }
                    }
                }
                out.close();
            }

            in .close();
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }

    }

}
