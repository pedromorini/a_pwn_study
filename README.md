# O que são desafios PWN
São um tipo de desafio que exige a exploração de vulnerabilidade em um sistema, normalmente em um servidor remoto, através de binários. Há varias formas de fazer isso, mas a mais simples é utilizando buffers overflow, que é basiamente um estouro de escrita na área de memória. Os passos para resolver um problema de pwn costumam ser:
Conectar a um servidor usando netcat
Descobrir o que o um binário faz
Encontrar uma vulnerabilidade no binário ou através dele
Criar um script de solução fazendo exploit no binário
Capturar a Bandeira

# Explorando a memória
Um modo de explorar os buffers na área de memória são as pilhas, mas o que é uma pilha? No contexto de exploração de memória, pilha é uma região da memória atribuida a cada programa enquanto é carregado pelo sistema operacional e é usada como uma estrutura de dados pilha (LIFO), quando se defina um área na memória para uma variável por exemplo sem usar funções de alocação, ela sera alocada na pilha. 


Alterações de valores de variáveis
Injeção de shellcode
programação oirentada a retorno
Ataques return-to-libc
Vazamento de endereços de memória
Permissões de segurança em binário
