# Implementação MIPS
Esse repositório contém o circuito responsável pela implementação simples do MIPS no Logisim. Esse projeto foi realizado para disciplina de Arquitetura e Organização de Computadores, e será atualizado ao longo da disciplina

### Instruções implementadas

- Instruções de memória: `LB` , `SB` , `LH` , `SH` , `LW` e `SW`
- Intruções lógicas e aritméticas: `ADD` , `SUB` , `AND` , `OR`, `SLT`, `ADDI` , `ANDI`, `ORI` e `SLTI`
- Instruções de salto: `BEQ`, `BNE` e `J`

### Implementações
Nesse repositório, exitem dois tipos de implementações:
- Datapath CPU: [mips-datapath-claura.circ](https://github.com/lauramoroni/mips-logisim/blob/main/mips-datapath-claura.circ)
- Pipeline CPU: [mips-pipeline-claura.circ](https://github.com/lauramoroni/mips-logisim/blob/main/mips-pipeline-claura.circ)

## Tabelas de operações

Para selecionar entre os tipos de operação, segue a tabela abaixo com os valores correspondentes a cada entrada.

| **Instrução** | **Operação ULA** | **READ_MEM** | **WRITE_MEM** | **WRITE_REG** | **Tipo de instrução** | **RegDst** | **MemToReg** | **BEQ** | **BNE** | **Jump** | **ALUsrc** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| load byte | 0010 | 1 | 0 | 1 | 00 | 0 | 1 | 0 | 0 | 0 | 1 |
| store byte | 0010 | 0 | 1 | 0 | 00 | 0 | 0 | 0 | 0 | 0 | 1 |
| load half | 0010 | 1 | 0 | 1 | 01 | 0 | 1 | 0 | 0 | 0 | 1 |
| store half | 0010 | 0 | 1 | 0 | 01 | 0 | 0 | 0 | 0 | 0 | 1 |
| load word | 0010 | 1 | 0 | 1 | 10 | 0 | 1 | 0 | 0 | 0 | 1 |
| store word | 0010 | 0 | 1 | 0 | 10 | 0 | 0 | 0 | 0 | 0 | 1 |
| bne | 0110 | 0 | 0 | 0 | 00 | 0 | 0 | 0 | 1 | 0 | 0 |
| j | 0000 | 0 | 0 | 0 | 00 | 0 | 0 | 0 | 0 | 1 | 0 |
| add | 0010 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| and | 0000 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| sub | 0110 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| or | 0001 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| slt | 0111 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| addi | 0010 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| andi | 0000 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| ori | 0001 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| slti | 0111 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |

## Carregando memória de instruções

Para testar seu processador, fornecemos as seguintes instruções:

~~~Assembly
sb $t1, 0($t0)
lb $t2, 4($t0)
sh $t1, 0($t0)
lh $t2, 4($t0)
sw $t1, 0($t0)
lw $t2, 4($t0)
~~~

Este programa aparece em código de máquina, na forma hexadecimal, no arquivo **“test-L-S.mem”** fornecido no projeto, usado para inicializar a memória de instruções.

Para usar esses arquivos, é necessário clicar com o botão direito do mouse na **memória de instruções** e nas **memórias de dados** e **carregar os arquivos** com extensão `.mem`.

![Memória de instrução](implementacao-mips/image%203.png)

## Carregando memória de dados

Para utilizar o exemplo de código fornecido, é necessário inicializar o **endereço de memória** `0x04` com o valor desejado. Isso porque, nas instruções de `Load`, utilizamos o valor que está localizado nesse endereço de memória para carregar e escrever no registrador do exemplo.




