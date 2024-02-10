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

# Exploits
É um código, método ou técnica criado para explorar e tirar vantagem de uma vulnerabilidade e obter acesso ou controle de um sistema. Para isso usa-se o conhecimento de conceitos como os descritos acima aplicados em ferramentas como as descritas a baixo. 

# Ferramentas que podem auxiliar nesse processo
- pwntools: biblioteca python para auxiliar a desenvovler exploits mais rápido e interagir com o servidor
- GDB: um depurador de binários
- Ghidra: uma ferramenta que realiza engenharia reversa em binários
- E é claro o bom e velho Python

# Outras formas de explorar um Buffer Overflow
- Alterações de valores de variáveis: é possível sobrescrever valores de variáveis quando ocorre um estouro de pilha
- Injeção de shellcode: é possível também sobrescrever o buffer com um conjunto de instruções maliciosas fazendo o ponteiro apontar para elas
- programação orientada a retorno: é quando sobrescreve uam cadeia de retornos na pilha direcionados para fragmentos do próprio binário, útil para montar uma estratégia de ataque
- Ataques return-to-libc: ataques que exploram funções de bibliotecas do código binario substituindo o endereço do ponteiro para o de alguma função, assim pode gerar comportamentos maliciosos no código sem precisar injetar código
- Vazamento de endereços de memória: vazar o endereço armazenado no ponteiro pode ser útil na hora de criar um exploit
- Permissões de segurança em binário: também é possível sobrescrever áreas de permissão do binário pela pilha
