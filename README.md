# chat-v2

> “us mlk è lizo~~”
> (a descrição do repositório original)

Em 18 de abril de 2016, um chat com Firebase começou como brincadeira de uma tarde entre colegas de trabalho. Em duas horas a graça já era outra: usar o chat para mexer na tela dos outros, trocando o fundo, tocando som, apagando tudo. Foram 132 commits num único `index.html`, quase todos feitos direto pelo site do GitHub, com a página no ar para a sala inteira.

Este repositório guarda essa história e uma recriação dela:

- **[O relatório](https://jonathansantos.github.io/chat-v2/)**: a história contada commit a commit, o que há de interessante no código e uma leitura de 2026.
- **[A simulação](https://jonathansantos.github.io/chat-v2/simulacao.html)**: uma sala com três colegas imaginários, para sentir como era. O botão “Reviver 2016” encena os doze momentos principais.
- **[O original](original/index.html.txt)**: o arquivo de 2016 como terminou, guardado em texto.

> [!NOTE]
> O projeto nasceu no meu perfil antigo do GitHub, [**@JonathanSantos-zz**](https://github.com/JonathanSantos-zz), em [JonathanSantos-zz/chat](https://github.com/JonathanSantos-zz/chat). Este repositório é a continuação dele no meu perfil atual, [@JonathanSantos](https://github.com/JonathanSantos), com o histórico de 2016 preservado: os 132 primeiros commits daqui são os de lá.

Feito com [Rafael Escobar](https://github.com/Nhanderu) (70 commits) e Giovanni Perillo (9 commits), e com um quarto colega que jogou sem commitar.

## A simulação é só uma simulação

O chat de 2016 inseria mensagens como HTML e executava scripts recebidos pelo banco. A recriação não faz nenhuma das duas coisas:

- não há servidor nem outras pessoas: os colegas são personagens com roteiro;
- o que você digita aparece sempre como texto;
- as peças (fundo, som, tremer, “oloco”, limpar, trocar de nome) são uma lista fixa de funções.

Pelo mesmo motivo, o arquivo original está como `.txt`: publicado como página, ele voltaria a executar o que encontrasse no banco.

## O que tem aqui

```
index.html            o relatório
simulacao.html        a recriação, num arquivo só, sem dependências
original/
└── index.html.txt    o chat como estava no último commit de 2016
vendor/jonacode/      o editor Jonacode, usado para destacar código no relatório
```

Tudo abre direto do disco, sem servidor e sem build.

---

# Relatório resumido

*A versão completa, com os trechos de código e um testador do filtro de 2016, está em [index.html](https://jonathansantos.github.io/chat-v2/).*

## Em números

| | |
|---|---|
| Primeiro commit | 18/04/2016 13:09 |
| Último commit | 12/12/2016 18:40 |
| Commits | 132, todos em `index.html` |
| Primeiro dia | 48 commits em 4h14 |
| Autores | Rafael Escobar 70 · Jonathan 53 · Giovanni Perillo 9 |
| Tamanho | 201 linhas no início, 304 no auge, 276 no fim |

## A história pelos commits

**Segunda, 18/04.** Às 13:09 nasce o “Chat BRQ”, com Material Design Lite, Firebase e nomes sorteados (“Chaves do bonde”). Às 13:42 chega o primeiro pull request, “as cor”, com um bug corrigido três minutos depois (“arruma”). Às 14:12, para mostrar imagens, a mensagem passa de `innerText` para `innerHTML`: é o commit que muda o rumo da tarde. Às 15:00 surge um comando que executa código só para quem digita; às 15:07 ele passa a valer para todos. Às 15:47 aparece o primeiro filtro de palavras, com a condição invertida, consertada dez minutos depois. A lista de bloqueio cresce em tempo real até o fim do dia, e às 17:02 chega o player de áudio.

**Terça, 19/04.** O dia abre com a palavra `while` entrando na lista. Às 10:37 uma refatoração troca a inserção por `.text()` e, sem querer, fecha a porta do HTML por 41 minutos. Às 13:28 a execução é comentada; às 13:30, descomentada; às 13:31, a palavra “querido” é bloqueada. Às 14:06 um commit faz todos aparecerem com o mesmo nome, e às 14:52 “johnny” e “jonathan” entram no bloqueio. Giovanni resolve a rolagem automática com o comentário `//fuckyeah²`. Às 15:53 nasce o comando `oloco`, que apaga a tela de todos e deixa um texto quicando.

**Quarta, 20/04.** Botão para apagar o banco inteiro, filtro refatorado em função, notificações do sistema. Quem recusa a permissão recebe `alert("Seu feio.")` e vira “Sou Feio”.

**25/04.** Chaves para desligar scripts e notificações só para si. A brincadeira esfria.

**11/08.** Reescrita completa: de 304 para 120 linhas. Vira “CMD”, um terminal verde em que todos são “Anonymous” e o texto aparece letra por letra, abrindo com `TERMINAL - WE ARE ANONYMOUS`.

**12/12.** Em 56 minutos, os scripts voltam e chega a “criptografia jd5”, um hash caseiro com alfabeto próprio de 58 símbolos, para reconhecer um administrador. No último commit, o administrador é o único protegido pelo filtro.

## O que eu curti

- **O repositório como campo de batalha.** A lista de palavras bloqueadas é um placar: cada palavra nova é a marca de um ataque que deu certo minutos antes.
- **Ataque e defesa pelas mesmas mãos.** Quem escreve o filtro é quem cria o comando que passa por ele.
- **Um minuto entre o erro e o conserto.** Pelo menos nove commits quebram a página, e todos são consertados em até três minutos, quase sempre por outra pessoa.
- **A reviravolta de agosto.** Jogar fora dois terços do código e resolver tudo com uma ideia só, a máquina de escrever.
- **O humor.** “as cor”, “PREGUIÇA REINA”, “pogueta”, `//fuckyeah²`, “Sou Feio” e listas de nomes que são uma cápsula do Brasil de 2016.

## Olhando de 2026

O grupo construiu, sem usar esse nome, um laboratório de XSS armazenado. E o histórico registra três lições em miniatura: lista de bloqueio não segura ninguém; o conserto certo (`.text()` no lugar de `.html()`) apareceu por acidente e durou 41 minutos, porque matava a funcionalidade de que todos gostavam; e filtro que roda no navegador de quem recebe é opcional para quem ataca.
