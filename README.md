# Descrición

Emprega este arquivo para describir os cambios do teu proxecto.

Utiliza o formato en markdown coas marcas básicas que aparcen no seguinte exemplo:

# Título principal
## Subtítulo

Texto normal con **negriña** e *cursiva*.

- Lista 1
- Lista 2

[Ligazón](https://exemplo.com)


```csharp
using UnityEngine;

public class OlaMundo : MonoBehaviour
{
    void Start()
    {
        Debug.Log("Ola, mundo desde C#!");
    }
}

```



### Waypoints e destinos

Os waypoints configurados no `WPManager` son:

- **WP01** → Refinería (botón `Go to Refi`)
- **WP03** → Fábrica (botón `Go to Factory`)
- **WP04** → Ruínas (botón `Go to Ruin`)
- **WP05** → Helicóptero (botón `Go to Heli`)
- **WP09** → Roca / zona alternativa (botón `Go to Rock`)

Cada botón da UI chama a un método público en `TanksWaypointsFollow` (`GotoHeli`, `GotoRefi`, `GotoFactory`, `GotoRuin`, `GotoRock`), que executa A* no grafo dende o nodo actual ata o waypoint de destino e fai que o tanque siga o `pathList` xerado.

### Grafo e links

O script `TanksWaypointsManager` crea o grafo engadindo todos os waypoints como nodos e definindo as conexións entre eles mediante a estrutura `Link`.  
As conexións entre waypoints foron axustadas para garantir que exista camiño desde a posición inicial do tanque a todos os destinos anteriores, de maneira que o A* sempre poida atopar unha ruta válida. Modificouse os links para crear camiños alternativos entre os WP