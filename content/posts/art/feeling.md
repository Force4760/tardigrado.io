+++
title = "Étude about feeling"
date = "2022-03-19"
tags = ['Coding', 'Arte Generativa']
description = "Preencher círculos de forma artística"
+++

Era uma noite normal, estava cansado, mas não queria dormir. Decidi abrir o _youtube_ e descobri um vídeo sobre a melhor forma de selecionar um ponto dentro de um _círculo_ .

Então comecei a pensar em qual seria a melhor forma de _preencher um círculo_, e aqui mostro o resultado.

- _Language_: _JavaScript_
- _Libraries_: _P5.js_

<br></br>

---

## Linhas

A primeira tentativa foi escolher dois pontos aleatórios na circunferência e unir os mesmos através de uma linha reta. Os pontos são selecionados através dos ângulos, tal que _a ∈ [0,2π]_, ou seja, o ângulo está em _radianos_ , e as coordenadas finais serão obtidas através da utilização de _coordenadas polares_.

```js
function lines() {
  let a = random(2 * PI);
  let b = random(2 * PI);

  line(r * cos(a), r * sin(a), r * cos(b), r * sin(b));
}
```

![Lines 1](/images/feeling/lines.png)

<br></br>

A segunda tentativa consistiu em escolher pontos, desta vez não necessáriamente pertencentes à circunferência, e unir
os mesmo através de retas. Para escolher cada ponto, selecionei um ângulo tal que _a ∈ [0,2π]_ e um raio tal que _r₂ ∈ [ 0, r ]_

```js
function lines2() {
  let a = random(2 * PI);
  let b = random(2 * PI);

  let r1 = random(r);
  let r2 = random(r);

  line(r1 * cos(a), r1 * sin(a), r2 * cos(b), r2 * sin(b));
}
```

![Lines 2](/images/feeling/lines2.png)

<br></br>

De seguida, apenas alterei a forma como os raios dos pontos são selecionados, utilizando uma função random diferente _rand_.

```js
function lines3() {
  let a = random(2 * PI);
  let b = random(2 * PI);

  let r1 = rand(r);
  let r2 = rand(r);

  line(r1 * cos(a), r1 * sin(a), r2 * cos(b), r2 * sin(b));
}
```

![Lines 3](/images/feeling/lines3.png)

<br></br>

## Círculos

Para os antigos, Círculos eram perfeitos, então, porque não tentar preencher um círculo com outros círculos?

A primeira versão, começa por rodar a tela num ângulo aleatório a, tal que _a ∈ [0,2π]_. De seguida, escolhe um raio rr tal que _rr ∈ [0,r]_ e desenha um círculo tangente à circunferência original ou seja, com centro nas coordenadas _(r-rr, 0)_ e raio _rr_, mas devemos nos lembrar que aplicamos previamente um raotação de ângulo _a_.

```js
function circs() {
  push();
  rotate(random(2 * PI));
  let rr = random(r);

  circle(r - rr, 0, rr);
  pop();
}
```

![Circles 1](/images/feeling/circs.png)

<br></br>

A segunda versão, segue o mesmo princípio da primeira, apenas alterando a forma como escolhe o raio.

```js
function circs2() {
  push();
  rotate(random(2 * PI));
  let rr = rand(r);

  circle(r - rr, 0, rr);
  pop();
}
```

![Circles 2](/images/feeling/circs2.png)

<br></br>

## Pontos

O terceiro método baseia-se em desenhar pontos dentro do círculo.

A primeira versão escolhe um _ângulo a_ e um _raio rr_, e através de coordenadas polares desenha esse ponto.

```js
function dots(n) {
  let a = random(2 * PI);
  let rr = random(r);

  point(rr * cos(a), rr * sin(a));
}
```

![Dots 1](/images/feeling/dots.png)

<br></br>

A segunda versão escolhe um _ângulo a_, mas a função que seleciona o raio é _rand_.

```js
function dots2(n) {
  let a = random(2 * PI);
  let rr = rand(r);
  point(rr * cos(a), rr * sin(a));
}
```

![Dots 2](/images/feeling/dots3.png)

<br></br>

Por fim, são selecionadas _duas coordenadas, x e y_, tal que _x, y ∈ [-r,r]_.
Este método tem o problema de alguns dos possíveis pontos não estarem contidos no círculo, pelo que utilizei o _teorema de pitágoras_, para saber se a distância entre este ponto e o centro era menor ou igual que o raio _(x² + y² ≤ r²)_. No caso do ponto não estar contido, a função seria repetida, até que o ponto selecionado estivesse contido no círculo.

```js
function dots3() {
  while (true) {
    let x = random(-r, r);
    let y = random(-r, r);

    if (x * x + y * y <= r * r) {
      point(x, y);
      return;
    }
  }
}
```

![Dots 3](/images/feeling/dots2.png)

<br></br>

---

_[1]_: [Vídeo](https://www.youtube.com/watch?v=4y_nmpv-9lI&t=166s)

_[2]_: [P5.js](https://p5js.org/)

_[3]_: [Radianos](https://upchieve.org/blog/2021/4/18/what-are-radians)

_[4]_: [Coordenadas polares](https://tutorial.math.lamar.edu/Classes/CalcII/PolarCoordinates.aspx) são um sistema de coordenadas, onde, em vez de duas coordenadas _x_ e _y_ temos uma coordenada _r (distância à origem)_ e uma coordenada _φ (ângulo feito com o semi-eixo positivo Ox)_. Este tipo de coordenadas facilida o estudo de movimentos circulares por exemplo e a conversão entre coordenadas polares e cartezianas pode ser feita da seguinte forma:

- Polares → Cartezianas:

  - _x = r · cos(φ)_
  - _y = r · sin(φ)_

- Cartezianas → Polares:
  - _r = √(x² + y²)_
  - _φ =_
    - _arctan(y/x) if x > 0_
    - _arctan(π + y/x) if x < 0_

_[5]_: a função rand foi definida por mim da seguinte forma:

```js
function rand(m) {
  return sqrt(random(m) * random(m));
}
```

Ou seja, utilizando _√(m₁+m₂)_, onde m₁ e m₂ são números aleatórios tal que: _m₁,m₂ ∈ [0,m]_
