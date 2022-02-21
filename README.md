package application;

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class Program {

	public static void main(String[] args) {
		
		String path = "c:\\Projetos\\in.txt";
		
		try(BufferedReader br = new BufferedReader(new FileReader(path))) {
			/*
			 *  o BufferedReader ele é instancaido a partir do FileReader, ele é uma abstração maior, eu pego a stream basica
			 *  e apartir dela eu instancio a stream que tem um esquema de buffer pra deixar mais rapida a leitura, muito 
			 *  esteresante esse esquema, por que deixa mais flexivel o sistema de leitura de arquivos. 
			 */
			
			String line = br.readLine();
			/*
			 * esse readLine ele vai ler uma linha do arquivo, se o arquivo ja estiver no final, esse readLine vai 
			 * retornar nulo, então agora vou fazer a seguiten lógica, eu vou criar um while e testar, enquanto  esse line
			 * for diferente de nulo, significa que ele leu com sucesso a minha linha, então eu vou imprimir na tela esse
			 * line e em seguida eu vou mandar ler novamente outra linha fazendo br.readLine novamente, então esse é o
			 * esquema basico de você ler uma arquivo com o BufferedReader
			 */
			while (line != null) {
				System.out.println(line);
				line = br.readLine();
			}
		}
		catch (IOException e) {
			System.out.println(e.getMessage());
		}
	}
}

![11-arquivos pdf](https://user-images.githubusercontent.com/61166475/155008321-4d9b66b0-b4fe-4278-8743-e152fa3013f4.png)
