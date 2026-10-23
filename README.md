# Java-code-2
package q28434;
import java.io.*;
import java.util.*;

public class WordFrequencyAnalyzer {

	public static void main(String[]args){
		Scanner sc = new
			Scanner(System.in);
		String fileName = sc.nextLine();
		File file = new File(fileName);
		if(!file.exists()){
			System.out.println("File does not exist");
			return;
		}
		TreeMap<String,Integer>map = new TreeMap<>();
		try{
			Scanner reader = new Scanner(file);
			while(reader.hasNext()){
				String word = reader.next().toLowerCase();
				word = word.replaceAll("[^a-zA-Z0-9]","");
				if(!word.isEmpty()){
					map.put(word,map.getOrDefault(word,0)+1);
				}
			}
			reader.close();
			for(String word:map.keySet()){
				System.out.println(word+": "+map.get(word));
			}
		}catch(FileNotFoundException e){
			System.out.println("File does not exist");
		}
		sc.close();
	}

}
