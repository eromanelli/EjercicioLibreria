import java.util.Scanner;
import java.util.ArrayList;


	public class Libreria {
	
	private int cuit;
	private String razonSocial;
	private ArrayList<Libro> libros;
	private ArrayList<Autor> autores;
	
	public Libreria() {
		Scanner entrada = new Scanner (System.in);
		System.out.print("Ingrese Cuit: ");
		cuit = entrada.nextInt();
		System.out.print("Ingrese Razon Social: ");
		razonSocial = entrada.next();
		autores = new ArrayList<Autor>();
                libros = new ArrayList<Libro>();
		
	}
	
	/// punto 1, visto en clase.
	
	public void agregarLibro() {
	Scanner entrada = new Scanner (System.in);
	System.out.print("Ingrese ISBN");
	int isbn = entrada.nextInt();
	Libro lib = this.buscarLibro(isbn);
	if(lib!=null)
		System.out.print("Error. Ya existe el libro");
	else
	{
		System.out.print("Ingrese Titulo: ");
		String tit = entrada.next();
		System.out.print("Ingrese cantidad de Ejemplares: ");
		byte cant = entrada.nextByte();
		System.out.print("Ingrese nombre del Autor: ");
		String nom = entrada.next();
		Autor aut = this.buscarAutor(nom);
		if (aut == null) {
			System.out.print("Ingrese Nacionalidad: ");
			String nac = entrada.next();
			aut = new Autor (nom,nac);
			autores.add(aut);
		}
		
		lib = new Libro(isbn,tit,cant,aut);
		libros.add(lib);
		aut.agregarLibro(lib);
	}
	
	}
	
	/// funcion auxiliar busco libro
	public Libro buscarLibro(int valor) {
	int i=0;
	while((i<libros.size())&&(!libros.get(i).sos(valor))) 
		i++;
		if(i>=libros.size())
			return null;
		else
			return libros.get(i);
	}
	
	/// funcion auxiliar busco autor
	public Autor buscarAutor(String str) {
	int i=0;
	while((i<autores.size())&& (!autores.get(i).sOs(str)))
		i++;
		if(i>=autores.size())
			return null;
		else
			return autores.get(i);
	}
	
	/// Punto 2) Llamo a la funcion buscarLibro para verificar que exista el libro
	
	public void agregarEjemplaresLibro(int valor) {
		Libro libro = buscarLibro(valor);
		if(libro!=null)
		{
			libro.agregarEjemplares(libro);
		}
		else
			System.out.print("No se encontro el libro especificado");
	}
	
	/// Punto 3) Llamo a la fucion buscarAutor para verificar existencia
	
	public void mostrarEjemplaresDisponibles(String aut){
		Autor autor = buscarAutor(aut);
		if(autor!=null)
		{
			autor.mostrarLibrosDisponibles();
		}
	}
	
	/// Punto 4) Invo
