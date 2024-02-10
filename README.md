# O que são desafios PWN
São um tipo de desafio que exige a exploração de vulnerabilidade em um sistema, normalmente em um servidor remoto, através de binários. Há varias formas de fazer isso, mas a mais simples é utilizando buffers overflow, que é basiamente um estouro de escrita na área de memória. Os passos para resolver um problema de pwn costumam ser:
- Conectar a um servidor usando netcat
- Descobrir o que o um binário faz
- Encontrar uma vulnerabilidade no binário ou através dele
- Criar um script de solução fazendo exploit no binário
- Capturar a Bandeira

# Explorando a memória
Um modo de explorar os buffers na área de memória são as pilhas, mas o que é uma pilha? No contexto de exploração de memória, pilha é uma região da memória atribuida a cada programa enquanto é carregado pelo sistema operacional e é usada como uma estrutura de dados pilha (LIFO), quando se define um área na memória para uma variável por exemplo sem usar funções de alocação, ela sera alocada na pilha. Para salvar e remover dados na pilha são usadas instruções push e pop pela linguagem de máquina, o ponteiro dessas instruções é armazenado na pilha e quando a variável ou função associada a essa pilha é chamada o programa aponta passa a apontar para a direção desse ponteiro para executar as instruções.

# Qual a vulnerabildiade na pilha?
Basicamente se um programa estiver lendo uma entrada em um buffer na pilha e não verificar o tamanho da entrada ocorre um estouro da pilha pois podem vir dados a mais que seram sobrescritos na própria pilha ou em outras áreas de memória, como o endereço das instruões também fica armazenado na pilha e podemos sobrescreve-la, também é possível sobrescrever o a pilha onde o endereço da função esta armezenado, ganhando-se assim controle sobre o fluxo de execução e portanto sobre o sistema.

# Ferramentas que podem auxiliar nesse processo
- pwntools
- GDB
- Ghidra
- radare2
- E o bom e velho Python

# Outras formas de explorar um Buffer Overflow
- Alterações de valores de variáveis
- Injeção de shellcode
- programação oirentada a retorno
- Ataques return-to-libc
- Vazamento de endereços de memória
- Permissões de segurança em binário
