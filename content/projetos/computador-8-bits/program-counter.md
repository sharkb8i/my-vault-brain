---
title: Program Counter (PC)
tags:
- vhdl
---

> _Falar mais da parte teórica aqui..._

#### DM74LS161A/163A

Os [DM74LS161A](../../docs/datasheets/74LS161_fairchild.pdf) e DM74LS163A são contadores binários de 4 bits.

Esses contadores síncronos e predefinidos apresentam um carry lookahead interno para aplicação em projetos de contagem de alta velocidade.

A saída carry é decodificada por meio de uma porta NOR, evitando assim picos durante o modo normal de operação de contagem.

Uma entrada de clock com buffer aciona os quatro flip-flops na borda ascendente (positiva) da forma de onda de entrada do clock.

**Características:**
- Tempo de propagação típico do clock para saída Q de 14 ns;
- Frequência de clock típica de 32 MHz.

##### Exemplo:

```vhdl
-- DM74LS161A.vhd

LIBRARY ieee;
USE ieee.std_logic_1164.ALL;
USE ieee.numeric_std.ALL;

ENTITY DM74LS161A                 -- 161A/163A
    PORT(
        CLEAR    :  IN std_logic; -- PIN 1
        CLOCK    :  IN std_logic; -- PIN 2  Clock é negado, portanto inicia em 0
        DATA_A   :  IN std_logic; -- PIN 3
        DATA_B   :  IN std_logic; -- PIN 4
        DATA_C   :  IN std_logic; -- PIN 5
        DATA_D   :  IN std_logic; -- PIN 6
        ENABLE_P :  IN std_logic; -- PIN 7  NEGADO
        GND      :  IN std_logic; -- PIN 8  (?)
        LOAD     :  IN std_logic; -- PIN 9
        ENABLE_T :  IN std_logic; -- PIN 10 NEGADO
        VCC      :  IN std_logic; -- PIN 16
        QD       : OUT std_logic; -- PIN 11
        QC       : OUT std_logic; -- PIN 12
        QB       : OUT std_logic; -- PIN 13
        QA       : OUT std_logic; -- PIN 14
        RP_CARRY : OUT std_logic; -- PIN 15
    );
END ENTITY;

ARCHITECTURE main OF DM74LS161A IS
BEGIN
    -- Comportamento
END ARCHITECTURE;
```

#### DM74LS245A

**Datasheets:**
- [[../../docs/datasheets/74LS245_national.pdf]]
- [[../../docs/datasheets/74LS245_texas.pdf]]

...

##### Referências:

https://www.engineersgarage.com/vhdl-tutorial-19-designing-a-4-bit-binary-counter-using-vhdl/

https://www.youtube.com/watch?v=Fm4q6fCcJjg

https://staff.fysik.su.se/~silver/digsyst/lab6.html