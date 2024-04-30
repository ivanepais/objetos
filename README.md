# objetos

|| Dependencias

	Se refiere a la relación entre dos elementos del código, donde un elemento, llamado "dependiente", requiere o utiliza otro elemento, llamado "dependencia". 

	Esta relación puede surgir en diferentes contextos y tiene implicaciones importantes para el diseño, la modularidad y la mantenibilidad del software.


	1. Dependencia de Clases: 

		En la programación orientada a objetos, una clase puede depender de otra si la utiliza como un tipo de datos o si crea instancias de ella.

		La dependencia de clases se manifiesta cuando una clase utiliza los métodos o atributos de otra clase.
	

		```java

		public class Cliente {
		    private Servicio servicio = new Servicio();

		    public void realizarOperacion() {
		        servicio.hacerAlgo();
		    }
		}

		```


	2. Dependencia de Métodos:

    	Un método puede depender de otro si lo invoca o utiliza su resultado. 

    	La dependencia de métodos es común en la programación modular, donde los métodos se organizan de manera que realicen tareas específicas y se invocan según sea necesario.

    	```java

    	public void metodoPrincipal() {
		    int resultado = calcularResultado();
		    // Hacer algo con el resultado
		}

		public int calcularResultado() {
		    // Realizar cálculos
		    return resultado;
		}

    	```


    3. Dependencia de Archivos y Módulos:

	    En sistemas más grandes, los archivos o módulos pueden depender unos de otros. 

	    Por ejemplo, un archivo fuente podría depender de las funciones proporcionadas por otro archivo o módulo.


	4. Dependencia de Librerías Externas:

	    Los programas a menudo dependen de librerías externas o frameworks para aprovechar funcionalidades predefinidas. 

	    La dependencia de librerías externas implica que el programa confía en ciertos comportamientos y API proporcionados por esas librerías.

	    ```java

	    import java.util.List;

		public class MiClase {
		    public void usarLista(List<String> lista) {
		        // Hacer algo con la lista
		    }
		}

	    ```


	5. Dependencia Temporal:

    	Una dependencia temporal se produce cuando la ejecución de una parte del código depende del estado o resultados de otra parte ejecutada previamente.

    	```java

		public void ejecutarOperaciones() {
		    inicializarDatos();
		    procesarDatos();
		}

		private void inicializarDatos() {
		    // Inicializar datos necesarios
		}

		private void procesarDatos() {
		    // Procesar los datos inicializados
		}

    	```


    Un exceso de dependencias puede conducir a un código fuente acoplado y difícil de mantener.

    Por lo tanto, los principios como la Inversión de Dependencias (Dependency Inversion Principle) y la Inyección de Dependencias (Dependency Injection) se utilizan para minimizar el acoplamiento y mejorar la capacidad de mantenimiento y extensión del código.



|| Inyección de dependencias

	
	Clase 1: 

		```java

		import org.springframework.stereotype.Component;

		@Component
		public class MiComponente {

		    public void ejecutarAlgo() {
		        // Lógica del componente
		    }
		}

		```

		'MiComponente' es un componente gestionado por Spring. 

		Puede ser inyectado en otros componentes, controladores o servicios utilizando la inyección de dependencias.


	Clase 2: 

		```java

		@Controller
			public class OtroControlador {

			    private final MiComponente miComponente;

			    @Autowired
			    public OtroControlador(MiComponente miComponente) {
			        this.miComponente = miComponente;
			    }

			    @GetMapping("/otra-ruta")
			    public String otraRuta() {
			        miComponente.ejecutarAlgo();
			        return "otra-vista";
			    }
			}

		```

		'OtroControlador' tiene una dependencia de MiComponente, que se inyecta mediante el constructor. 

		Luego, en el método 'otraRuta()', se puede llamar a métodos de miComponente.



|| Tipos de inyección de dependencias

	
	1. Inyección de Dependencias en Campos:

		```java

		@Component
		public class Cliente {

		    @Autowired
		    private ServicioCliente servicioCliente;

		    public void realizarOperacion() {
		        servicioCliente.realizarOperacion();
		    }
		}

		```
		
		Se utiliza en un campo 'servicioCliente' de la clase 'Cliente'.

		Spring buscará un bean de tipo 'ServicioCliente' y lo inyectará automáticamente en este campo cuando se cree el bean de 'Cliente'.


	2. Inyección de Dependencias en Constructor:

		```java

		@Component
		public class Cliente {

		    private final ServicioCliente servicioCliente;

		    @Autowired
		    public Cliente(ServicioCliente servicioCliente) {
		        this.servicioCliente = servicioCliente;
		    }

		    public void realizarOperacion() {
		        servicioCliente.realizarOperacion();
		    }
		}

		```

		'@Autowired' se utiliza en el constructor de la clase 'Cliente'. 

		Cuando Spring crea un bean de 'Cliente', buscará un bean de tipo 'ServicioCliente' y lo inyectará automáticamente en el constructor.


	3. Inyección de Dependencias en Métodos:

		```java

		@Component
		public class Cliente {

		    private ServicioCliente servicioCliente;

		    @Autowired
		    public void setServicioCliente(ServicioCliente servicioCliente) {
		        this.servicioCliente = servicioCliente;
		    }

		    public void realizarOperacion() {
		        servicioCliente.realizarOperacion();
		    }
		}

		```

		La anotación '@Autowired' se utiliza en un método 'setServicioCliente'. 

		Spring llamará automáticamente este método y le proporcionará una instancia de 'ServicioCliente' cuando se cree el bean de 'Cliente'.



|| Objetos

	Se refiere a instancias de clases. 

	Java es un lenguaje de programación orientado a objetos, lo que significa que todo en Java es un objeto (excepto los tipos primitivos). 

	Un objeto es una instancia única de una clase que tiene atributos y métodos asociados.


	1. Clases y objetos: 

		Clases: 

			Es una plantilla para crear objetos. 

			Define la estructura y el comportamiento que compartirán los objetos de esa clase. 

			Se definen con la palabra clave 'class'. 

		```java

		public class Persona {
		    // Atributos
		    String nombre;
		    int edad;

		    // Métodos
		    void saludar() {
		        System.out.println("Hola, soy " + nombre + " y tengo " + edad + " años.");
		    }
		}

		```


		Objetos: 

			Es una instancia particular de una clase.

			Se crea a partir de la plantilla proporcionada por la clase y tiene su propia existencia en la memoria.


		```java

		// Creación de un objeto de la clase Persona
		Persona persona1 = new Persona();
		persona1.nombre = "Juan";
		persona1.edad = 30;

		// Llamada al método de la clase
		persona1.saludar();

		```


	2. Características de los Objetos:

    	Atributos: 

    		Representan las propiedades o características del objeto. 

    		En el ejemplo anterior, 'nombre' y 'edad' son atributos de la clase Persona.


    	Métodos: 

    		Representan el comportamiento del objeto. 

    		El método 'saludar()' es un método de la clase Persona.


   	3. Instanciación de Objetos:

    	La palabra clave 'new' se utiliza para crear una instancia (un objeto) de una clase. 

    	La memoria se asigna para el objeto, y el constructor de la clase se llama para inicializar el objeto.

    	```java

    	Persona persona1 = new Persona();

    	```


	4. Referencias a Objetos:

    	Las variables que almacenan objetos no almacenan realmente el objeto en sí, sino una referencia al objeto en la memoria.    

    	```java

    	Persona persona1 = new Persona();
		Persona persona2 = persona1; // Ambas variables apuntan al mismo objeto

    	```


    5. Encapsulamiento: 


    	Las clases pueden utilizar el concepto de encapsulamiento para ocultar ciertos detalles internos y exponer solo lo necesario a través de métodos públicos.

    	```java

    	public class CuentaBancaria {
		    private double saldo; // Atributo privado

		    public void depositar(double cantidad) {
		        // Lógica para depositar
		        saldo += cantidad;
		    }

		    public double obtenerSaldo() {
		        return saldo;
		    }
		}

    	```


    6. Herencia y Polimorfismo:

    	Herencia. 

    		Una clase puede heredar atributos y métodos de otra clase.

    	```java

    	// Herencia
		public class Empleado extends Persona {
		    // Nuevos atributos y métodos específicos para Empleado
		}

    	``` 


    	Polimorfismo: 

    		Un objeto puede ser tratado como un objeto de su clase base.

    		Es la capacidad de un objeto de tomar muchas formas.

    	```java

    	// Clase base
		class Animal {
		    void hacerSonido() {
		        System.out.println("Haciendo un sonido genérico");
		    }
		}

		// Clases derivadas
		class Perro extends Animal {
		    @Override
		    void hacerSonido() {
		        System.out.println("El perro ladra");
		    }
		}

		class Gato extends Animal {
		    @Override
		    void hacerSonido() {
		        System.out.println("El gato maulla");
		    }
		}

		public class EjemploPolimorfismo {
		    public static void main(String[] args) {
		        // Creación de objetos
		        Animal miAnimal1 = new Perro();
		        Animal miAnimal2 = new Gato();

		        // Llamadas a los métodos
		        miAnimal1.hacerSonido();  // Salida esperada: El perro ladra
		        miAnimal2.hacerSonido();  // Salida esperada: El gato maulla
		    }
		}

    	```

    	'Animal' es la clase base que tiene un método llamado 'hacerSonido'. 

    	Luego, hay dos clases derivadas, 'Perro' y 'Gato', que sobrescriben el método 'hacerSonido' para proporcionar implementaciones específicas para cada tipo de animal.

		En el método 'main', creamos dos objetos de tipo 'Animal', pero asignamos instancias de las clases derivadas 'Perro' y 'Gato' a esas variables. 

		Esto se llama "polimorfismo de ejecución". 

		Cuando llamamos al método 'hacerSonido' en estos objetos, se ejecuta la versión específica del método según el tipo real del objeto en tiempo de ejecución.


    7. Recolector de Basura: 

    	Java cuenta con un recolector de basura (Garbage Collector) que se encarga de liberar la memoria utilizada por los objetos que ya no son referenciados.


   	8. Equals y HashCode:

    	Los métodos 'equals()' y 'hashCode()' se utilizan para comparar la igualdad de objetos y son parte de la implementación de la clase Object, la clase base para todas las clases en Java.



|| Constructor 

	Es un método especial utilizado para inicializar objetos de una clase. 

	Su nombre debe ser idéntico al nombre de la clase y no tiene tipo de retorno, ni siquiera void. 

	Los constructores se llaman automáticamente cuando se crea una instancia (objeto) de la clase.


	1. Sintaxis: 

		```java

		public class MiClase {
		    // Constructor por defecto (sin parámetros)
		    public MiClase() {
		        // Código de inicialización
		    }

		    // Constructor con parámetros
		    public MiClase(int parametro1, String parametro2) {
		        // Código de inicialización con parámetros
		    }
		}


		```


	2. Constructor por Defecto:

    	Si no defines ningún constructor en tu clase, Java proporciona un constructor por defecto automáticamente.

    	Este constructor no toma ningún parámetro y simplemente inicializa los valores predeterminados.


	3. Constructor con Parámetros:

    	Puedes definir constructores que acepten parámetros para inicializar los atributos de la clase según los valores proporcionados durante la creación del objeto.


	4. Llamada al Constructor de la Clase Base:

    	En una jerarquía de clases, el constructor de una clase puede llamar al constructor de su clase base usando 'super()'.

    	```java

    	public class ClaseBase {
		    public ClaseBase(int valor) {
		        // Código de inicialización para la clase base
		    }
		}

		public class ClaseDerivada extends ClaseBase {
		    public ClaseDerivada(int valor) {
		        super(valor); // Llamada al constructor de la clase base
		        // Código de inicialización para la clase derivada
		    }
		}

    	```


    5. Uso de Constructores:

	    Los constructores se utilizan para asignar valores iniciales a los atributos de un objeto y realizar otras operaciones de inicialización necesarias. 

	    Son esenciales para garantizar que un objeto sea válido y coherente en su estado inicial.


	6. Sobrecarga de Constructores:

	    Puedes tener múltiples constructores en una clase mediante la técnica de sobrecarga de métodos, donde cada constructor tiene una lista de parámetros diferente.

	    ```java

	    public class Persona {
		    private String nombre;
		    private int edad;

		    // Constructor por defecto
		    public Persona() {
		        // Inicialización predeterminada
		    }

		    // Constructor con parámetros
		    public Persona(String nombre, int edad) {
		        this.nombre = nombre;
		        this.edad = edad;
		    }
		}

	    ```


	7. Construcción de objetos. 

		Se usa el operador 'new' seguido por la llamada al constructor de la clase.

		```java

		Persona persona1 = new Persona(); // Constructor por defecto
		Persona persona2 = new Persona("Juan", 25); // Constructor con parámetros

		```


	Ejemplos de uso: 

	1. Inicializar de Atributos: 

		Asignar valores iniciales a los atributos de un objeto.

		Esto garantiza que el objeto tenga un estado coherente desde el principio.

	```java

	public class Persona {
	    String nombre;
	    int edad;

	    // Constructor con parámetros para inicializar atributos
	    public Persona(String nombre, int edad) {
	        this.nombre = nombre;
	        this.edad = edad;
	    }
	}

	// Uso del constructor
	Persona persona = new Persona("Juan", 25);

	```


	2. Asignación de Valores Predeterminados: 

		Un constructor puede establecer valores predeterminados para los atributos si no se proporcionan al crear el objeto.


	```java

	public class Coche {
	    String modelo;
	    int año;

	    // Constructor con valores predeterminados
	    public Coche() {
	        this.modelo = "Desconocido";
	        this.año = 0;
	    }
	}

	// Uso del constructor
	Coche miCoche = new Coche(); // Se asignan valores predeterminados

	```


	3. Acciones adicionales:	

		Los constructores también se utilizan para realizar operaciones de inicialización adicionales necesarias para que el objeto esté en un estado válido.

	```java

	public class ConectorBD {
	    // Constructor que abre la conexión a la base de datos
	    public ConectorBD() {
	        // Código para abrir la conexión
	    }
	}

	// Uso del constructor
	ConectorBD bd = new ConectorBD(); // Se abre la conexión automáticamente

	```


	4. Herencia:	 

		Los constructores se utilizan para inicializar tanto la parte de la clase base como la de las clases derivadas.	

	```java

	public class Vehiculo {
	    int velocidad;

	    public Vehiculo(int velocidad) {
	        this.velocidad = velocidad;
	    }
	}

	public class Coche extends Vehiculo {
	    String modelo;

	    public Coche(int velocidad, String modelo) {
	        super(velocidad); // Llamada al constructor de la clase base
	        this.modelo = modelo;
	    }
	}

	```	


	5. Sobrecarga de Constructores:

   		Puedes tener múltiples constructores en una clase mediante la sobrecarga, lo que significa tener diferentes versiones del constructor con diferentes parámetros.

	```java

	public class Libro {
	    String titulo;
	    String autor;

	    // Constructor por defecto
	    public Libro() {
	        // Código de inicialización por defecto
	    }

	    // Constructor con parámetros
	    public Libro(String titulo, String autor) {
	        this.titulo = titulo;
	        this.autor = autor;
	    }
	}

	```


	6. This, llamada al constructor (sobrecargado o por defecto):

		Asigna valores. 

	```java

	public class Persona {
	    private String nombre;
	    private int edad;

	    // Constructor principal
	    public Persona(String nombre, int edad) {
	        this.nombre = nombre;
	        this.edad = edad;
	    }

	    // Constructor por defecto que llama al constructor principal
	    public Persona() {
	        this("Desconocido", 0);
	    }
	}

	```



|| Constructores sobrecargados
	
	Capacidad de una clase de tener múltiples constructores con la misma o diferente cantidad de parámetros. 

	Estos constructores comparten el mismo nombre pero difieren en la firma, es decir, en la cantidad, tipo o orden de los parámetros que aceptan.

	Cuando se crea una instancia de una clase utilizando un constructor, la JVM (Java Virtual Machine) determina cuál constructor utilizar según la cantidad y tipo de argumentos proporcionados. 

	Esto permite a la clase proporcionar diferentes maneras de inicializar sus objetos.

	```java

	public class Persona {
	    private String nombre;
	    private int edad;

	    // Constructor por defecto
	    public Persona() {
	        nombre = "Sin nombre";
	        edad = 0;
	    }

	    // Constructor con un parámetro
	    public Persona(String nombre) {
	        this.nombre = nombre;
	        edad = 0; // Edad por defecto
	    }

	    // Constructor con dos parámetros
	    public Persona(String nombre, int edad) {
	        this.nombre = nombre;
	        this.edad = edad;
	    }

	    // Otros métodos de la clase...
	    
	    // Método para mostrar información de la persona
	    public void mostrarInformacion() {
	        System.out.println("Nombre: " + nombre);
	        System.out.println("Edad: " + edad);
	    }

	    public static void main(String[] args) {
	        // Crear instancias utilizando diferentes constructores
	        Persona persona1 = new Persona();
	        Persona persona2 = new Persona("Alice");
	        Persona persona3 = new Persona("Bob", 30);

	        // Mostrar información de las personas
	        persona1.mostrarInformacion();
	        persona2.mostrarInformacion();
	        persona3.mostrarInformacion();
	    }
	}

	```



|| Referencias

	Son variables que almacenan direcciones de memoria, específicamente direcciones de objetos en el 'heap'. 

	Aunque en Java no puedes manipular directamente direcciones de memoria como lo harías en lenguajes de bajo nivel, las referencias te permiten acceder y manipular objetos de forma indirecta.

	1. Declaracion de Referencias:

		Se declaran con el tipo de objeto al que apuntarán, seguido del nombre de la variable. 

		```java

		// Declaración de referencia a un objeto de tipo String
		String miString;

		```

	2. Asignación de Referencias: 

		Las referencias se pueden asignar a objetos existentes utilizando el operador de asignación (=).

		```java

		// Asignación de referencia a un nuevo objeto String
		miString = new String("Hola, mundo");

		```


	3. Operaciones con Referencias: 

		Como pasarlas como argumentos a métodos, retornarlas desde métodos o asignarles nuevos valores.

		```java

		String otroString = miString;  // Asignación de una referencia a otra

		```


	4. Referencias y Objetos:

		La referencia apunta al objeto en el heap, pero no es el objeto en sí. 

		Varias referencias pueden apuntar al mismo objeto.

		```java

		String referencia1 = new String("Java");
		String referencia2 = referencia1;  // Ambas referencias apuntan al mismo objeto

		```


	5. Null: 	

		Una referencia puede tener el valor especial null, que indica que no apunta a ningún objeto.


	6. Operaciones de Dereferenciación:

    	Para acceder a los métodos y campos de un objeto, se utiliza la dereferenciación a través de la referencia.

    	```java

    	int longitud = miString.length();  // Dereferenciación para acceder al método 'length'

    	```


    7. Garbage Collection:

    	El recolector de basura liberar la memoria de objetos no utilizados. 

    	Cuando no hay referencias que apunten a un objeto, se convierte en candidato para ser recolectado.

    	```java

    	miString = null;  // La referencia a 'miString' ahora es null, el objeto puede ser recolectado

    	```


    8. Referencias a Objetos Anónimos:

    	Puedes crear referencias a objetos de manera anónima, especialmente al trabajar con interfaces o clases abstractas.

    
    9. Referencias a Objetos Genéricos:

    	Las referencias a objetos pueden ser utilizadas con tipos genéricos para hacer que el código sea más flexible y reutilizable

    	```java

    	List<String> lista = new ArrayList<>();

    	```



|| Objetos como argumentos
	
	De métodos o como valores de retorno desde métodos. 

	En Java, cuando pasas un objeto a un método, estás pasando la referencia al objeto, no el objeto en sí. 

	Esto significa que, dentro del método, puedes manipular el objeto referenciado, y cualquier cambio que realices afectará al objeto original fuera del método.

	```java

	public class ObjectPassingExample {
	    public static void main(String[] args) {
	        // Crear un objeto Persona
	        Persona persona = new Persona("Alice", 25);

	        // Llamar a un método y pasar el objeto como argumento
	        modificarPersona(persona);

	        // Imprimir la información después de llamar al método
	        System.out.println("Después de llamar al método:");
	        System.out.println(persona);
	    }

	    // Método que modifica el objeto Persona
	    public static void modificarPersona(Persona p) {
	        p.setEdad(30);
	        p.setNombre("Nuevo Nombre");
	    }
	}

	class Persona {
	    private String nombre;
	    private int edad;

	    public Persona(String nombre, int edad) {
	        this.nombre = nombre;
	        this.edad = edad;
	    }

	    public void setNombre(String nombre) {
	        this.nombre = nombre;
	    }

	    public void setEdad(int edad) {
	        this.edad = edad;
	    }

	    @Override
	    public String toString() {
	        return "Persona [nombre=" + nombre + ", edad=" + edad + "]";
	    }
	}

	```

	Se crea un objeto 'Persona' llamado 'persona'. 

	Luego, se llama al método 'modificarPersona' y se le pasa el objeto 'persona' como argumento. 

	Dentro del método, se modifica la 'edad' y el 'nombre' de la persona.

	Después de llamar al método, se imprime la información de la persona y se observa que los cambios realizados dentro del método han afectado al objeto original.


	Estás pasando la referencia al objeto, no puedes cambiar la referencia en sí misma. 

	Es decir, no puedes hacer que la referencia apunte a un objeto completamente diferente dentro del método. 

	La referencia es pasada por valor, pero aún así te permite modificar el estado del objeto al que apunta.



|| Herencia 

	Permite la creación de nuevas clases basadas en clases existentes. 

	En Java, la herencia se implementa utilizando la palabra clave 'extends'. 

	Una clase que hereda de otra se denomina "subclase" o "clase hija", y la clase de la cual hereda se llama "superclase" o "clase padre". 

	Facilita la reutilización de código y la creación de una jerarquía de clases.

	```java

	// Superclase o clase padre
	class Animal {
	    String nombre;

	    public Animal(String nombre) {
	        this.nombre = nombre;
	    }

	    public void hacerSonido() {
	        System.out.println("Haciendo un sonido genérico");
	    }
	}

	// Subclase o clase hija que hereda de Animal
	class Perro extends Animal {
	    public Perro(String nombre) {
	        super(nombre);
	    }

	    // Sobrescribe el método hacerSonido de la superclase
	    @Override
	    public void hacerSonido() {
	        System.out.println("Guau, guau");
	    }

	    // Nuevo método específico de la clase Perro
	    public void perseguirCola() {
	        System.out.println("Persiguiendo la cola");
	    }
	}

	public class EjemploHerencia {
	    public static void main(String[] args) {
	        // Crear una instancia de la clase Perro
	        Perro miPerro = new Perro("Buddy");

	        // Acceder a los miembros de la superclase
	        System.out.println("Nombre del perro: " + miPerro.nombre);

	        // Llamar al método hacerSonido de la subclase
	        miPerro.hacerSonido();

	        // Llamar al método específico de la clase Perro
	        miPerro.perseguirCola();
	    }
	}

	```

	La clase 'Animal' es la superclase con un constructor y un método 'hacerSonido'.

    La clase 'Perro' es la subclase que hereda de Animal utilizando extends.

    La subclase 'Perro' sobrescribe el método 'hacerSonido' y agrega un nuevo método 'perseguirCola'.

    En el método 'main', se crea una instancia de 'Perro' y se accede tanto a los miembros heredados de 'Animal' como a los específicos de 'Perro'.



|| Métodos sobreescritos
	
	Una subclase proporciona una implementación específica de un método que ya está definido en su superclase. 

	Cuando una subclase tiene un método con la misma firma (nombre, tipo de retorno y parámetros) que un método en la superclase, se dice que la subclase está sobrescribiendo el método de la superclase.


	1. Firma Idéntica: 

		El método en la subclase debe tener la misma firma que el método en la superclase. Esto incluye el nombre del método, el tipo de retorno y la lista de parámetros.


    2. Visibilidad Compatible o Más Permisiva: 

    	La visibilidad del método en la subclase puede ser igual o más permisiva que la visibilidad del método en la superclase. 

    	Por ejemplo, si un método en la superclase es 'protected', en la subclase puede ser 'protected' o 'public', pero no puede ser private.

    
    3. Valor de Retorno Covariante:

    	El tipo de retorno del método en la subclase puede ser un subtipo del tipo de retorno del método en la superclase.

    	Esto significa que la subclase puede devolver un tipo más específico.



|| Super
	
	Se utiliza para referirse a la superclase de la clase actual.

	Puede ser utilizada de varias maneras, y su principal propósito es acceder a los miembros (campos o métodos) de la superclase.


	1. Acceder a los Campos de la Superclase:

		Puedes utilizar 'super' para acceder a los campos de la superclase cuando hay un campo en la subclase con el mismo nombre y deseas diferenciarlos.

		```java
		class Animal {
		    String nombre = "Animal";
		}

		class Perro extends Animal {
		    String nombre = "Perro";

		    void mostrarNombres() {
		        System.out.println("Nombre en la subclase: " + nombre);
		        System.out.println("Nombre en la superclase: " + super.nombre);
		    }
		}

		public class EjemploSuperKeyword {
		    public static void main(String[] args) {
		        Perro miPerro = new Perro();
		        miPerro.mostrarNombres();
		    }
		}

		```

		'super.nombre' se utiliza para acceder al campo 'nombre' de la superclase 'Animal', mientras que nombre se refiere al campo de la subclase 'Perro'.

	
	2. Invocar Métodos de la Superclase:

		Puedes utilizar 'super' para invocar métodos de la superclase cuando hay una sobrescritura de método en la subclase y deseas ejecutar la versión de la superclase.

		```java

		class Animal {
		    void hacerSonido() {
		        System.out.println("Sonido genérico de un animal");
		    }
		}

		class Perro extends Animal {
		    @Override
		    void hacerSonido() {
		        super.hacerSonido();  // Invoca el método de la superclase
		        System.out.println("Guau, guau");
		    }
		}

		public class EjemploSuperKeyword {
		    public static void main(String[] args) {
		        Perro miPerro = new Perro();
		        miPerro.hacerSonido();
		    }
		}

		```

		'super.hacerSonido()' se utiliza para invocar el método 'hacerSonido' de la superclase 'Animal' desde la subclase 'Perro'.		


	3. Llamar al Constructor de la Superclase:

		Puedes utilizar 'super' para llamar al constructor de la superclase desde el constructor de la subclase.

		```java

		class Animal {
		    String nombre;

		    Animal(String nombre) {
		        this.nombre = nombre;
		    }
		}

		class Perro extends Animal {
		    String raza;

		    Perro(String nombre, String raza) {
		        super(nombre);  // Llama al constructor de la superclase
		        this.raza = raza;
		    }
		}

		public class EjemploSuperKeyword {
		    public static void main(String[] args) {
		        Perro miPerro = new Perro("Buddy", "Labrador");
		        System.out.println("Nombre del perro: " + miPerro.nombre);
		        System.out.println("Raza del perro: " + miPerro.raza);
		    }
		}

		```

		'super(nombre)' se utiliza para llamar al constructor de la superclase 'Animal' desde el constructor de la subclase 'Perro' y heredar la característica. 



|| Abstracción
	
	Es la capacidad de representar las características esenciales de un objeto sin proporcionar detalles innecesarios o irrelevantes. 

	En otras palabras, la abstracción se trata de centrarse en los aspectos más importantes de un objeto y ocultar los detalles de implementación menos importantes.


	Principios: 

	1. Identificar Entidades Relevantes: 

		La abstracción comienza identificando las entidades relevantes en el problema que estás tratando de resolver.

		Estas entidades pueden ser objetos del mundo real o conceptos abstractos.


    2. Definir Clases y Objetos: 

    	Una vez identificadas las entidades, las representas en tu programa mediante clases y objetos en Java. 

    	Cada clase encapsula el comportamiento y el estado asociado con una entidad específica.


    3. Ocultar Detalles de Implementación: 

    	En la definición de una clase, te enfocas en los detalles esenciales y relevantes para la entidad que estás representando, mientras ocultas los detalles de implementación innecesarios. 

    	Esto se logra mediante la encapsulación, donde los detalles internos de la clase se mantienen privados y solo se exponen los aspectos relevantes a través de métodos públicos.


    Ejemplo: 

		Programa para gestionar una biblioteca, debemos tener una clase que represente sus entidades, como una clase 'Libro' que representa a los libros de la biblioteca. 


	```java

	public class Libro {
	    private String titulo;
	    private String autor;
	    private int añoPublicacion;

	    // Constructor y métodos getter y setter...

	    public void prestar() {
	        // Implementación para prestar un libro
	    }

	    public void devolver() {
	        // Implementación para devolver un libro
	    }

	    // Otros métodos relevantes...
	}

	```

	La clase 'Libro' encapsula el comportamiento y el estado asociado con un libro. 

	Los detalles de implementación, sobre cómo se almacena el título o el autor, se mantienen ocultos dentro de la clase y solo se exponen a través de métodos públicos como 'getTitulo()' y 'getAutor()'. 

	Esto permite que otros objetos interactúen con un libro de manera abstracta, sin necesidad de conocer los detalles internos de cómo se implementa la clase Libro.




|| Abstracción
	
	Es la capacidad de representar las características esenciales de un objeto sin proporcionar detalles innecesarios o irrelevantes. 

	En otras palabras, la abstracción se trata de centrarse en los aspectos más importantes de un objeto y ocultar los detalles de implementación menos importantes.


	Principios: 

	1. Identificar Entidades Relevantes: 

		La abstracción comienza identificando las entidades relevantes en el problema que estás tratando de resolver.

		Estas entidades pueden ser objetos del mundo real o conceptos abstractos.


    2. Definir Clases y Objetos: 

    	Una vez identificadas las entidades, las representas en tu programa mediante clases y objetos en Java. 

    	Cada clase encapsula el comportamiento y el estado asociado con una entidad específica.


    3. Ocultar Detalles de Implementación: 

    	En la definición de una clase, te enfocas en los detalles esenciales y relevantes para la entidad que estás representando, mientras ocultas los detalles de implementación innecesarios. 

    	Esto se logra mediante la encapsulación, donde los detalles internos de la clase se mantienen privados y solo se exponen los aspectos relevantes a través de métodos públicos.


    Ejemplo: 

		Programa para gestionar una biblioteca, debemos tener una clase que represente sus entidades, como una clase 'Libro' que representa a los libros de la biblioteca. 


	```java

	public class Libro {
	    private String titulo;
	    private String autor;
	    private int añoPublicacion;

	    // Constructor y métodos getter y setter...

	    public void prestar() {
	        // Implementación para prestar un libro
	    }

	    public void devolver() {
	        // Implementación para devolver un libro
	    }

	    // Otros métodos relevantes...
	}

	```

	La clase 'Libro' encapsula el comportamiento y el estado asociado con un libro. 

	Los detalles de implementación, sobre cómo se almacena el título o el autor, se mantienen ocultos dentro de la clase y solo se exponen a través de métodos públicos como 'getTitulo()' y 'getAutor()'. 

	Esto permite que otros objetos interactúen con un libro de manera abstracta, sin necesidad de conocer los detalles internos de cómo se implementa la clase Libro.




|| Encapsulación
		
	Es la idea de agrupar datos y los métodos que operan sobre esos datos en una única unidad llamada clase. 

	Además, la encapsulación implica ocultar los detalles internos de implementación de una clase y proporcionar una interfaz pública consistente para interactuar con la misma.

	
	Principios: 

	1. Ocultar Detalles Internos:

        Los detalles internos de implementación, como la representación interna de los datos y la lógica de implementación de los métodos, se ocultan fuera de la clase. 

        Esto se conoce como ocultamiento de información.


    2. Proteger Datos:

        Los datos internos de una clase se protegen al proporcionar acceso controlado a través de métodos de la clase. 

        Esto evita que los datos sean modificados de manera inapropiada desde fuera de la clase.


    3. Proporcionar Interfaz Pública:

        Se define una interfaz pública consistente que especifica cómo interactuar con la clase. 

        Esta interfaz se compone de métodos públicos y actúa como un contrato entre la clase y el mundo exterior.


    4. Facilitar Mantenimiento:

        La encapsulación facilita el mantenimiento del código, ya que los cambios internos en la implementación de una clase no afectarán a las partes del programa que utilizan la clase, siempre y cuando la interfaz pública permanezca inalterada.


	```java

	public class Persona {
	    private String nombre;  // Campo encapsulado
	    private int edad;       // Campo encapsulado

	    // Constructor
	    public Persona(String nombre, int edad) {
	        this.nombre = nombre;
	        this.edad = edad;
	    }

	    // Métodos públicos para acceder a los campos encapsulados
	    public String getNombre() {
	        return nombre;
	    }

	    public void setNombre(String nombre) {
	        this.nombre = nombre;
	    }

	    public int getEdad() {
	        return edad;
	    }

	    public void setEdad(int edad) {
	        if (edad > 0) {
	            this.edad = edad;
	        }
	    }
	}

	```

	La clase 'Persona' encapsula los campos 'nombre' y 'edad'. 

	Los métodos 'get' y 'set' proporcionan una interfaz para acceder y modificar estos campos.

	La palabra clave 'private' asegura que los campos solo sean accesibles y modificables desde dentro de la propia clase. 

	Este enfoque permite un control más preciso sobre cómo se accede y se modifica la información interna de la clase.	

	```java

	public class EjemploEncapsulacion {
	    public static void main(String[] args) {
	        Persona persona = new Persona("Alice", 25);

	        // Acceder a los campos encapsulados mediante métodos públicos
	        System.out.println("Nombre: " + persona.getNombre());
	        System.out.println("Edad: " + persona.getEdad());

	        // Modificar los campos encapsulados mediante métodos públicos
	        persona.setNombre("Bob");
	        persona.setEdad(30);

	        System.out.println("Nuevo Nombre: " + persona.getNombre());
	        System.out.println("Nueva Edad: " + persona.getEdad());
	    }
	}

	```




|| Interface 
	
	Colección de métodos abstractos (sin implementación) y, a partir de Java 8, puede contener métodos con implementación (conocidos como métodos por defecto o default methods) y constantes (variables que no pueden ser modificadas). 

	Una interfaz define un contrato que las clases pueden implementar, especificando los métodos que deben proporcionar. Las interfaces permiten la creación de código más modular y facilitan la implementación de múltiples herencias


	Características: 

	1 .Métodos Abstractos:

    	Una interfaz puede contener métodos abstractos, que son declaraciones de métodos sin implementación.

    	```java

    	interface Forma {
		    void dibujar();  // Método abstracto
		}

    	```


    2. Métodos por Defecto (Default Methods):

    	A partir de Java 8, las interfaces pueden tener métodos con implementación proporcionando una implementación predeterminada para el método. 

    	Las clases que implementan la interfaz pueden optar por utilizar la implementación predeterminada o proporcionar su propia implementación

    	```java

    	interface Saludable {
		    default void saludar() {
		        System.out.println("¡Hola!");
		    }
		}

    	```


    3. Constantes:

   		Las interfaces pueden contener constantes, que son variables con valores que no pueden ser modificados. 

   		Estas constantes son implícitamente public, static y final.

   		```java

   		interface Colores {
		    int ROJO = 1;     // Constante
		    int VERDE = 2;    // Constante
		    int AZUL = 3;     // Constante
		}

   		```


   	4. Múltiple Herencia:

    	A diferencia de las clases, una clase puede implementar múltiples interfaces. 

    	Esto permite la implementación de múltiple herencia en Java.

    	```java

    	class Circulo implements Forma, Saludable {
		    @Override
		    public void dibujar() {
		        System.out.println("Dibujando un círculo");
		    }
		}

    	```


    Ejemplo: 

    ```java

    // Definir una interfaz
		interface Animal {
		    void hacerSonido();  // Método abstracto
		}

		// Implementar la interfaz en una clase
		class Perro implements Animal {
		    @Override
		    public void hacerSonido() {
		        System.out.println("Guau, guau");
		    }
		}

		// Otra implementación de la interfaz
		class Gato implements Animal {
		    @Override
		    public void hacerSonido() {
		        System.out.println("Miau, miau");
		    }
		}

		// Ejemplo de uso
		public class EjemploInterfaz {
		    public static void main(String[] args) {
		        Animal perro = new Perro();
		        perro.hacerSonido();  // Resultado: Guau, guau

		        Animal gato = new Gato();
		        gato.hacerSonido();   // Resultado: Miau, miau
		    }
		}


    ```



|| Contrato: 

	Conjunto de reglas y expectativas que establece cómo se deben utilizar y comportar las clases que implementan una interfaz o heredan de una clase base. 

	Un contrato establece las responsabilidades y garantías que deben cumplir las clases que participan en él.	

	
	1. Interfaz como contrato: 

		Se establece mediante los métodos declarados en la interfaz. 

		Cada clase que implementa la interfaz está obligada a proporcionar implementaciones concretas para todos los métodos declarados en esa interfaz. 

		Cada método en la interfaz representa una expectativa que se debe cumplir. 

		```java

		interface Forma {
		    void dibujar();
		    double calcularArea();
		}

		```

		Cualquier clase que implemente la interfaz Forma debe proporcionar una implementación para los métodos dibujar y calcularArea. 

		Este conjunto de métodos forma el contrato que las clases deben seguir.


	2. Herencia como Contrato:

    	En el caso de la herencia, una clase base define un conjunto de métodos y propiedades que las clases derivadas deben heredar. 

    	La clase base establece un contrato que las clases derivadas deben cumplir, lo que significa que deben proporcionar implementaciones concretas para todos los métodos definidos en la clase base.

    	```java

    	class Animal {
		    void hacerSonido() {
		        System.out.println("Sonido genérico de un animal");
		    }
		}

		class Perro extends Animal {
		    // Implementación específica para hacerSonido en la clase Perro
		    @Override
		    void hacerSonido() {
		        System.out.println("Guau, guau");
		    }
		}

    	```

    	En este ejemplo, la clase 'Animal' establece un contrato al definir el método 'hacerSonido'. 

    	La clase 'Perro', que hereda de 'Animal', debe proporcionar su propia implementación del método 'hacerSonido' para cumplir con el contrato.


    Características: 

    1. Interoperabilidad:

	    El contrato facilita la interoperabilidad entre clases y componentes. 

	    Las clases que cumplen con el mismo contrato pueden interactuar de manera eficiente y predecible, lo que facilita la construcción de sistemas complejos.


	2. Extensibilidad:

	    El contrato permite la extensibilidad del código.

	    Puedes introducir nuevas clases que implementen el mismo contrato sin afectar las partes existentes del sistema.


	3. Mantenimiento:

	    El contrato facilita el mantenimiento del código. 

	    Si una clase cumple con un contrato, se puede confiar en que cumplirá con las expectativas definidas por ese contrato, incluso si la implementación interna de la clase cambia.




|| Polimorfismo 
	
	Es la capacidad de un objeto de tomar muchas formas diferentes.

	El polimorfismo permite que un mismo nombre (como un método o una propiedad) se utilice de manera diferente en diferentes contextos. 

	Hay dos tipos principales de polimorfismo en POO: 

	1. Polimorfismo de tiempo de compilación (compile-time polymorphism o polimorfismo estático): 

		También conocido como sobrecarga de métodos o "overloading", este tipo de polimorfismo ocurre en tiempo de compilación. 

		En la sobrecarga de métodos, múltiples métodos en una clase tienen el mismo nombre pero diferentes listas de parámetros. 

		El compilador determina qué método llamar en función de la cantidad y tipos de argumentos proporcionados.

		```java

		public class EjemploPolimorfismoCompileTime {
		    // Sobrecarga de métodos
		    static int sumar(int a, int b) {
		        return a + b;
		    }

		    static double sumar(double a, double b) {
		        return a + b;
		    }

		    public static void main(String[] args) {
		        System.out.println(sumar(5, 10));       // Llama al primer método
		        System.out.println(sumar(3.5, 7.2));    // Llama al segundo método
		    }
		}

		```


	2. Polimorfismo de tiempo de ejecución (runtime polymorphism o polimorfismo dinámico): 

		También conocido como sobrescritura de métodos o "overriding", este tipo de polimorfismo ocurre en tiempo de ejecución. 

		En la sobrescritura de métodos, una clase hija proporciona una implementación específica para un método que ya está definido en su clase base. 

		La elección de qué método llamar se realiza en tiempo de ejecución, basándose en el tipo real del objeto.

		```java

		// Clase base
		class Animal {
		    void hacerSonido() {
		        System.out.println("Sonido genérico de un animal");
		    }
		}

		// Clase derivada que sobrescribe el método hacerSonido
		class Perro extends Animal {
		    @Override
		    void hacerSonido() {
		        System.out.println("Guau, guau");
		    }
		}

		public class EjemploPolimorfismoRunTime {
		    public static void main(String[] args) {
		        Animal miAnimal = new Perro();  // Crear una instancia de la clase derivada

		        miAnimal.hacerSonido();  // Llama al método sobrescrito en tiempo de ejecución
		    }
		}

		```



|| Manejo de excepciones

	Permite a los programadores controlar y responder a situaciones excepcionales o errores que pueden ocurrir durante la ejecución de un programa. 

	Las excepciones son eventos imprevistos que interrumpen el flujo normal de ejecución. 

	Al utilizar el manejo de excepciones, puedes escribir código que detecte, maneje y recupere de manera controlada de estos errores.

	Se manejan mediante el uso de bloques 'try', 'catch', 'finally' y, opcionalmente, la cláusula 'throws' en la firma de los métodos.


	1. Bloque try y catch:

		El bloque 'try' se utiliza para contener el código que podría generar una excepción.

		Dentro del bloque 'try', puedes tener uno o varios bloques 'catch' que capturan y manejan excepciones específicas.

	```java

	try {
	    // Código que podría generar una excepción
	    // Por ejemplo, división entre cero
	    int resultado = 10 / 0;
	} catch (ArithmeticException e) {
	    // Manejar la excepción específica
	    System.out.println("Error de división por cero: " + e.getMessage());
	} catch (Exception e) {
	    // Manejar excepciones generales
	    System.out.println("Ocurrió una excepción: " + e.getMessage());
	} finally {
	    // Bloque opcional que siempre se ejecutará, ocurra o no una excepción
	    System.out.println("Este bloque siempre se ejecuta.");
	}

	```

	Si ocurre una excepción durante la división entre cero, el control se transfiere al bloque 'catch' correspondiente (ArithmeticException). 

	Si no coincide con el tipo de excepción esperado, se intentará con el siguiente bloque 'catch'. 

	El bloque 'finally' se ejecutará siempre, independientemente de si se produjo una excepción o no.


	2. Cláusula throws:

		La cláusula 'throws' se utiliza en la firma de un método para indicar que el método puede lanzar ciertos tipos de excepciones. 

		Los métodos que lanzan excepciones deben declarar las excepciones usando throws o manejarlas internamente con bloques try-catch.

	```java

	public void miMetodo() throws MiExcepcion {
	    // Código que podría lanzar la excepción MiExcepcion
	    if (condicion) {
	        throw new MiExcepcion("Ocurrió un error");
	    }
	}

	```

	'miMetodo' puede lanzar una excepción de tipo 'MiExcepcion'.
	
	Quien llame a este método deberá manejar esta excepción o declararla en su propia firma usando 'throws'	


	3. Excepciones Personalizadas

		Puedes crear tus propias excepciones personalizadas extendiendo la clase Exception o alguna de sus subclases. 

		Esto te permite definir excepciones específicas para tu aplicación.

		```java

		class MiExcepcion extends Exception {
		    public MiExcepcion(String mensaje) {
		        super(mensaje);
		    }
		}

		```

		Luego, puedes lanzar y manejar instancias de esta excepción en tu código.

		```java

		try {
		    throw new MiExcepcion("Ocurrió un error personalizado");
		} catch (MiExcepcion e) {
		    System.out.println("Manejando MiExcepcion: " + e.getMessage());
		}

		```


	El manejo de excepciones permiten escribir código que pueda anticipar y gestionar situaciones excepcionales, mejorando la robustez y la fiabilidad de tus programas. 

	Es crucial para desarrollar software que pueda responder adecuadamente a condiciones imprevistas durante la ejecución.



|| Buenas prácticas para Objetos

	1. Sigue los Principios SOLID:

    	S (Responsabilidad Única):

    		Cada clase debería tener una única razón para cambiar.


    	O (Abierto/Cerrado): 

    		Las clases deben estar abiertas para la extensión pero cerradas para la modificación.


    	L (Sustitución de Liskov):

    		Los objetos de una superclase deberían ser reemplazables por objetos de sus subclases.


    	I (Segregación de Interfaces): 

    		No deberías ser obligado a depender de interfaces que no utilizas.


    	D (Inversión de Dependencia):

    		Deberías depender de abstracciones, no de implementaciones concretas.


	2. Encapsulamiento:

	    Oculta los detalles internos de una clase y expone solo lo que es necesario.

	    Utiliza modificadores de acceso (public, private, protected) para controlar el acceso a los miembros de la clase.


	3. Herencia y Composición:

	    Prefiere la composición sobre la herencia cuando sea posible.

	    Usa la herencia de manera cuidadosa, evitando jerarquías profundas y frágiles.


	4. Polimorfismo:

	    Aprovecha el polimorfismo para permitir que objetos de diferentes clases sean tratados de manera uniforme a través de interfaces comunes.


	5. Interfaces:

	    Define interfaces claras y cohesivas para abstraer comportamientos comunes.

	    Las interfaces deben ser pequeñas y centradas en un propósito específico.


	6. Evita el Acoplamiento Excesivo:

	    Minimiza las dependencias entre clases para hacer el sistema más flexible y fácil de mantener.

	    Utiliza patrones de diseño como Inyección de Dependencias para reducir el acoplamiento.


	7. Evita Clases Demasiado Grandes:

	    Divide clases grandes en clases más pequeñas y cohesivas que realicen tareas específicas.


	8. Nombres Significativos:

	    Elige nombres descriptivos y significativos para clases, métodos y variables.

	    Sigue convenciones de nomenclatura Java (CamelCase para nombres de variables y métodos, PascalCase para nombres de clases).


	9. Mantenlo Simple:

	    Sigue el principio KISS (Keep It Simple, Stupid). 

	    Evita complejidades innecesarias.


	10. Pruebas Unitarias:

	    Escribe pruebas unitarias para validar el comportamiento de tus clases y métodos.

	    Utiliza frameworks de pruebas como JUnit.


	11. Documentación Clara:

	    Proporciona comentarios y documentación clara para explicar el propósito y uso de tus clases y métodos.


	12. Versionamiento:

	    Utiliza sistemas de control de versiones como Git para rastrear cambios en tu código.


	13. Manejo de Excepciones:

	    Maneja las excepciones de manera adecuada y evita el uso excesivo de bloques try-catch.


	14. Diseño Defensivo:

	    Valida las entradas y salidas para evitar errores y comportamientos inesperados.


	15. Consistencia de Estilo:

	    Mantén un estilo de codificación consistente en todo el proyecto. 

	    Puedes seguir las convenciones de estilo Java (por ejemplo, Java Code Conventions).



|| Convensión de nomenclatura

	Son reglas que especifican cómo se deben nombrar los identificadores, como variables, métodos, clases, etc. 

	Estas convenciones ayudan a que el código sea más legible y comprensible.	


	1. Nombres de Clases:

    	Utiliza PascalCase para nombres de clases.

    	Ejemplo: MiClase, Empleado, ConexionBD


	2. Nombres de Interfaces:

	    Utiliza el mismo formato que para las clases (PascalCase).

	    Ejemplo: MiInterfaz, Serializable, Comparable


	3. Nombres de Métodos:

	    Utiliza camelCase para nombres de métodos.

	    Ejemplo: calcularTotal(), obtenerNombre(), conectarBD()


	4. Nombres de Variables:

	    Utiliza camelCase para nombres de variables.

	    Ejemplo: numeroEstudiantes, precioProducto, nombreUsuario


	5. Nombres de Constantes:

	    Utiliza MAYÚSCULAS con guiones bajos para separar palabras en nombres de constantes.

	    Ejemplo: MAXIMO_VALOR, CANTIDAD_MAXIMA, PI


	6. Nombres de Paquetes:

	    Utiliza letras minúsculas y evita el uso de mayúsculas.

	    Ejemplo: com.miempresa.miproducto, org.ejemplo.paquete


	7. Convenciones para Booleans:

	    Utiliza prefijos como is, has, o can para nombres de variables booleanas.

	    Ejemplo: esActivo, tienePermiso, puedeEditar


	8. Convenciones para Acrónimos:

	    Acrónimos de dos letras deben estar en mayúsculas. 

	    Acrónimos más largos deben seguir las reglas de camelCase.

	    Ejemplo: HTTPConnection, IOStream, XMLParser


	9. Evitar Nombres de Una Letra:

	    A menos que sea un índice de bucle (i, j, k) o un objeto de colección, evita nombres de una letra.

	    Utiliza nombres descriptivos para mejorar la legibilidad.


	10. Nombres Descriptivos:

	    Elige nombres que sean descriptivos y que indiquen claramente el propósito del identificador.


	11. Convenciones para Métodos Getters y Setters:

	    Utiliza 'getNombreVariable()' y 'setNombreVariable()'' para métodos getters y setters.

	    Ejemplo: getNombre(), setEdad(int edad).


	12. Convenciones para Constructores:

	    Utiliza nombres descriptivos y significativos para los constructores.

	    Puedes usar camelCase o PascalCase según tu preferencia.



|| KISS

	Keep It Simple, Stupid es un principio de diseño y desarrollo de software que aboga por la simplicidad y la claridad en la creación de sistemas y programas.

	Este principio se atribuye a Kelly Johnson, un ingeniero aeroespacial de la Lockheed Skunk Works, y ha sido adoptado en la programación y en diversos campos de diseño.


	Principios:

	1. Simplicidad:

	    Aboga por soluciones sencillas en lugar de soluciones complejas.

	    Prefiere la claridad y la comprensión directa del código.


	2. Eliminar Complejidades Innecesarias:

	    Evita agregar características, código o estructuras que no sean esenciales para el funcionamiento del sistema.

	    Elimina código redundante y complicaciones no justificadas.


	3. Facilita la Comprensión:

	    Un código simple es más fácil de entender y mantener.

	    Mejora la legibilidad y reduce la probabilidad de errores.


	4. Menos Propenso a Errores:

	    Menos código y menos complejidad reducen la posibilidad de introducir errores.

	    Facilita la identificación y corrección de problemas.


	5. Diseño Efectivo:

	    Se centra en la efectividad y la funcionalidad esencial en lugar de en características avanzadas innecesarias.

	    Simplifica el diseño para lograr el objetivo principal.	


	KISS en programación: 

	1. Diseño de Algoritmos:

	    Prefiere algoritmos simples y eficientes sobre algoritmos complicados.

	    Evita la sobreoptimización que puede aumentar la complejidad sin proporcionar beneficios significativos.


	2. Estructuras de Datos:

	    Utiliza estructuras de datos simples y apropiadas para el problema en cuestión.

	    Evita estructuras demasiado complejas si no son necesarias.


	3. Mantenimiento del Código:

	    Escribe código que sea fácil de entender para otros desarrolladores y para ti mismo en el futuro.

	    Documenta donde sea necesario, pero no exageres.


	4. Interfaz de Usuario:

	    Diseña interfaces de usuario simples y fáciles de usar.

	    Evita la sobrecarga de características que pueden confundir a los usuarios.


	5. Manejo de Errores:

	    Diseña manejo de errores claro y directo.

	    Evita construcciones complejas que dificulten la depuración.


	6. Escalabilidad:

	    Prefiere soluciones escalables y flexibles, pero no añadas complejidad innecesaria en previsión de posibles expansiones futuras que podrían no ser necesarias.



|| Validación de entradas y salidas

	Práctica de verificar y asegurar que los datos que ingresan o salen de una parte del programa cumplan con ciertos criterios o restricciones específicas. 

	Esto se hace para prevenir errores, mejorar la robustez del software y garantizar que el programa funcione de manera predecible y segura.


	1. Validación de Entradas:

    Datos del Usuario:

        Al recibir datos del usuario a través de la interfaz de usuario, como formularios, asegúrate de que los datos ingresados sean del tipo y formato correctos.

        Verifica la longitud, el formato, y la validez semántica de los datos.


    Parámetros de Funciones y Métodos:
        
        Antes de procesar los datos dentro de una función o método, valida que los parámetros cumplen con los requisitos esperados.

        Verifica si los valores están dentro de rangos aceptables y si son del tipo correcto.


    Datos Externos:

        Al interactuar con fuentes externas, como archivos, bases de datos o servicios web, valida los datos antes de procesarlos.

        Evita procesar datos corruptos o maliciosos que podrían comprometer la integridad del sistema.


    Prevención de Inyección de Datos:
        
        Para evitar vulnerabilidades como la inyección de SQL, asegúrate de que los datos ingresados por el usuario no puedan ser interpretados como comandos o instrucciones maliciosas.


	2. Validación de Salidas:

	Datos Mostrados al Usuario:
	
		Antes de presentar datos al usuario, verifica que estén formateados correctamente y que no contengan información confidencial o incorrecta.
	
		Evita la presentación de datos que podrían ser confusos o malinterpretados.


    Datos Enviados a Otros Sistemas:
       
        Cuando el programa envía datos a otros sistemas, como servicios web, asegúrate de que los datos cumplen con los requisitos de ese sistema.

        Verifica la integridad y el formato de los datos antes de enviarlos.


    Prevención de Errores de Codificación:

        Asegúrate de que los datos generados por el programa, ya sea para su almacenamiento, presentación o envío, estén libres de errores de codificación que puedan causar malentendidos o problemas en otros sistemas.



|| SOLID
	
	Son un conjunto de cinco principios de diseño de software que, cuando se aplican correctamente, ayudan a crear sistemas más comprensibles, flexibles y mantenibles. 

	Fueron introducidos por Robert C. Martin, representan una guía para desarrolladores que buscan escribir código más eficiente y escalable.


	1. Principio de Responsabilidad Única (SRP):

		Definición:

	    	Una clase debe tener una sola razón para cambiar, es decir, debe tener una única responsabilidad.

		Implicaciones:

	    	Cada clase debe tener un propósito específico y no debe asumir responsabilidades que no le correspondan.
	    	
	    	Facilita la comprensión, el mantenimiento y la evolución del código.


	2. Principio de Abierto/Cerrado (OCP):

		Definición:

	    	Una clase debe estar abierta para la extensión pero cerrada para la modificación.

		Implicaciones:

	    	Deberías poder extender el comportamiento de una clase sin modificar su código fuente.

	    	Se logra mediante el uso de interfaces, herencia y polimorfismo.


	3. Principio de Sustitución de Liskov (LSP):

		Definición:

	    	Las subclases deben ser sustituibles por sus clases base sin afectar la funcionalidad del programa.

		Implicaciones:

	   		Las clases derivadas deben ser coherentes con las clases base en términos de comportamiento.

	    	Garantiza que las subclases cumplan con el contrato establecido por las clases base.


	4. Principio de Segregación de Interfaces (ISP):

		Definición:

	    	Un cliente no debe verse obligado a depender de interfaces que no utiliza.

		Implicaciones:

	    	Divide interfaces grandes en interfaces más pequeñas y específicas.

	    	Evita que las clases implementen métodos que no necesitan.


	5. Principio de Inversión de Dependencias (DIP):

		Definición:

	    	Las dependencias deben ser sobre abstracciones, no sobre implementaciones concretas.

		Implicaciones:

	    	Las clases de alto nivel no deben depender de clases de bajo nivel, sino de abstracciones.
	    	
	    	Promueve el uso de interfaces y abstracciones para reducir el acoplamiento.




|| Superclase y Subclase
	
	Los términos están relacionados con la herencia. 


    Superclase:

        También conocida como clase base o clase padre, una superclase es una clase que es extendida o subclase por otra clase.

        La superclase contiene atributos y métodos comunes que pueden ser compartidos por una o más subclases.

        Proporciona una estructura común y funcionalidades básicas que las subclases pueden heredar y extender según sea necesario.

        En Java, la palabra clave 'extends' se utiliza para indicar que una clase está extendiendo otra, es decir, que es una subclase de esa superclase.


    Subclase:

        También conocida como clase derivada o clase hija, una subclase es una clase que hereda atributos y métodos de una superclase.

        Puede añadir nuevos atributos y métodos o sobrescribir (redefinir) los métodos existentes de la superclase.

        Permite la reutilización de código y la especialización de comportamientos.

        En Java, una subclase se declara utilizando la palabra clave 'extends' seguida del nombre de la superclase.

	
	```java

	// Superclase
	class Vehiculo {
	    String marca;
	    int año;

	    // Constructor
	    public Vehiculo(String marca, int año) {
	        this.marca = marca;
	        this.año = año;
	    }

	    // Método de la superclase
	    void mostrarInformacion() {
	        System.out.println("Vehículo de marca " + marca + ", año " + año);
	    }
	}

	// Subclase que extiende la superclase Vehiculo
	class Coche extends Vehiculo {
	    int numeroPuertas;

	    // Constructor de la subclase
	    public Coche(String marca, int año, int numeroPuertas) {
	        // Llamada al constructor de la superclase
	        super(marca, año);
	        this.numeroPuertas = numeroPuertas;
	    }

	    // Método específico de la subclase
	    void mostrarInformacionCoche() {
	        System.out.println("Coche de marca " + marca + ", año " + año + ", " + numeroPuertas + " puertas");
	    }

	    // Sobrescritura del método de la superclase
	    @Override
	    void mostrarInformacion() {
	        // Se puede modificar el comportamiento del método de la superclase
	        System.out.println("Información del coche: " + marca + ", año " + año + ", " + numeroPuertas + " puertas");
	    }
	}

	public class EjemploHerencia {
	    public static void main(String[] args) {
	        // Crear un objeto de la subclase Coche
	        Coche miCoche = new Coche("Toyota", 2022, 4);

	        // Llamar a métodos de la superclase y subclase
	        miCoche.mostrarInformacion(); // Utiliza el método sobrescrito de la subclase
	        miCoche.mostrarInformacionCoche(); // Utiliza el método específico de la subclase
	    }
	}

	```
 	
 	'Vehiculo' es la superclase, y 'Coche' es la subclase que extiende Vehiculo. 

 	La subclase hereda los atributos y métodos de la superclase y puede agregar funcionalidades específicas. 

 	También se ilustra la sobrescritura del método 'mostrarInformacion()' en la subclase 'Coche'. 



|| Abstracción sobre Implementación
	
	Este principio enfatiza la importancia de programar contra interfaces y abstracciones en lugar de depender directamente de implementaciones concretas. 

	Al hacerlo, se logra un código más flexible, mantenible y resistente a cambios.
	
	Simplifica las pruebas unitarias, ya que puedes utilizar mocks o stubs para simular el comportamiento de las implementaciones concretas durante las pruebas.


	Ejemplo 1: 

	```java

	// Dependiendo de la abstracción (Interfaz)
	public interface Reproducible {
	    void reproducir();
	}

	// Implementación concreta
	public class Reproductor implements Reproducible {
	    @Override
	    public void reproducir() {
	        // Lógica para reproducir
	    }
	}

	// Cliente que depende de la abstracción (Interfaz)
	public class ClienteReproductor {
	    private Reproducible reproductor;

	    public ClienteReproductor(Reproducible reproductor) {
	        this.reproductor = reproductor;
	    }

	    public void iniciarReproduccion() {
	        reproductor.reproducir();
	    }
	}

	```

	'ClienteReproductor' depende de la abstracción Reproducible en lugar de depender directamente de la implementación concreta 'Reproductor'. 

	Esto permite cambiar fácilmente la implementación concreta sin modificar el código del cliente.



	Ejemplo 2: 

		```java

		// Definición de la clase abstracta Libro
		public abstract class Libro {
		    private String titulo;
		    private String autor;

		    public Libro(String titulo, String autor) {
		        this.titulo = titulo;
		        this.autor = autor;
		    }

		    // Métodos abstractos para representar comportamientos específicos
		    public abstract void mostrarDetalles();
		    public abstract void prestar();
		    public abstract void devolver();
		}

		// Implementación concreta de un libro específico
		public class LibroFisico extends Libro {
		    private int numeroPaginas;

		    public LibroFisico(String titulo, String autor, int numeroPaginas) {
		        super(titulo, autor);
		        this.numeroPaginas = numeroPaginas;
		    }

		    @Override
		    public void mostrarDetalles() {
		        System.out.println("Libro Físico: " + titulo + " de " + autor + ", " + numeroPaginas + " páginas.");
		    }

		    @Override
		    public void prestar() {
		        System.out.println("Libro físico prestado.");
		    }

		    @Override
		    public void devolver() {
		        System.out.println("Libro físico devuelto.");
		    }
		}

		// Implementación concreta de otro tipo de libro
		public class LibroElectronico extends Libro {
		    private double tamanoMB;

		    public LibroElectronico(String titulo, String autor, double tamanoMB) {
		        super(titulo, autor);
		        this.tamanoMB = tamanoMB;
		    }

		    @Override
		    public void mostrarDetalles() {
		        System.out.println("Libro Electrónico: " + titulo + " de " + autor + ", " + tamanoMB + " MB.");
		    }

		    @Override
		    public void prestar() {
		        System.out.println("Libro electrónico prestado.");
		    }

		    @Override
		    public void devolver() {
		        System.out.println("Libro electrónico devuelto.");
		    }
		}


		```


	Este principio está estrechamente relacionado con otros principios de diseño, como la inversión de dependencias (Dependency Inversion Principle, DIP) y la inversión de control (Inversion of Control, IoC). 

	La inversión de dependencias sugiere que las clases de alto nivel no deberían depender de clases de bajo nivel, sino de abstracciones. 

	La inversión de control se refiere a la inversión del flujo de control desde el código cliente a un contenedor o marco de trabajo que maneja la creación y gestión de objetos.



	Ejemplo 3: 

		Usando una clase abstracta 

	```java

	// Clase abstracta que representa la abstracción de una forma geométrica
	abstract class FormaGeometrica {
	    // Método abstracto para calcular el área (sin implementación aquí)
	    public abstract double calcularArea();

	    // Método concreto que se aplica a todas las formas geométricas
	    public void mostrarDescripcion() {
	        System.out.println("Esta es una forma geométrica.");
	    }
	}

	// Clase concreta que representa un círculo
	class Circulo extends FormaGeometrica {
	    private double radio;

	    public Circulo(double radio) {
	        this.radio = radio;
	    }

	    @Override
	    public double calcularArea() {
	        return Math.PI * Math.pow(radio, 2);
	    }
	}

	// Clase concreta que representa un rectángulo
	class Rectangulo extends FormaGeometrica {
	    private double longitud;
	    private double ancho;

	    public Rectangulo(double longitud, double ancho) {
	        this.longitud = longitud;
	        this.ancho = ancho;
	    }

	    @Override
	    public double calcularArea() {
	        return longitud * ancho;
	    }
	}

	public class EjemploAbstraccion {
	    public static void main(String[] args) {
	        // Crear instancias de formas geométricas
	        Circulo circulo = new Circulo(5.0);
	        Rectangulo rectangulo = new Rectangulo(4.0, 6.0);

	        // Utilizar la abstracción para trabajar con formas geométricas genéricas
	        FormaGeometrica forma1 = circulo;
	        FormaGeometrica forma2 = rectangulo;

	        // Llamar a métodos abstractos y concretos sin conocer los detalles específicos
	        System.out.println("Área del círculo: " + forma1.calcularArea());
	        forma1.mostrarDescripcion();

	        System.out.println("Área del rectángulo: " + forma2.calcularArea());
	        forma2.mostrarDescripcion();
	    }
	}

	```

	'FormaGeometrica' es una clase abstracta que representa la abstracción de una forma geométrica. 

	Contiene un método abstracto 'calcularArea()' que debe ser implementado por las clases concretas. 

	Además, tiene un método concreto 'mostrarDescripcion()' que se aplica a todas las formas geométricas.

	Las clases 'Circulo' y 'Rectangulo' son clases concretas que extienden 'FormaGeometrica' y proporcionan implementaciones específicas para calcular el área. 

	En el main del programa, se crean instancias de círculo y rectángulo, pero se almacenan en referencias de tipo 'FormaGeometrica', lo que permite trabajar con ellas de manera genérica. 

	Esto ilustra el uso de la abstracción para simplificar el código y manejar formas geométricas sin conocer sus detalles específicos.


	Ejemplo 4: 

	```java

	// Abstracción: Interfaz que define el servicio de envío
	interface ServicioEnvio {
	    void enviarPaquete(String destino);
	}

	// Implementación concreta 1: Envío terrestre
	class EnvioTerrestre implements ServicioEnvio {
	    @Override
	    public void enviarPaquete(String destino) {
	        System.out.println("Enviando paquete por tierra a " + destino);
	        // Lógica específica de envío terrestre
	    }
	}

	// Implementación concreta 2: Envío aéreo
	class EnvioAereo implements ServicioEnvio {
	    @Override
	    public void enviarPaquete(String destino) {
	        System.out.println("Enviando paquete por aire a " + destino);
	        // Lógica específica de envío aéreo
	    }
	}

	// Contexto: Clase que utiliza la abstracción
	class Cliente {
	    private ServicioEnvio servicioEnvio;

	    // Constructor que recibe la implementación concreta deseada
	    public Cliente(ServicioEnvio servicioEnvio) {
	        this.servicioEnvio = servicioEnvio;
	    }

	    // Método que utiliza la abstracción
	    public void enviarPaquete(String destino) {
	        servicioEnvio.enviarPaquete(destino);
	    }
	}

	// Clase principal que demuestra el uso de abstracción e implementación
	public class EjemploAbstraccionImplementacion {
	    public static void main(String[] args) {
	        // Crear instancias de las implementaciones concretas
	        EnvioTerrestre envioTerrestre = new EnvioTerrestre();
	        EnvioAereo envioAereo = new EnvioAereo();

	        // Utilizar la abstracción con diferentes implementaciones
	        Cliente clienteTerrestre = new Cliente(envioTerrestre);
	        clienteTerrestre.enviarPaquete("Ciudad A");

	        Cliente clienteAereo = new Cliente(envioAereo);
	        clienteAereo.enviarPaquete("Ciudad B");
	    }
	}

	```

	'ServicioEnvio' es la abstracción que define el servicio de envío.

	Las clases 'EnvioTerrestre' y 'EnvioAereo' son implementaciones concretas que proporcionan la lógica específica para el envío terrestre y aéreo, respectivamente. 

	La clase 'Cliente' utiliza la abstracción para enviar paquetes sin conocer los detalles específicos de la implementación concreta. 

	Este enfoque permite agregar fácilmente nuevas implementaciones de envío sin cambiar el código en la clase 'Cliente', siguiendo el principio de abstracción e implementación.



|| Inyección de Dependencias
	
	Es un patrón de diseño en el que las dependencias de un objeto son proporcionadas externamente en lugar de ser creadas internamente. 

	Este patrón tiene como objetivo reducir el acoplamiento entre componentes, mejorar la modularidad y facilitar la prueba unitaria al hacer que las dependencias sean más flexibles y fáciles de cambiar.


	Componentes: 

	1. Cliente:

    	El cliente es el componente que necesita ciertas funcionalidades o servicios para cumplir su propósito.


	2. Servicio (o Dependencia):

	    El servicio es la dependencia requerida por el cliente. Puede ser cualquier objeto, clase o componente que el cliente necesite para realizar su tarea.


	3. Inyector (o Contenedor de Inversión de Control, IoC):

	    El inyector es responsable de proporcionar las dependencias al cliente. 

	    Puede ser un contenedor de IoC que gestiona y suministra las dependencias.	


	Dos formas de Implementación: 

	1. Constructor:

    	La inyección de dependencias se realiza a menudo a través de un constructor. 

    	El cliente declara las dependencias como parámetros en su constructor.

    	```java

		public class Cliente {
		    private Servicio servicio;

		    // Inyección de dependencias a través del constructor
		    public Cliente(Servicio servicio) {
		        this.servicio = servicio;
		    }

		    public void realizarTarea() {
		        // Utilizar el servicio
		        servicio.realizarAccion();
		    }
		}

    	```


	2. Setter (Método de Configuración):

    	En lugar de inyectar dependencias a través del constructor, se pueden proporcionar mediante métodos setter.

    	```java

    	public class Cliente {
		    private Servicio servicio;

		    // Setter para la inyección de dependencias
		    public void setServicio(Servicio servicio) {
		        this.servicio = servicio;
		    }

		    public void realizarTarea() {
		        // Utilizar el servicio
		        servicio.realizarAccion();
		    }
		}

    	```


	Ventajas de la Inyección de Dependencias:

	    Desacoplamiento:
	        
	        Reduce el acoplamiento entre componentes al no requerir que el cliente conozca cómo crear sus dependencias.


	    Flexibilidad:

	        Facilita el cambio de implementaciones de dependencias sin modificar el código del cliente.


	    Pruebas Unitarias:

	        Facilita las pruebas unitarias al permitir la sustitución de implementaciones reales por implementaciones de prueba.


	    Modularidad:

	        Mejora la modularidad del código al dividir la creación de objetos y la lógica de negocio.


	Implementación con Contenedor de IoC:

		En muchos casos, la inyección de dependencias se implementa mediante un contenedor de IoC, como Spring en Java.

		Este tipo de contenedores gestionan la creación y administración de objetos, así como la inyección de dependencias automáticamente

		```java

		public class Cliente {
		    private Servicio servicio;

		    // Inyección de dependencias a través de Spring
		    public Cliente(Servicio servicio) {
		        this.servicio = servicio;
		    }

		    public void realizarTarea() {
		        // Utilizar el servicio
		        servicio.realizarAccion();
		    }
		}

		```

		Spring se encargaría de crear la instancia de Cliente y proporcionar la implementación de Servicio al momento de la creación.


	La Inyección de Dependencias es una técnica poderosa que promueve la construcción de sistemas más flexibles y mantenibles al reducir las dependencias directas entre los componentes.



|| Interfaces Comunes
	
	Se refiere al uso de interfaces para establecer contratos comunes que varias clases pueden implementar. 

	Una interfaz define un conjunto de métodos que las clases deben implementar, pero no proporciona la implementación real de esos métodos. 

	Esto permite que múltiples clases compartan un comportamiento común a través de la implementación de la misma interfaz.
	

	Ejemplo: 

		Interfaz llamada 'Reproducible' que define un método abstracto (sin implementación) reproducir para objetos que pueden reproducirse:

	```java

	public interface Reproducible {
	    void reproducir();
	}

	```

	Varias clases pueden implementar esta interfaz para indicar que son capaces de reproducirse:

	```java

	public class Mamifero implements Reproducible {
	    @Override
	    public void reproducir() {
	        // Lógica de reproducción para mamíferos
	    }
	}

	public class Pajaro implements Reproducible {
	    @Override
	    public void reproducir() {
	        // Lógica de reproducción para aves
	    }
	}

	public class Pez implements Reproducible {
	    @Override
	    public void reproducir() {
	        // Lógica de reproducción para peces
	    }
	}

	```


	Ejemplo 2: 

	```java

	// Definición de una interfaz que representa un dispositivo electrónico
	interface DispositivoElectronico {
	    void encender();
	    void apagar();
	    boolean estaEncendido();
	}

	// Clase que implementa la interfaz para un televisor
	class Televisor implements DispositivoElectronico {
	    private boolean encendido;

	    @Override
	    public void encender() {
	        System.out.println("Encendiendo el televisor");
	        encendido = true;
	    }

	    @Override
	    public void apagar() {
	        System.out.println("Apagando el televisor");
	        encendido = false;
	    }

	    @Override
	    public boolean estaEncendido() {
	        return encendido;
	    }
	}

	// Clase que implementa la interfaz para una lámpara
	class Lampara implements DispositivoElectronico {
	    private boolean encendido;

	    @Override
	    public void encender() {
	        System.out.println("Encendiendo la lámpara");
	        encendido = true;
	    }

	    @Override
	    public void apagar() {
	        System.out.println("Apagando la lámpara");
	        encendido = false;
	    }

	    @Override
	    public boolean estaEncendido() {
	        return encendido;
	    }
	}

	public class EjemploInterfaz {
	    public static void main(String[] args) {
	        // Uso de la interfaz para trabajar con diferentes dispositivos electrónicos
	        DispositivoElectronico tv = new Televisor();
	        DispositivoElectronico lampara = new Lampara();

	        // Encender y apagar el televisor
	        tv.encender();
	        System.out.println("¿El televisor está encendido? " + tv.estaEncendido());
	        tv.apagar();
	        System.out.println("¿El televisor está encendido? " + tv.estaEncendido());

	        // Encender y apagar la lámpara
	        lampara.encender();
	        System.out.println("¿La lámpara está encendida? " + lampara.estaEncendido());
	        lampara.apagar();
	        System.out.println("¿La lámpara está encendida? " + lampara.estaEncendido());
	    }
	}

	```

	'DispositivoElectronico' es una interfaz que define tres métodos: 'encender()', 'apagar()' y 'estaEncendido()'. 

	Las clases 'Televisor' y 'Lampara' implementan esta interfaz proporcionando sus propias implementaciones para esos métodos.

	En el main del programa, se crean instancias de 'Televisor' y 'Lampara', pero se almacenan en referencias de tipo 'DispositivoElectronico'. 

	Esto permite tratar ambas instancias de manera uniforme, ya que ambas implementan la interfaz 'DispositivoElectronico'. 

	Este es un ejemplo de cómo las interfaces en Java pueden proporcionar una forma de lograr la abstracción y la flexibilidad en la programación orientada a objetos.


	Ejemplo 3: 

	```java

	// Definición de una interfaz llamada Trabajador
	interface Trabajador {
	    // Métodos abstractos (sin implementación)
	    void trabajar();

	    double calcularSalario();
	}

	// Clase que implementa la interfaz Trabajador
	class Empleado implements Trabajador {
	    private String nombre;
	    private double salarioBase;

	    // Constructor
	    public Empleado(String nombre, double salarioBase) {
	        this.nombre = nombre;
	        this.salarioBase = salarioBase;
	    }

	    // Implementación del método trabajar de la interfaz
	    @Override
	    public void trabajar() {
	        System.out.println(nombre + " está trabajando duro.");
	    }

	    // Implementación del método calcularSalario de la interfaz
	    @Override
	    public double calcularSalario() {
	        // Implementación específica para calcular el salario del empleado
	        return salarioBase;
	    }
	}

	// Otra clase que implementa la interfaz Trabajador
	class Freelancer implements Trabajador {
	    private String nombre;
	    private double tarifaPorHora;
	    private int horasTrabajadas;

	    // Constructor
	    public Freelancer(String nombre, double tarifaPorHora, int horasTrabajadas) {
	        this.nombre = nombre;
	        this.tarifaPorHora = tarifaPorHora;
	        this.horasTrabajadas = horasTrabajadas;
	    }

	    // Implementación del método trabajar de la interfaz
	    @Override
	    public void trabajar() {
	        System.out.println(nombre + " está trabajando como freelancer.");
	    }

	    // Implementación del método calcularSalario de la interfaz
	    @Override
	    public double calcularSalario() {
	        // Implementación específica para calcular el salario del freelancer
	        return tarifaPorHora * horasTrabajadas;
	    }
	}

	// Clase principal que demuestra el uso de la interfaz
	public class EjemploInterfaz {
	    public static void main(String[] args) {
	        // Crear un objeto de la clase Empleado
	        Empleado empleado = new Empleado("Juan", 50000.0);

	        // Llamar a los métodos de la interfaz a través del objeto Empleado
	        empleado.trabajar();
	        System.out.println("Salario del empleado: $" + empleado.calcularSalario());

	        // Crear un objeto de la clase Freelancer
	        Freelancer freelancer = new Freelancer("Ana", 25.0, 20);

	        // Llamar a los métodos de la interfaz a través del objeto Freelancer
	        freelancer.trabajar();
	        System.out.println("Salario del freelancer: $" + freelancer.calcularSalario());
	    }
	}

	```

	La interfaz 'Trabajador' define dos métodos abstractos ('trabajar' y 'calcularSalario'). 

	Las clases 'Empleado' y 'Freelancer' implementan esta interfaz y proporcionan implementaciones concretas para estos métodos. 

	El programa principal demuestra cómo se pueden llamar a los métodos de la interfaz a través de objetos de las clases que implementan la interfaz.




|| Composición sobre Herencia
	
	La composición es un principio de diseño en programación orientada a objetos (POO) que sugiere que, en lugar de extender una clase a través de la herencia, es preferible componerla utilizando otras clases como componentes.

	Este principio resalta los beneficios de construir sistemas flexibles y mantenibles mediante la composición de objetos en lugar de depender en gran medida de la jerarquía de herencia.	


	Ejemplo:

		En lugar de extender una clase 'Vehiculo' a través de la herencia, podríamos componerla utilizando diferentes clases para representar partes específicas de un vehículo, como Motor, Ruedas, etc.


	```java

	public class Vehiculo {
	    private Motor motor;
	    private Ruedas ruedas;

	    public Vehiculo(Motor motor, Ruedas ruedas) {
	        this.motor = motor;
	        this.ruedas = ruedas;
	    }

	    public void iniciar() {
	        motor.arrancar();
	        // Lógica para iniciar el vehículo
	    }

	    public void conducir() {
	        ruedas.girar();
	        // Lógica para conducir el vehículo
	    }
	}

	```

	'Vehiculo' está compuesto por un Motor y unas Ruedas. 

	Esto proporciona mayor flexibilidad para crear diferentes tipos de vehículos al combinar diferentes componentes.


	Uso de Herencia: 

		Hay situaciones en las que la herencia tiene sentido y es apropiada. 

		Por ejemplo, cuando se quiere establecer una relación de "es un" clara y directa entre dos clases, la herencia puede ser la elección adecuada.

		La clave es no depender exclusivamente de la herencia como el único mecanismo para la creación de jerarquías de clases, sino considerar la composición como una herramienta poderosa y versátil para construir sistemas orientados a objetos


	Ejemplo 2: 

	```java

	// Componente: Clase que representa un Motor
	class Motor {
	    private String tipo;

	    // Constructor
	    public Motor(String tipo) {
	        this.tipo = tipo;
	    }

	    // Método que muestra el tipo de motor
	    public void mostrarTipo() {
	        System.out.println("Tipo de motor: " + tipo);
	    }
	}

	// Clase que utiliza composición para incorporar un Motor
	class Coche {
	    private String modelo;
	    private Motor motor;  // Composición: Coche tiene un Motor

	    // Constructor
	    public Coche(String modelo, Motor motor) {
	        this.modelo = modelo;
	        this.motor = motor;
	    }

	    // Método que muestra información del coche, incluyendo el tipo de motor
	    public void mostrarInformacion() {
	        System.out.println("Modelo: " + modelo);
	        motor.mostrarTipo();  // Utilizando el método del componente Motor
	    }
	}

	// Clase principal que demuestra el uso de composición
	public class EjemploComposicion {
	    public static void main(String[] args) {
	        // Crear una instancia de la clase Motor
	        Motor motorCoche = new Motor("Motor de Gasolina");

	        // Crear una instancia de la clase Coche que utiliza la composición con el motor
	        Coche miCoche = new Coche("Sedan", motorCoche);

	        // Mostrar información del coche (incluyendo el tipo de motor)
	        miCoche.mostrarInformacion();
	    }
	}

	```

	La clase 'Coche' utiliza composición al tener un miembro de tipo 'Motor'. 

	La instancia de 'Motor' es creada y luego pasada al constructor de 'Coche'. 

	La clase 'Coche' puede utilizar los métodos de la clase 'Motor' a través de su instancia interna.

	Este enfoque permite que la relación entre 'Coche' y 'Motor' sea más flexible, ya que puedes cambiar el tipo de motor o incluso tener varios motores en un mismo coche sin cambiar la estructura de la clase 'Coche'. 

	La composición ofrece una forma modular y flexible de construir clases y componentes en un sistema orientado a objetos.

	

|| Clases de Alto Nivel vs Bajo Nivel
	
	Sos niveles distintos en la jerarquía de dependencias entre clases. 

	Estos conceptos están relacionados con el principio de diseño conocido como el "Principio de Inversión de Dependencias" (Dependency Inversion Principle, DIP).


	Clases de Alto Nivel:

    	Las clases de alto nivel son aquellas que contienen la lógica principal y las políticas de negocio de una aplicación.

    	Estas clases suelen ser más abstractas y están diseñadas para manejar tareas específicas de nivel superior.

    	Las clases de alto nivel deberían depender de abstracciones (interfaces o clases abstractas), no de detalles de implementación.

    	Siguen el principio de que las abstracciones no deben depender de detalles, pero los detalles deben depender de abstracciones.


    	```java

    	public interface Motor {
		    void arrancar();
		    void detener();
		}

		public class Coche {
		    private Motor motor;

		    public Coche(Motor motor) {
		        this.motor = motor;
		    }

		    public void conducir() {
		        motor.arrancar();
		        // Lógica para conducir el coche
		        motor.detener();
		    }
		}

    	```

    	'Coche' es una clase de alto nivel que depende de la abstracción 'Motor'. 

    	Puede trabajar con cualquier implementación de 'Motor', permitiendo la flexibilidad y el intercambio de implementaciones concretas.


    Clases de Bajo Nivel:

    	Las clases de bajo nivel son aquellas que implementan detalles específicos y funciones básicas.

    	Estas clases proporcionan implementaciones concretas de abstracciones y están destinadas a ser utilizadas por clases de alto nivel.

    	Deberían depender de abstracciones, no de otras clases de bajo nivel. 

    	La inversión de dependencias sugiere que las clases de bajo nivel no deben ser la base de la jerarquía de dependencias.

    	```java

    	public class MotorGasolina implements Motor {
		    @Override
		    public void arrancar() {
		        // Lógica específica para arrancar un motor de gasolina
		    }

		    @Override
		    public void detener() {
		        // Lógica específica para detener un motor de gasolina
		    }
		}

    	```

    	'MotorGasolina' es una clase de bajo nivel que implementa la abstracción 'Motor'.

    	Proporciona la lógica concreta para arrancar y detener un motor de gasolina.


    Principio de Inversión de Dependencias (DIP):

    	El principio de inversión de dependencias sugiere que las clases de alto nivel no deben depender de clases de bajo nivel, sino de abstracciones.

    	Las abstracciones deben ser independientes de las implementaciones concretas.

   		La inversión de dependencias se logra al diseñar sistemas donde las clases de alto nivel dependen de abstracciones, y las implementaciones concretas dependen de esas mismas abstracciones.




|| Encapsulación 

	Ejemplo cuenta bancaria: 

	```java

	// Clase que ilustra encapsulación
	class CuentaBancaria {
	    // Atributos privados
	    private String titular;
	    private double saldo;

	    // Constructor
	    public CuentaBancaria(String titular, double saldoInicial) {
	        this.titular = titular;
	        this.saldo = saldoInicial;
	    }

	    // Método getter para obtener el titular
	    public String getTitular() {
	        return titular;
	    }

	    // Método getter para obtener el saldo
	    public double getSaldo() {
	        return saldo;
	    }

	    // Método para realizar un depósito
	    public void depositar(double cantidad) {
	        if (cantidad > 0) {
	            saldo += cantidad;
	            System.out.println("Depósito de " + cantidad + " realizado. Nuevo saldo: " + saldo);
	        } else {
	            System.out.println("La cantidad de depósito debe ser mayor que cero.");
	        }
	    }

	    // Método para realizar un retiro
	    public void retirar(double cantidad) {
	        if (cantidad > 0 && cantidad <= saldo) {
	            saldo -= cantidad;
	            System.out.println("Retiro de " + cantidad + " realizado. Nuevo saldo: " + saldo);
	        } else {
	            System.out.println("La cantidad de retiro no es válida o supera el saldo disponible.");
	        }
	    }
	}

	public class EjemploEncapsulacion {
	    public static void main(String[] args) {
	        // Crear una instancia de CuentaBancaria
	        CuentaBancaria cuenta = new CuentaBancaria("Juan Pérez", 1000.0);

	        // Acceder a los atributos mediante métodos getter
	        System.out.println("Titular de la cuenta: " + cuenta.getTitular());
	        System.out.println("Saldo inicial: " + cuenta.getSaldo());

	        // Realizar operaciones de depósito y retiro
	        cuenta.depositar(500.0);
	        cuenta.retirar(200.0);

	        // Acceder al saldo después de las operaciones
	        System.out.println("Saldo actual: " + cuenta.getSaldo());
	    }
	}

	```

	La clase 'CuentaBancaria' tiene atributos 'titular' y 'saldo' que están declarados como privados.

	Los métodos 'getTitular()' y 'getSaldo()' son métodos getter que permiten acceder a estos atributos desde fuera de la clase de manera controlada.

	Las operaciones de depósito y retiro ('depositar()' y 'retirar()') también están encapsuladas dentro de la clase. 

	Estas operaciones verifican las condiciones necesarias antes de realizar cambios en el saldo.

	Este enfoque de encapsulación ayuda a controlar el acceso y la manipulación de los datos internos de la clase, proporcionando una interfaz más segura y mantenible para interactuar con objetos de esa clase.


	Ejemplo 2: 

	```java

	// Clase que utiliza encapsulación
	class Persona {
	    // Variables privadas, solo accesibles dentro de la clase
	    private String nombre;
	    private int edad;

	    // Constructor
	    public Persona(String nombre, int edad) {
	        this.nombre = nombre;
	        this.edad = edad;
	    }

	    // Método getter para obtener el nombre
	    public String getNombre() {
	        return nombre;
	    }

	    // Método setter para establecer el nombre
	    public void setNombre(String nombre) {
	        this.nombre = nombre;
	    }

	    // Método getter para obtener la edad
	    public int getEdad() {
	        return edad;
	    }

	    // Método setter para establecer la edad
	    public void setEdad(int edad) {
	        // Validar que la edad sea no negativa antes de asignarla
	        if (edad >= 0) {
	            this.edad = edad;
	        } else {
	            System.out.println("La edad no puede ser negativa.");
	        }
	    }

	    // Otro método que utiliza las variables encapsuladas
	    public void saludar() {
	        System.out.println("Hola, soy " + nombre + " y tengo " + edad + " años.");
	    }
	}

	// Clase principal que demuestra el uso de encapsulación
	public class EjemploEncapsulacion {
	    public static void main(String[] args) {
	        // Crear un objeto de la clase Persona
	        Persona persona = new Persona("Juan", 25);

	        // Utilizar métodos getter y setter
	        System.out.println("Nombre: " + persona.getNombre());
	        System.out.println("Edad: " + persona.getEdad());

	        // Modificar la edad utilizando el setter
	        persona.setEdad(30);

	        // Utilizar el método que utiliza las variables encapsuladas
	        persona.saludar();
	    }
	}

	```

	La clase 'Persona' tiene variables privadas ('nombre' y 'edad') y métodos públicos ('getNombre', 'setNombre', 'getEdad', 'setEdad', 'saludar') para acceder y modificar esas variables. 

	El uso de estos métodos garantiza que la encapsulación se mantenga, y cualquier validación o lógica específica puede aplicarse dentro de los métodos setters. 

	Además, las variables privadas no pueden ser accedidas directamente desde fuera de la clase, lo que mejora la seguridad y el control sobre el estado interno de la instancia de la clase.



|| Clase Abstracta
	
	Es una clase que no se puede instanciar directamente, es decir, no se pueden crear objetos directamente a partir de ella. 

	En cambio, se utiliza como una plantilla o modelo para otras clases derivadas (subclases), que pueden extenderla y proporcionar implementaciones para sus métodos abstractos y no abstractos.


	1. Métodos abstractos: 

		Una clase abstracta puede contener métodos abstractos, que son métodos que no tienen una implementación definida en la clase abstracta. 

		En su lugar, las subclases deben proporcionar una implementación para estos métodos.


	2. Métodos concretos: 

		Además de los métodos abstractos, una clase abstracta puede contener métodos concretos (implementados). 

		Estos métodos pueden tener una implementación definida en la clase abstracta y las subclases pueden heredarlos sin necesidad de proporcionar una implementación adicional.


	3. Propiedades y constructores: 

		Una clase abstracta puede contener propiedades (variables de instancia) y constructores como cualquier otra clase en Java. 

		Sin embargo, no se pueden instanciar objetos directamente a partir de una clase abstracta.


	4. Uso de la palabra clave abstract:

		Para definir una clase como abstracta, se utiliza la palabra clave abstract antes de la palabra clave class en la declaración de la clase.

		Además, los métodos abstractos se declaran con la palabra clave abstract y no tienen cuerpo.


	5. Herencia: 

		Las subclases de una clase abstracta pueden extenderla utilizando la palabra clave extends y proporcionar implementaciones para sus métodos abstractos.


	Ejemplo: 

	```java

	// Definición de una clase abstracta
	abstract class Animal {
	    // Propiedad
	    protected String nombre;

	    // Constructor
	    public Animal(String nombre) {
	        this.nombre = nombre;
	    }

	    // Método abstracto
	    public abstract void hacerSonido();
	}

	// Clase derivada (subclase)
	class Perro extends Animal {
	    // Constructor
	    public Perro(String nombre) {
	        super(nombre); // Llamada al constructor de la clase base
	    }

	    // Implementación del método abstracto
	    @Override
	    public void hacerSonido() {
	        System.out.println(nombre + " hace guau guau");
	    }
	}

	public class EjemploClaseAbstracta {
	    public static void main(String[] args) {
	        // No se puede crear una instancia de la clase abstracta Animal
	        // Animal animal = new Animal("Animal"); // Esto producirá un error

	        // Crear una instancia de la subclase Perro
	        Perro perro = new Perro("Fido");
	        perro.hacerSonido(); // Imprime "Fido hace guau guau"
	    }
	}

	```

	'Animal' es una clase abstracta que contiene un método abstracto 'hacerSonido()'. 

	La clase 'Perro' es una subclase de 'Animal' que extiende la clase abstracta y proporciona una implementación para el método abstracto. 

	Se puede crear una instancia de 'Perro', pero no se puede crear una instancia de 'Animal' directamente.


