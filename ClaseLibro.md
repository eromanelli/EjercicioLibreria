import java.util.Scanner;

public class Libro {

	private int isbn;
	private String titulo;
	private byte cantEjempl;
	private Autor autor;
	
	public Libro(int valor1, String str, byte valor2, Autor aut) {
		
		isbn = valor1;
		titulo = str;
		cantEjempl = valor2;
		autor = aut;
		
	}
	
	/// metodo para devolver el identificador del libro
	
	public boolean sos(int valor) {
		return isbn == valor;
	}
	
	/// agrego ejemplares de un solo libro 
	
	public void agregarEjemplares(Libro lib) {
		
	Scanner entrada = new Scanner(System.in);
	System.out.print("Ingrese cantidad de ejemplares a ingresar: ");
	int cant = entrada.nextInt();
	this.cantEjempl+=cant;
	
	}
	
	public int devolvercantEjemplares()
	{
		return cantEjempl;
	}
	
	public String devolverNombreLibro()
	{
		return titulo;
	}

	
}
