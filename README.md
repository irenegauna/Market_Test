# Market_Test

# Economía Basada en el Intercambio de Tarjetas Gráficas

## Contexto del Proyecto
Simulación de un mercado de tarjetas gráficas donde diferentes tipos de agentes operan bajo reglas específicas para comprar y vender tarjetas.

## Requisitos del Mercado

- **Stock limitado:** 100,000 tarjetas gráficas disponibles.
- **Agentes económicos:** 100 participantes con distintas estrategias de compra y venta.
- **Iteraciones:** En cada iteración del mercado, los agentes actúan en orden aleatorio y pueden:
  - Comprar → Aumenta el precio un **0.5%**.
  - Vender → Disminuye el precio un **0.5%**.
  - No hacer nada.

### Distribución de Agentes:
- **51 Agentes Aleatorios:**  
  - 1/3 de probabilidad de comprar, vender o no hacer nada en cada iteración.

- **24 Agentes Tendenciales:**  
  - Si el precio ha subido un **1%** o más:  
    - 75% de probabilidad de comprar.  
    - 25% de probabilidad de no hacer nada.  
  - Si no ha subido un **1%**:  
    - 20% de probabilidad de vender.  
    - 80% de probabilidad de no hacer nada.

- **24 Agentes Anti-Tendenciales:**  
  - Si el precio ha bajado un **1%** o más:  
    - 75% de probabilidad de comprar.  
    - 25% de probabilidad de no hacer nada.  
  - Si no ha bajado un **1%**:  
    - 20% de probabilidad de vender.  
    - 80% de probabilidad de no hacer nada.

- **1 Agente Lógico (Personalizado):**  
  - Su estrategia está basada en el **Índice de Fuerza Relativa (RSI)** y busca maximizar su balance final.
  - **Debe terminar con cero tarjetas gráficas** al finalizar la simulación.

### Otras Condiciones del Mercado:
- Cada agente inicia con un **balance de $1,000**.
- No pueden tomar dinero prestado ni vender más tarjetas de las que poseen.
- Los agentes conocen la distribución de estrategias en la población, pero no el orden de ejecución de los demás.
- El precio inicial de las tarjetas es de **$200**.
- La simulación consta de **1,000 iteraciones**.

---

# Estrategia del Agente Lógico (RSI)

Este agente utiliza el **Índice de Fuerza Relativa (RSI)** para tomar decisiones de compra y venta.

### 📈 ¿Cómo funciona?
- **Compra cuando RSI < 30** → Considera que el mercado está en sobreventa y espera una recuperación.
- **Vende cuando RSI > 70** → Detecta sobrecompra y espera una caída.

---

## ✅ **Ventajas de esta Estrategia**
- **Detecta momentos clave del mercado**  
  - Aprovecha zonas de sobreventa y sobrecompra.
- **Evita operar impulsivamente**  
  - No sigue tendencias de forma ciega.
- **Funciona bien en mercados laterales**  
  - Compra barato y vende caro dentro de rangos de precio.

## ❌ **Desventajas de esta Estrategia**
- **No funciona bien en tendencias fuertes**  
  - Puede vender demasiado pronto en mercados alcistas o comprar demasiado pronto en bajistas.
- **No considera volumen ni volatilidad**  
  - Solo analiza el precio, lo que puede generar señales poco confiables.

---

# 📊 ¿Por qué su rendimiento varía en cada simulación?
1. **La evolución del mercado cambia en cada ejecución**  
   - Agentes aleatorios afectan el precio de forma impredecible.  
   - Agentes tendenciales y anti-tendenciales generan dinámicas distintas.  
   - Si el mercado es oscilante → **RSI funciona bien**.  
   - Si hay una tendencia fuerte → **RSI falla**.

2. **El orden de ejecución del agente lógico es clave**  
   - **Si actúa primero:** Tiene ventaja para comprar barato o vender caro antes que los demás.  
   - **Si actúa después:** Puede verse afectado por decisiones previas de otros agentes.

---

## 🔧 **Posibles Mejoras**
- **Filtrar señales con medias móviles** para evitar operar en tendencias contrarias.  
- **Ajustar el período del RSI** según la volatilidad del mercado.  
- **Confirmar señales** con indicadores adicionales antes de operar.  
- **Implementar Stop-Loss y Take-Profit** para proteger capital.

---

**Este proyecto simula un mercado financiero con diferentes estrategias, permitiendo analizar su impacto en el precio y la rentabilidad de los agentes.**

