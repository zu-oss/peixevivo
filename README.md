>**Projeto de Extensão Acadêmica — FATEC** | Curso: Tecnologia em Informática para Negócios (Comunicação e Expressão)

# 🐟 Restaurante & Choperia Peixe-Vivo

Site vitrine institucional desenvolvido como **Projeto de Extensão** para o curso de **Tecnologia em Informática para Negócios** (disciplina de Comunicação e Expressão) da **FATEC**, em colaboração com o **Restaurante Peixe-Vivo**, localizado às margens do Rio Grande em **Icém - SP**.

---

## 🎯 Sobre o Projeto

O objetivo do projeto é ajudar a criar umaa presença digital do restaurante, apresentando sua história de mais de 70 anos, estrutura, cardápio, choperia, eventos e localização de forma acessível, rápida e responsiva para clientes em dispositivos móveis e computadores.

### 🎨 Conceito e Identidade Visual
Como referência de identidade visual, foram utilizados o **logotipo** e o **cardápio impresso** tradicionais do restaurante. O design expande essa linguagem para o ambiente digital simulando uma imersão — *"como um mergulho pelo Rio Grande"* —* **Profundidade e Movimento:** O plano de fundo apresenta ondas em degradê com movimento suave e contínuo, transitando de tons mais claros na superfície para tons mais profundos de azul na base da página, remetendo às águas do rio e ao design do menu, com contrastes escuros para facilitar a leitura e dar destaque para a vista da do Rio Grande e Usina de Marimbondo diretamente da varanda do Restaurante e os pratos da casa.

---

## ✨ Seções e Funcionalidades

* **Home:** Apresentação institucional, vista panorâmica e horário de funcionamento.
* **Promoções:** Destaques e ofertas especiais da casa.
* **Cardápio & Choperia:** Exibição dos pratos tradicionais à base de peixes frescos e bebidas.
* **Sobre Nós & História:** Trajetória do restaurante desde sua fundação e marco histórico da visita de Juscelino Kubitschek.
* **Eventos & Estrutura:** Demonstração do espaço para eventos, varanda panorâmica e área kids.
* **Contato e Localização:** Mapa interativo integrado (Google Maps) e com 2 botão direto para atendimento via WhatsApp.

---

## 🛠️ Tecnologias e Otimizações Aplicadas

* **HTML5** (estrutura semântica em página única / *one-page layout*)
* **CSS3** (estilização responsiva e identidade visual e animações basicas)
* **JavaScript** (Script leve dedicado exclusivamente ao funcionamento do menu responsivo (*menu hambúrguer*) em dispositivos móveis e ao efeito visual de destaque/brilho na seção de promoções.)
* **Otimização de Performance:** Conversão de ativos visuais para o formato **WebP**, redimensionamento responsivo e carregamento sob demanda (*lazy loading*), reduzindo o peso inicial da página de ~30 MB para ~2 MB.

---

## 👥 Equipe e Orientação

**Desenvolvimento — Grupo HexaZets:**
* Paulo H. B. Castrequini
* João P. Pagotto
* Danty M. B. dos Santos

**Professores Orientadores:**
* Lucimar Sasso Vieira
* Lucimeirie Maria Schinelo

**Parceiro / Cliente:**
* Restaurante & Choperia Peixe-Vivo (Icém - SP)





##Destaques do Site e Codigo 

##Identidade Visual Pt1

A identidade do site foi pensada como um mergulho pelo Rio Grande, puxando a referência das ondas e dos tons de azul da logo e do cardápio do restaurante."

"Para criar essa sensação de profundidade, fizemos um fundo fixo em degradê que vai do azul mais claro no topo até um azul bem escuro no fundo da página — como descer na água — e sobre ele colocamos 6 camadas de divs que viram ondas animadas no próprio CSS, com algumas indo para um lado e outras no sentido inverso."

"As seções e cartões recebem um visual translúcido estilo vidro, para não pesar e deixar o fundo aparecer de leve. Tudo isso é centralizado no :root com variáveis reutilizáveis — inclusive o desenho da onda em SVG — que usamos tanto no fundo quanto nas faixas onduladas das seções, nos posts de rede social e no efeito de onda ao passar o mouse nos menus.

1. Variáveis reutilizáveis no :root (style.css)
Mostra a onda em SVG e os tokens de vidro/cor reaproveitados no projeto inteiro:

:root {
  --onda: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1200 120' preserveAspectRatio='none'%3E%3Cpath d='M0,60 C200,20 400,20 600,60 S1000,100 1200,60 V120 H0 Z'/%3E%3C/svg%3E");

  --azul-claro: #5ec2ec;
  --faixa: rgba(2, 26, 58, 0.55);
  --vidro: rgba(255, 255, 255, 0.10);
  --borda-vidro: 1px solid rgba(255, 255, 255, 0.30);
}

2. Container de divs virando ondas no degradê (index.html + style.css)
No index.html:

<div class="oceano-caixa">
  <div class="ondas-wrapper">
    <div class="wave onda1"></div>
    <div class="wave onda2"></div>
    <div class="wave onda3"></div>
    <div class="wave onda4"></div>
    <div class="wave onda5"></div>
    <div class="wave onda6"></div>
  </div>
</div>

No style.css (degradê claro em cima/escuro embaixo, camadas .onda1 a .onda6, reverse nas pares e animação @keyframes fluxo):
.oceano-caixa {
  position: fixed;
  inset: 0;
  height: 100vh;
  background: linear-gradient(to bottom, #2a8fc4 0%, #0e6ba8 30%, #03406f 65%, #022a52 100%);
  z-index: -9999;
}

.wave {
  mask-image: var(--onda), linear-gradient(#000, #000);
  animation: fluxo var(--vel) linear infinite;
}

.onda1 { --topo: 0vh;  --alt: 170px; --cor: #5ec2ec; --vel: 22s; opacity: 0.22; }
/* ... até .onda6 (--topo: 72vh; --alt: 50px; --cor: #021a3a; --vel: 60s; opacity: 0.38;) */

.onda2, .onda4, .onda6 {
  animation-direction: reverse;
}

@keyframes fluxo {
  from { transform: translate3d(0, 0, 0); }
  to   { transform: translate3d(-800px, 0, 0); }
}

3. Aparência de vidro nos cartões e seções (style.css)
.moldura-fachada,
.evento-foto,
.evento,
.card-contato,
.bloco-historia,
.cartao-menu,
.destaque-casa,
.menu-acordeao {
  background: var(--vidro);
  border: var(--borda-vidro);
  backdrop-filter: blur(6px);
}
									 
4. Onda no topo das seções (fachada e redes sociais) e no hover do menu (style.css)
Segunda sessão (fachada) e posts da rede social (redes_social): 

#fachada::before,
#redes_social::before {
  content: "";
  position: absolute;
  left: 0;
  top: -59px;
  width: 100%;
  height: 59px;
  background-color: var(--faixa);
  mask-image: var(--onda);
  mask-size: 800px 100%;
  mask-repeat: repeat-x;
}
Interação com o menu / itens (summary e .item-menu):
.menu-acordeao summary::before,
.item-menu::before {
  content: "";
  position: absolute;
  inset: 0;
  z-index: -1;
  background: rgba(94, 194, 236, 0.28);
  transform: translateY(100%);
  transition: transform 0.5s ease;
  mask-image: var(--onda), linear-gradient(#000, #000);
}

.menu-acordeao summary:hover::before,
.item-menu:hover::before {
  transform: translateY(0);
  animation: ondaMover 1.6s linear infinite;
}
