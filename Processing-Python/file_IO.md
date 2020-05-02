## Leitura/entrada (*Input*) e escrita/saída (*Output*) de dados em arquivos
### Lendo texto de um arquivo 

Nosso primeiro exemplo vai ser sobre como ler linhas de texto (*strings*) de um arquivo texto (*text file*).

O arquivo `frutas.txt` vai ficar dentro da pasta `/data/` dentro  do seu sketch:
```
sketch_2020_04a                (pasta/folder do sketch)
  L  sketch_2020_04a.pyde      (arquivo com o código)
  L  data                      (pasta/folder)
       L  frutas.txt           (arquivo texto)
```
Conteúdo do aquivo:
```
maçã
abacaxi
pêra
banana
jaca
maracujá
```
A leitura dos dos dados pode ser feita no Python de maneira mais 'universal', o que é útil saber para poder fazer em outros contextos de uso de Python:
```python
# No Python - exemplo mais universal
from io import open  # melhor encoding no Python 2 
with open("data/frutas.txt",'r') as file:
    linhas = file.readlines()
```
Ou usando uma função bem simples do Processing chamada `loadStrings()`:
```python
# No Processing - mais específico - use dentro do setup()!
linhas = loadStrings("nomes.txt")  # frutas.txt na pasta /data/
```
Note que em ambos os casos, ler dados de um arquivo no computador é considerada uma operação relativamente lenta e não deve ser feita repetidas vezes dentro do `draw()` pois vai ser um disperdício e deixa o seu desenho ou animação lentos.

```python
def setup():
    size(400, 400)
    background(0)
    # frutas.txt na pasta /data/
    linhas = loadStrings("frutas.txt")  

    fill(100, 100, 255)
    textAlign(CENTER, CENTER)
    textSize(24)
    for linha in linhas:
        x, y = random(40, 360), random(20, 380)             
        text(linha, x, y)    
```
![resultado](assets/read_lines.png)


