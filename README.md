# 38.File-using-Streams-and-files
File using stream and files

package fileusingstreamandfiles;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.List;
import java.util.logging.Level;
import java.util.logging.Logger;
import java.util.stream.Collectors;

public class FileUsingStreamAndFiles{
public static void main(String[] args) {
// Define file paths
String inputFilePath = "C:\\Users\\1BSCCSA43\\Documents\\input_names.txt";
String outputFilePath = "C:\\Users\\1BSCCSA43\\Documents\\output_uppercase.txt";
try {
// Read names from the input file using BufferedReader and Java streams
List<String> names = readNamesFromFile(inputFilePath);
// Convert names to uppercase using Java streams
List<String> uppercaseNames = names.stream()
.map(String::toUpperCase)
.collect(Collectors.toList());
// Write uppercase names to the output file using BufferedWriter
writeUppercaseNamesToFile(outputFilePath, uppercaseNames);
System.out.println("Uppercase names written to " + outputFilePath);
} catch (IOException e) {

e.printStackTrace();
}
}
// Read names from a file using BufferedReader and Java streams
private static List<String>readNamesFromFile(String filePath) throws IOException {
try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {
return reader.lines().collect(Collectors.toList());
}
}
// Write uppercase names to a file using BufferedWriter
private static void writeUppercaseNamesToFile(String filePath, List<String> uppercaseNames) throws IOException  {
try (BufferedWriter writer = new BufferedWriter(new FileWriter(filePath))) { 
for (String name : uppercaseNames) {
writer.write(name);
writer.newLine();
}
}   catch (IOException ex) {
        Logger.getLogger(FileUsingStreamAndFiles.class.getName()).log(Level.SEVERE, null, ex);
    }
}
}

Output:
(save as input_names)
Uppercase names written to C:\Users\1BSCCSA43\Documents\output_uppercase.txt

