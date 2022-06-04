# Mas como o Git funciona por de baixo dos panos?



## SHA1

A sigla SHA significa Secure Hash Algorithm, é um conjunto de funções hash criptográficas projetadas pela NSA (Agência de Segurança Nacional dos EUA). 

 

A encriptação gera conjunto de caracteres identificador de 40 dígitos

 

É um algoritmo de encriptação. Uma forma curta de representar um arquivo

 

:star: openssl sha 1 *nome do arquivo*



## Objetos fundamentais

 Tipos de objetos

- **BLOBS**

  - echo -e 'blob 9\0conteudo' ?      | openssl sha1

  - O git armazena metadados      entro do BLOB
  - Armazena o código      criptografado do arquivo (O sha1 do arquivo)

- **TREES**

  - As trees armazenam BLOBS e      também contém metadados

  - Também contém a " \0 "
  - Também armazena o nome do      arquivo
  - Qualquer mudança em um      arquivo de um blob que seja, muda toda a estrutura, toda a criptografia      (sha1), da árvore inteira

- **COMMITS**

  - É o objeto que vai juntar tudo

  - Ele aponta para uma árvore, um parente, autor, mensagem
  - Indica as modificações feitas nos arquivos (blobs), nas pastas (trees), necessitando de um autor      e suportando uma mensagem. 
  - Caso ocorra qualquer mudança      em qualquer arquivo ou pasta, a criptografia sim, inclusive do commit, será alterada. Por isso o Git é tão confiável.



## Sistema distribuído 

 

Pois o versionamento do código é literalmente distribuído não só nas máquinas tanto do autor pioneiro do código, mas também nas máquinas de seus colaboradores e além disso, na nuvem de um sistema que armazena versionamentos, como o GitHub por exemplo.



## Segurança :lock:

Devido a sua criptografia de nível e complexidade altíssimos e também pela maneira de como a distribuição é feita





## Chave SSH e Tokens :key:

 

Chave SSH é uma forma estabelecer uma conexão segura e encriptada entre duas máquinas, utilizando duas chaves (uma pública e uma privada).

 

Gerando a chave SSH

ssh-keygen -t ed25519 -C *email*

 

cat *chave publica*

​	*Pegue a chave criptografa e adicione ao github*

 

Comando para o agente lidar com as chaves

eval $(ssh-agent -s)

 

Adicionar a chave ao agente

ssh-add *chave privada*
