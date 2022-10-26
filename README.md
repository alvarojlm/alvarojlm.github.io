# Processamento Digital de Imagens.

> Essa página se destina a exibição de atividades propostas na disciplina de Processamento Digital de Imagens. 
A linguagem escolhida para implemnetação foi **Python**. 
Os códigos foram feitos na plataforma do **Google Colaboratory**, conhecido como **Colab**, portanto, algumas funcionalidade foram feitas de modo exclusivo para essa ferramenta. 
Por exemplo, como a plataforma não permite o uso do função _imshow_, utilizada para exibição da imagem pelo OpenCV, em alguns casos foi utilizado uma importação do propio Colab que permite a execução, de forma semelhante, pelo codigo *cv2_imshow*. Assumindo que as importações necessarias foram feitas, iremos diretamente as implementações.

## Manipulando pixels.
1. A primeira atividade desta etapa se dá da seguinte forma: Será feito um tratamento de erro para o carregamento da imagem, verificando se o arquivo foi aberto corretamente, após isso a imagem é convertida em escala de cinza e, através da função _shape_ da numpy array, como é lido em Python, são lidos os atributos da imagem, sua altura e largura em pixels  estes serão usados para avisar ao usuario os limetes que podem ser digitados.

```
try:
  img=cv2.imread('/content/drive/MyDrive/Colab Notebooks/PDI/img/img.png')
except:
  print('Erro ao carregar imagem.')
else:
  print('Imagem carregada.')

img_g = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

altura,largura=img_g.shape

print(f'As coordenadas devem estar entre (0,{altura}) e (0,{largura}).')

P1_x=int(input(f'Digite o primeiro ponto de coordenada P1: '))
P1_y=int(input(f'Digite o segundo ponto de coordenada P1: '))
P2_x=int(input(f'Digite o primeiro ponto de coordenada P2, maior que {P1_x}: '))
P2_y=int(input(f'Digite o segundo ponto de coordenada P2, maior que {P1_y}: '))

P1=(P1_x,P1_y)
P2=(P2_x,P2_y)
```
 Também é avisado ao usuario que o próximo valor para uma coordenada horizontal ou vertical deverá ser maior que o anterior, isto para a forma como o  códgio foi implementado.
Após as coordenadas serem dadas e considerar que o usuario tenha seguido as instruções, para o intervalo estabelecido é feito o negativo da imagem, ou seja, uma inversão das cores da imagem e, por fim, a imagem é exibida, através do seguinte codigo:
 ```
 for i in range(P1[0], P2[0]):
  for j in range(P1[1], P2[1]):
    img_g[i][j]= 255 - img_g[i][j]
cv2_imshow(img_g)
```
![Imagem em Negativo](img/print/img_negativa.png)

2. A segunda atividade propõe um algortimo que faça a troca de regiões de uma imagem. Para tal importamos a bibliotaca Numpy para utilizar da função **concatenate**, que permite agrupar uma sequencia a outra, esta foi necessaria pois foi feita a divisão da imagem em 4 partes, para então agrupar no formato solicitado.

```
#endereçando imagens
img_pA=img[0:int(altura/2), 0:int(largura/2)]
img_pB=img[0:int(altura/2),int(largura/2):largura]
img_pC=img[int(altura/2):altura, 0:int(largura/2)]
img_pD=img[int(altura/2):altura, int(largura/2):largura]

#criando linhas da nova matriz de imagem
img_trocada1=np.concatenate((img_pD,img_pB))
img_trocada2=np.concatenate((img_pC,img_pA))

#juntando em uma mesma linha
img_trocada=np.concatenate((img_trocada1,img_trocada2), axis=1)
cv2_imshow(img_trocada)
```

A imagem é dividida de acordo com seu tamanho de forma a gerar 4 novas imagens que a compõe, através dos parametros lidos anteriormente através da função shape. 
A última concatenção é feita com um parametro a mais que indica que deverá ser feita formando um segundo eixo. O resultado é o seguinte:

![Imagem Trocada](img/print/imagem_trocada.png)
