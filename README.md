package application;

import java.io.File;
import java.util.Scanner;

public class Program {
	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		System.out.println("Enter a folder path: ");
		String strPath = sc.nextLine();
		
		File path = new File(strPath);
		
		File[] folders = path.listFiles(File::isDirectory); // listar apenas quem é diretório, ou pasta.
		System.out.println("FOLDERS:");
		for (File folder : folders) { // para cada FILE folder contido no meu vetor chamado folders
			System.out.println(folder);
		}
		
		File[] files = path.listFiles(File::isFile); // somente a lista de arquivos.
		System.out.println("FILES:");
		for (File file : files) { // para cada FILE folder contido no meu vetor chamado files
			System.out.println(file);
			
		}
		boolean success = new File(strPath + "\\subdir").mkdir(); // criar uma subpasta 'subdir' apartir da pasta strPath
		System.out.println("Directory created successfully: " + success);
		
		sc.close();
	}
}
