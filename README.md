package application;

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class Program {

	public static void main(String[] args) {
		
		String path = "c:\\Projetos\\in.txt";
		FileReader fr = null; //passar o null so pra ele ter um valor inicial
		BufferedReader br = null ; //passar o null so pra ele ter um valor inicial
		
		try {
			fr = new FileReader(path); // estou estabelecendo uma stream(sequencia) de leitura apartir do arquivo que estiver nesse caminho
			br = new BufferedReader(fr); 
			// br = new BufferedReader(new FileReader(path)); // poderia fazer assim.
			/*
			 *  o BufferedReader ele é instancaido a partir do FileReader, ele é uma abstração maior, eu pego a stream basica
			 *  e apartir dela eu instancio a stream que tem um esquema de buffer pra deixar mais rapida a leitura, muito 
			 *  esteresante esse esquema, por que deixa mais flexivel o sistema de leitura de arquivos. 
			 */
			
			String line = br.readLine();
			/*
			 * esse readLine ele vai ler uma linha do arquivo, se o arquivo ja estiver no final, esse readLine vai 
			 * retornar nulo, então agora vou fazer a seguiten lógica, eu vou criar um while e testar, enquanto  esse line
			 * foir diferente de nulo, significa que ele leu com sucesso a minha linha, então eu vou imprimir na tela esse
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
		/*
		 * só que aqui tambem pode uma excessão IOException na hora de fechar os streamers, então eu vou ter que abrir um
		 * bloco try, pra tentar fechar aqui as streams, e ai sim se acontecer uma excessão na hora de fechar as streams
		 * eu vou ter que capturar essa excessão e fazer alguma coisa, nesse caso aqui eu simplesmente vou colocar um
		 * e.PrintStackTrace(), por que ai se não der certo pra fechar as streams, segnifica que deu problema mesmo,
		 * ai e vou querer ver direitinho o erro que aconteceu.
		 */
		finally {
			try {
				if (br != null) {
				br.close();
				}
				if (fr != null) {
				fr.close();
				}
			
			}
			catch(IOException e) {
				e.printStackTrace(); 
			}
		}
	}
}

