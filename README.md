[README.md](https://github.com/user-attachments/files/35393182/README.md)
# Sistema de modulación en amplitud (AM)

Simulación en Python de AM convencional con portadora. El programa genera una señal de información de baja frecuencia, la modula, observa su forma de onda y su espectro, y compara la recuperación del mensaje bajo ruido, distorsión no lineal y atenuación.

## Requisitos

- Python 3.10 o posterior
- NumPy, SciPy y Matplotlib

## Ejecución

```bash
python -m pip install -r requirements.txt
python am_simulation.py
```

El programa imprime la relación señal a ruido (SNR) de la señal recuperada y guarda `am_resultados.png` junto al código. Se abre también una ventana con las gráficas.

## Modelo

La señal de mensaje y la señal AM son:

```text
m(t) = cos(2π fm t)
s(t) = [1 + μ m(t)] cos(2π fc t)
```

El índice de modulación `μ = 0.7` evita la sobremodulación (`μ ≤ 1`). El receptor usa demodulación síncrona: multiplica por una portadora local, filtra paso bajo y escala el resultado para recuperar el mensaje.

## Escenarios estudiados

- **Ruido:** se suma ruido blanco gaussiano a la señal AM.
- **Distorsión:** se agrega un término cúbico para representar una respuesta no lineal.
- **Atenuación:** la amplitud recibida se reduce al 45 %; la SNR se calcula antes de corregir la ganancia.

La gráfica incluye el mensaje original, la señal AM con su envolvente, las señales recuperadas y el espectro unilateral. En el espectro aparecen la portadora en `fc` y las bandas laterales en `fc ± fm`.

## Parámetros ajustables

Al inicio de `am_simulation.py` se pueden modificar la frecuencia de muestreo, duración, frecuencias del mensaje y de la portadora, índice de modulación y semilla aleatoria. La atenuación, el nivel de ruido y el coeficiente de distorsión se ajustan en la sección de canal.

## Publicación en GitHub

1. Crea un repositorio vacío en GitHub.
2. Desde esta carpeta, inicializa Git y publica los archivos:

```bash
git init
git add README.md am_simulation.py requirements.txt
git commit -m "Implementar simulación de modulación AM"
git branch -M main
git remote add origin https://github.com/USUARIO/REPOSITORIO.git
git push -u origin main
```

Reemplaza la URL de ejemplo con la dirección del repositorio creado.
