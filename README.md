# Fundamentos-spring-boot-platzi

# Apuntes Fundamentos Spring boot

## Dependencias

### ¿Que es una dependencia?

    Es un objeto con una funcionalidad, son objetos definidos 
    como una funcionalidad.

    Basicamente es un pequeño objeto con una funcionalidad.

    Y estas Funcionalidaddes tienen como objetivo, trabajar con 
    otros objetos y otras funcionalidades 

    Sin esta funcionalidad los otros objetos no podrán trabajar, 
    por que dependen de ellas 

    El termino de dependencia se deriva del termino MODULARIDAD en 
    programacion orientada a objetos POO

    Una aplicacion puede tener muchas caracteristicas, y esas caracteristicas, 
    son igual a dependencias, estas dependencias interactuian entre si para poder 
    lograr un objetivo.

    las dependencias se pueden probar de manera individual 

## Inversion de Control

### ¿Qué es una inversíon de control?

    - Principio que transfiere el control de objetos de un 
    programa a un contenedor o framework 

    Basicamente lo que se refiere es transferir el control del flujo del programa 
    a un contenedor o a un framewrk 

#### Ejemplo flujo tradicional

    // clase con el metodo Main principal 
    public class Generals {
        public static void main (String[] args){

            // lista se inicializa con 3 valores
            List<Integer> lista = Arrays.asList(1, 2, 3);
            int number = 5;
            // el for que recorre la lista 
            for( int value : lista){
                //
            }
            System.out.print(number);
        }
    }

    Entonces que pasa cuando se invierte el control ?

    Cuendo se invierte el control lo que se hace es que se le da el control 
    del flujo del porgrama a un contenedor o a un framework

    En este caso el contenedor puede ser un usuario de una aplicacion web o movil.
    Es decir El contenedor el el usuario que interactua con la apolicacion 

    Los objetos que son administrados por el contennedor de Spring IoC se denominan 
    Beans.

    un Bean es un objeto que es intanciado ensablado y administrado por un contenedor Spring IoC

    @Bean
    public MyBean anyNameMerhod(){
        return new MyBeanImpl();
    }

#### Que es inyeccion de dependencias (DI)

    Es el proceso en el que los objetos definen sus dependecias 

    Código más limpio y desacoplamiento más efectivo cuando cada objeto cuenta con
    su dependencia.

    //Tenemos un bean y este es inicializado 
    @Bean
    public MBean mybean(){
        return new MyBeanImpl();
    }

    // En esta clase se inicializa el bean o la interfaz
    public class ClaseNecestoDependencia{

        // De esta manera y se pone el nombre dependencie
        private final Mybean dependecie;

        //Constructor y de esta manera se esta inyectandoi esa dependencia
        //la cual inicializa esa dependencia 
        @Autowired
        public ClaseNecesitoDependencia(Mybean dependencie){
            this.dependecie = dependecie;
        }

        // LKuego mas abajo aca en esta parte del codigo 
        // Se puede utilizar sus implementaciones osea las funcioinalidades de esa 
        // dependencia y funcionalidades, en este caso la dependencia Mybean
    }

    El inversion de control y patron de inyeccion de depenmdencias.
    La inyeccion de dependencias es la implementación del inversíon de control 

## Autoconfiguracioin y tiempo de ejecucion (Runtime)

    Spring boot configura automaticamente tus aplicaciones basadas en dependencias jar 

##  Anotaciones para indicar dependencias en Spring Boot

### Tipos de anotacionoes

    - @component : anotacion general, son clases componentes o modulos, si es lago muy general se puede anotar con @component

    - @Controller : De igual forma que el modelo vista controlador, son las clases que controlan todo lo que se ve en la vista o todo lo que viene de la interfaz grafica de la aplicacion 

    - @Service : Sirve para toda la logica de negocio adicional del sistema. como validaciones logicas

    - @Repository : capa de persistencia de datos

#### Ejemplos

    - Implentacion general 

    @Component
    public class Component{

        public void myMethod(){

            // implementacion General
        }
    }
    Este cmponent se puede inyectar como dependencia 
    en otra parte de nuestro sistema 


    - Implementacion para Vista GUI

    @Controller
    public class Controller{

        public void myMethod(){
            
            //Respuesta HTTP
        }
    }
    Los controller se pueden anotar de cualquer manera 


#### Ejemplo inyeccion de dependencia con las anotaciones

    @Service
    public class DatabaseAccountService implements AccountService{

        // esta clase va a servir como dependencia de otra clase y a su ves tiene 
        // una dependencia que se llama RiskAssesor

        private final RiskAssesor riskAssesor;


        //Constructor 
        //aca se esta inyectando la dependencia RiskAssesor 
        @Autowired
        public DatabaseAccountService(RiskAssesor riskAssesor){

            this.riskAssesor = riskAssesor;

        }
        //

        public void miServiceFunction(){
            riskAssesor.myDependecyfunction();
        }
    }


## Estructura arquitectura de un poryecto spring boot

### Carpeta mvn
    plugin adicional de maven 

###  Caperta SRC (source)

    Esta se tiene todo el codigo fuente de la aplicacion 

#### Carpeta main (Esta se encuentra dentro de la carpeta src)

    dentro de esta carpeta se encuentr la carpeta java 

#### Carpeta Java

    dentro de esta carpeta se encuentra una clase fundamentosaplication de java 
    esta se anota con la anotacion @SpringBootAplication

    en esta clase tambien tenemos un metodo main, es el encargado de inicializar toda la arquitectura y la configuracion del proyercto springboot

## Archivo Pom.xml

    este archivo tiene todas las configuraciones del proyecto Springboot, 
    tambien se pueden agregar todas las dependencias adicionales y plugins 






