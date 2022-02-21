package application;

import java.io.File;
import java.io.IOException;
import java.util.Scanner;

public class Program {

	public static void main(String[] args) {
		
		File file = new File ("c:\\Projetos\\in.txt"); 
		/*
		 * porque tenho que colocar o '\\' ? é por que o '\' ele é o prefixo de caracteres especiais,
		 * por exemplo: \n, \t e assim por diante pra indicar que você quer uma barrinha invertida mesmo, voce
		 * tem que colocar duas barras.
		 */
		
		Scanner sc = null; // passar o null so pra ele ter um valor inicial
		
		/*
		 * agora vou instanciar meu scanner a partir desse arquivo(file), quando eu instanciar meu scanner a partir  
		 * desse arquivo, o meu programa vai tentar abrir o arquivo e nesse momento pode ser gerada uma excessao do tipo
		 * IOException, então eu vou ser orbigado a colocar essa abertura do arquivo dentro de um bloco try.
		 */
		
		try {
			sc = new Scanner(file);
			while (sc.hasNextLine()) { // isso é pra testar se ainda existe uma nova linha no arquivo.
				System.out.println(sc.nextLine());  // se existir uma proxima linha no arquivo ainda, eu vou mandar imprimir essa linha
			}
			
		}
		catch (IOException e) {
			System.out.println("Error " + e.getMessage());
		}
		/*
		 * tem uma coisa interesante aqui, o scanner foi aberto na linha 27 e eu não fechei o scanner
		 * eu poderia fechar o scanner na linha 31, só que se der algum erro no processo TRY, ou de leitura, ou de abertura
		 * do arquivo, o meu bloco TRY vai ser cortado e vai cair no catch, e o Scanner não vai ser fechado, que que eu vou
		 * fazer então? eu vou colocar um bloco finally aqui, pra fechar o Scanner, isso é uma boa pratica, você colocar
		 * o fechamento do seu recurso no bloco finally, por que? porque o recurso vai ser fechado independente se deu certo o try ou não,
		 * então eu tiro o cs.close() da linha 31 e coloco no finally, só que agora é o seguinte, pode ser que tenha dado
		 * um erro na hora de instanciar o Scanner, nesse caso o meu Scanner nem foi instanciado e ja deu uma excessão
		 * se isso acontecer eu não posso simplesmente dar um sc.close no finally, porque vai dar um "null point exception"
		 * pq o sc vai ta valendo nulo, então no finally eu vou ter que por um IF, testando se o Scanner  é diferente de 
		 * null(!=), se for diferente de nulo, ai sim eu vou dar um close nesse Scanner.  
		 */
		finally {
			if (sc != null) {
			sc.close();
			}
		}
	}
}
