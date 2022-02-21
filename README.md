package application;

import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class Program {

	public static void main(String[] args) {

		String[] lines = new String[] {"Good morning", "Good afternoon", "Good night"};
		
		String path = "c:\\Projetos\\out.txt";
		
		/*
		 * try (BufferedWriter bw = new BufferedWriter(new FileWriter(path, true)))  
		 * o true é pra não recriar, não destruir o que tinha, eu quero so gravar denovo no final
		 */
		
		try (BufferedWriter bw = new BufferedWriter(new FileWriter(path))){
			for (String line : lines) { // para cada STRING line contido no meu vetor chamado lines
				bw.write(line); // pra escrever essa linha no meu arquivo
				bw.newLine(); // que de linha
			}
		}
		catch(IOException e) {
			e.printStackTrace();
		}
	}

}
