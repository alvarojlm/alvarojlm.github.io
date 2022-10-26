# Processamento Digital de Imagens.

> Essa página se destina a exibição de atividades propostas na disciplina de Processamento Digital de Imagens. 
A linguagem escolhida para implemnetação foi **Python**. 
Os códigos foram feitos na plataforma do **Google Colaboratory**, conhecido como **Colab**, portanto, algumas funcionalidade foram feitas de modo exclusivo para essa ferramenta. 
Por exemplo, como a plataforma não permite o uso do função _imshow_, utilizada para exibição da imagem pelo OpenCV, em alguns casos foi utilizado uma importação do propio Colab que permite a execução, de forma semelhante, pelo codigo *cv2_imshow*.

## Manipulando pixels.
* A primeira atividade desta etapa se dá da seguinte forma: Será feito um tratamento de erro para o carregamento da imagem, verificando se o arquivo foi aberto corretamente, após isso a imagem é convertida em escala de cinza e, através da função _shape_ da numpy array, como é lido em Python, são lidos os atributos da imagem, sua altura e largura em pixels -- estes serão usados para avisar ao usuario os limetes que podem ser digitados).
