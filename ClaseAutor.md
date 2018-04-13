import java.util.ArrayList;

	public class Autor {

	private String nombre;
	private String nacionalidad;
	private ArrayList<Libro> libros;
	
	public Autor (String str1, String str2){
		nombre = str1;
		nacionalidad = str2;
		libros = new ArrayList<Libro>();
		
	}
	
	/// funciones
	
	public void agregarLibro(Libro lib) {
		libros.add(lib);
	}
	
	public boolean sOs(String str)
	{
		return nombre == str;
	}
	
	public void mostrarLibrosDisponibles()
	{
		Libro lib;
		int i=0;
		while(i<libros.size())
			{
			lib = libros.get(i);
				if(lib.devolvercantEjemplares()>=1)
				{
					System.out.print("Ejemplar: "+lib.devolverNombreLibro());
				}
			i++;
			
			}
	
	
	}
	
	
	public String devolverNacionalidad() {
		return nacionalidad;
	}
	
	public String devolverNombre()
	{
		return nombre;
	}
	
}
