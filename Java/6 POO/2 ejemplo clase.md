# Ejemplo clase


```java
public class Automovil {

    // ATRIBUTOS
    private final int id;
    private static int ultimoId;
    private Color color;
    private String modelo;
    private String fabricante;
    private float distanciaRecorrida;
    private final int capacidadEstanque = 40;
    private static String definition = "Un automóvil es un vehículo de motor diseñado para transportar personas o carga a través de carreteras.";
    public static final String NOMBRE = "Automovil";

    // CONSTRUCTOR Y SOBRECARGA DE CONSTRUCTORES

    public Automovil() {
        this.id = ++ultimoId;
    }

    public Automovil(String modelo, String fabricante) {
        this();
        this.modelo = modelo;
        this.fabricante = fabricante;
    }

    public Automovil(Color color, String modelo, String fabricante) {
        this(modelo, fabricante);
        this.color = color;
    }


    public Automovil(Color color, String modelo, String fabricante, float distanciaRecorrida) {
        this(color, modelo, fabricante);
        this.distanciaRecorrida = distanciaRecorrida;
    }


    // METODOS
    public String acelerar(int revolutionsPerMinute) {
        return "El automovil " + this.fabricante + " esta acelerando a " + revolutionsPerMinute + " rpm";
    }

    public String frenar() {
        return this.fabricante + " " + this.modelo + " esta frenando";
    }

    public float calcularConsumo(int kmRecorridos, float porcentajeVencido) {
        return kmRecorridos / (capacidadEstanque * porcentajeVencido);
    }

    public String detalles() {
        return "Automovil[Color: " + this.color + ", " +
                "Modelo: " + this.modelo + ", " +
                "Fabricante: " + this.fabricante + ", " +
                "Distancia Recorrida: " + this.distanciaRecorrida + "]";
    }

    // sobre Escritura de Método


    @Override
    public String toString() {
        return "Automovil{" +
                "id=" + id +
                ", color='" + color.getColor() + '\'' +
                ", modelo='" + modelo + '\'' +
                ", fabricante='" + fabricante + '\'' +
                ", distanciaRecorrida=" + distanciaRecorrida +
                ", capacidadEstanque=" + capacidadEstanque +
                '}';
    }

    @Override
    public boolean equals(Object obj) {
        // si tienen la misma referencia
        if (this == obj) return true;
        // por si no es una instancia de Automovil
        if (!(obj instanceof Automovil auto)) return false;
        // si no tienen la misma referencia pero los mismos datos
        if (!this.color.equals(auto.getColor())) return false;
        if (!this.fabricante.equals(auto.getFabricante())) return false;
        if (!this.modelo.equals(auto.getModelo())) return false;
        if (this.distanciaRecorrida != auto.getDistanciaRecorrida()) return false;

        return true;
    }

    // Getters && setters

    public int getId() {
        return id;
    }

    public Color getColor() {
        return color;
    }

    public void setColor(Color color) {
        this.color = color;
    }

    public String getModelo() {
        return modelo;
    }

    public void setModelo(String modelo) {
        this.modelo = modelo;
    }

    public String getFabricante() {
        return fabricante;
    }

    public void setFabricante(String fabricante) {
        this.fabricante = fabricante;
    }

    public float getDistanciaRecorrida() {
        return distanciaRecorrida;
    }

    public void setDistanciaRecorrida(float distanciaRecorrida) {
        this.distanciaRecorrida = distanciaRecorrida;
    }

    public int getCapacidadEstanque() {
        return capacidadEstanque;
    }

    // get y set de un atributo static
    public static String getDefinition() {
        return definition;
    }

    public static void setDefinition(String definition) {
        Automovil.definition = definition;
    }
}

```