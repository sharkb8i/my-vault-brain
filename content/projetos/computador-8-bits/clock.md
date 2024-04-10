---
title: Clock
tags:
- vhdl
---
> _Falar mais da parte teórica aqui..._

Também é um módulo **flip-flop**, o qual às vezes são chamados de **registradores**; é a mesma coisa.

A grande maioria dos projetos VHDL utiliza lógica sincronizada, também conhecida como lógica síncrona _(synchronous logic)_ ou lógica sequencial _(sequencial logic)_.

Um processo com clock é acionado apenas por um sinal de clock mestre, e não quando qualquer outro sinal de entrada muda.

O flip-flop é um circuito _sample-and-hold_, o que significa que ele copia o valor da entrada para a saída quando chega a borda ascendente do sinal de clock, pois nesse caso é um acionado com borda positiva. A saída é então mantida estável no valor amostrado até a próxima borda ascendente do relógio ou até que o sinal de reset seja pulsado.

![](https://cdn.vhdlwhiz.com/wp-content/uploads/2016/11/flipflop.gif)

##### Exemplo de flip-flop acionado por borda positiva com reset negativo:

```vhdl
-- clock-model1.vhd

LIBRARY ieee;
USE ieee.std_logic_1164.ALL;
USE ieee.numeric_std.ALL;

ENTITY clock-model1
    PORT(
        CLK   :  IN std_logic;    -- Clock
        N_RST :  IN std_logic;    -- Negative Reset
        IPT   :  IN std_logic;    -- Input
        OPT   : OUT std_logic;    -- Output
    );
END ENTITY clock-model1;

ARCHITECTURE main OF clock-model1 IS
BEGIN
    -- Flip-flop with synchronized reset
    PROCESS(CLK) IS
    BEGIN
        IF rising_edge(CLK) THEN
            IF N_RST = '0' THEN
                OUTPUT <= '0';
            ELSE
                OUTPUT <= INPUT;
            END IF;
        END IF;
    END PROCESS;
END ARCHITECTURE main;
```

##### Referências

https://vhdlwhiz.com/clocked-process/