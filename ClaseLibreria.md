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
	
	/// Punto 4) Invoco a la funcion devolverNacionalidad programada en AUTORES.
	
	public void mostrarAutoresNacionalidad(String nac)
	{
		Autor aut;
		int i=0;
		for(i=0;i<autores.size();i++)
		{
			aut = autores.get(i);
			if(aut.devolverNacionalidad()==nac)
			{
				System.out.print("Nombre: "+aut.devolverNombre());
			}
			else
				System.out.print("No hay autores de esta nacionalidad");
		}
		
	}
	
	/// Punto 5) Primero entro por autores, hago un ciclo for para el autor y otro ciclo para verificar todos los libros de cada autor, e informarlos si es de
	/// la nacionalidad solicitada.
	
	public void consultarTitulosAutoresNacionalidad(String nac)
	{
		Libro lib;
		Autor aut;
		int i=0,j=0;
		for(i=0;i<autores.size();i++)
		{
			aut = autores.get(i);
		
			if(aut.devolverNacionalidad()==nac)
			{
				System.out.print("Autor: "+aut.devolverNombre());
				
				for(j=0;j<libros.size();j++)
				{
					lib = libros.get(j);
					System.out.print("Libro: "+lib.devolverNombreLibro());
					j++;
				}
				
		i++;
			
			}
		}
	}
	
	/// Punto 6) Llamo a la funcion contarCantidadEscritos definida en la misma libreria, por eso uso el this, porque me refiero al mismo objeto.
	/// Recorro los autores, si tienen mas de tres imprimo su nombre.
	
	public void consultarAutoresMasDe3Titulos() 
	{
		Autor aut;
		Libro lib;
		int i=0,j=0,cantidadEscritos;
		for(i=0;i<autores.size();i++)
		{
			aut = autores.get(i);
			cantidadEscritos = this.contarCantidadEscritos(aut);
				if(cantidadEscritos>=3)
				{
					System.out.print("El autor "+aut.devolverNombre()+"tiene mas de 3 libros disponibles");
				}
			}
	}
	
	/// Funcion auxiliar para el punto 6.
	
	public int contarCantidadEscritos(Autor aut) {
		int cont=0;
		int i=0,j=0;
		Libro lib;
		String tit;
		while((i<autores.size()) && autores.get(i)!=aut)
		{
			i++;
			if(autores.get(i)==aut)
			{
				for(j=0;j<libros.size();j++)
				{
					cont++;
				}
			}
		}
	
		return cont;
	}
	
	/// Punto 7) Se supone unico porque el enunciado lo menciona de esa forma.
	
	public void mayorEjemplaresVenta()
	{ 
		Libro lib;
		int mayor=0,i=0;
		for(i=0;i<libros.size();i++)
		{
			lib = libros.get(i);
			if(lib.devolvercantEjemplares()>mayor)
			{
				mayor = lib.devolvercantEjemplares();
			}
		i++;
		}
	}
	
}

