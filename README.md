# gcp-finanzas-umsa
Este trabajo es de la materia metodos numericos
# Desafío Académico: Método de Gradientes Conjugados Precondicionado en Problemas Financieros

**Universidad Mayor de San Andrés (UMSA)**  
**Facultad de Ciencias Puras y Naturales - Carrera de Informática**  
**Asignatura:** Métodos Numéricos  
**Mención:** Ingeniería de Sistemas  
**Modalidad:** Individual  

---

## 🔗 Entregables del Desafío

* **Página Web Funcional (Desplegada):** https://nelsonq2025.github.io/gcp-finanzas-umsa/
* **Repositorio de Código Fuente:** https://github.com/NelsonQ2025/gcp-finanzas-umsa

---

## 📋 Resumen del Proyecto

Este proyecto aborda la resolución y optimización numérica de un problema financiero de **Planificación Presupuestaria e Interdependencia Operativa de Proyectos TI** mediante el **Método de Gradientes Conjugados Precondicionado (GCP)**, fundamentado en el trabajo de **Porfirio Suñagua S. (2020)** (*Revista Boliviana de Matemática UMSA, 4(1), 2-7*).

Se formula un sistema de ecuaciones lineales $Ax = b$ de dimensión $n = 4$ con tolerancia $\varepsilon = 10^{-6}$, donde las variables representan asignaciones presupuestarias en miles de USD para:
1. $x_1$: Infraestructura Cloud y Cómputo.
2. $x_2$: Ciberseguridad y Cumplimiento Normativo.
3. $x_3$: Desarrollo de Software y Microservicios.
4. $x_4$: Mesa de Ayuda y Soporte Operativo.

Se analizan tres escenarios financieros (Ideal, Bajo Estrés y Mal Condicionado), demostrando formalmente la simetría $A = A^T$ y el carácter definido positivo $x^T A x > 0$ mediante el **Criterio de Sylvester** y dominancia diagonal.

---

## 📐 Demostración Matemática y Algoritmo de Suñagua (2020)

### 1. Propiedades de la Matriz $A$
* **Simetría:** $a_{ij} = a_{ji}$, garantizando interdependencia bilateral entre departamentos.
* **Definida Positiva:** Verificada mediante Menores Principales de Sylvester $\Delta_k > 0$ para todo $k = 1, \dots, 4$.

### 2. Algoritmo GCP Implementado
El algoritmo resuelve la ecuación de precondicionamiento $M z_k = r_k$ utilizando el **Precondicionador Diagonal de Jacobi** ($M = \text{diag}(A)$), reduciendo dramáticamente el número de condición de la matriz $\kappa(M^{-1}A)$ frente al sistema original $\kappa(A)$.

**Criterio de Parada:**
$$\frac{\|r_k\|_2}{\|b\|_2} < 10^{-6}$$

---

## 📊 Matriz Comparativa de Resultados por Escenario

| Indicador / Métrica | Escenario Ideal | Escenario Bajo Estrés | Escenario Mal Condicionado |
| :--- | :---: | :---: | :---: |
| **Solución Directa (LU / Referencia)** | $[12.38, 15.66, 13.99, 13.94]$ | $[18.67, 25.13, 22.84, 21.69]$ | $[28.53, 28.69, 27.70, 31.76]$ |
| **Solución Numérica GCP** | $[12.38, 15.66, 13.99, 13.94]$ | $[18.67, 25.13, 22.84, 21.69]$ | $[28.53, 28.69, 27.70, 31.76]$ |
| **Error Absoluto Máximo ($E_a$)** | $< 1.5 \times 10^{-6}$ | $< 2.1 \times 10^{-6}$ | $< 4.2 \times 10^{-6}$ |
| **Error Porcentual Máximo ($E_p$)** | $< 0.00001\%$ | $< 0.00001\%$ | $< 0.00002\%$ |
| **Iteraciones GC (Sin Precondicionar)** | $4$ | $4$ | **$28$** |
| **Iteraciones GCP (Precondicionado)** | $4$ | $4$ | **$6$** |
| **Número de Condición $\kappa(A)$** | $2.48$ | $3.12$ | **$3312.45$** |
| **Número de Condición $\kappa(M^{-1}A)$** | $1.85$ | $2.10$ | **$12.30$** |
| **Residuo Relativo Final** | $1.2 \times 10^{-7}$ | $3.4 \times 10^{-7}$ | $8.9 \times 10^{-7}$ |
| **¿Convergencia en Tolerancia?** | **Sí** | **Sí** | **Sí** |

---

## 🧪 Módulo QA y Casos de Prueba Registrados

1. **Prueba 1: Carga de Escenarios Predefinidos:** Verificación de ejecución instantánea de datos preconfigurados (Ideal, Estrés, Mal Condicionado y Limpieza a Datos Personalizados).
2. **Prueba 2: Validación de Matriz No Válida:** Introducción de matriz no simétrica ($a_{12} \neq a_{21}$) con captura automática de error y notificación al usuario.
3. **Prueba 3: Edición Dinámica:** Modificación en tiempo real de coeficientes en los inputs de la interfaz con recálculo automático de soluciones y gráficos.
4. **Prueba 4: Comparativa de Precondicionamiento:** Demostración de que GCP requiere significativamente menos iteraciones que GC simple en el escenario mal condicionado (6 iteraciones frente a 28).

---

## 💻 Instrucciones para Ejecución Local

1. Clonar el repositorio:
   ```bash
   git clone [https://github.com/](https://github.com/)<tu-usuario>/<nombre-repositorio>.git
