
Buenas Prácticas en CSS
-----------------------

1.  **Organización del Código:**
    
    *   Utiliza comentarios para separar secciones.
    *   Agrupa selectores relacionados.
    *   Sigue una estructura lógica (por ejemplo, de lo general a lo específico).
2.  **Nomenclatura Consistente:**
    
    *   Sigue convenciones como **BEM** (Block Element Modifier) para nombrar clases.

```
    /* BEM Example */
    .tarjeta {
        /* Block */
    }

    .tarjeta__titulo {
        /* Element */
    }

    .tarjeta__titulo--destacado {
        /* Modifier */
    }

```

3.  **Optimización de Selectores:**
    
    *   Utiliza selectores específicos para mejorar el rendimiento.
    *   Evita selectores demasiado generales que puedan afectar a muchos elementos innecesariamente.

4.  **Uso de Variables CSS:**
    
    *   Define variables para colores, tamaños y otros valores repetitivos.

```
    :root {
        --color-primario: #3498db;
        --padding-base: 10px;
    }

    .boton {
        background-color: var(--color-primario);
        padding: var(--padding-base);
    }

```
5.  **Evita el CSS Innecesario:**
    
    *   Borra los estilos no utilizados para mantener el código limpio y eficiente.

* * *