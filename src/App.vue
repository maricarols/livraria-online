<script setup>
import { ref } from "vue";
let pesquisando = ref(``);
function limpar() {
  pesquisando.value = ``;
}
let listaDeLivros = ref([
  { id: 1, name: 'Anne de Green Gables', autor: 'Lucy Maud Montgomery', preco: 24.00, sinapse: 'Os irmãos Matthew e Marilla Cuthbert moram em uma linda propriedade em Green Gables. Eles decidem adotar um garoto órfão para ajudar nos serviços gerais, em troca de moradia. Qual não foi a surpresa dos dois ao receberem, em vez de um garoto, a adorável Anne, uma menina ruiva, sensível e cheia de vida. Encante-se com essa história adaptada por Donaldo Buchweitz a partir do adorável clássico de Lucy Maud Montgomery, Anne de Green Gables.', capa: 'public/images/annedegreengables.jpg', contador: 1 },

  { id: 2, name: 'Emma', autor: 'Jane Austen', preco: 36.00, sinapse: 'Emma Woodhouse, bonita, inteligente, rica e solteira, está perfeitamente feliz com sua vida e não vê necessidade de se apaixonar ou de se casar. Nada, no entanto, a agrada mais do que interferir na vida romântica dos outros. Mas quando ela ignora as advertências do sr. Knightley e tenta arranjar um marido para sua amiga e protegida Harriet Smith, seus planos tão cuidadosamente elaborados não saem como ela imaginava.', capa: 'public/images/emma.jpg', contador: 1 },

  { id: 3, name: 'Jane Eyre', autor: 'Charlotte Brontë', preco: 46.00, sinapse: 'é a autobiografia ficcional da personagem principal que apresenta-se como Jane, órfã de pai e mãe, vivendo infeliz em companhia de parentes que a detestam. Após uma série de confrontos, Jane é enviada para um colégio interno, onde conhece seus primeiros momentos de verdadeira felicidade.', capa: 'public/images/janeyere.jpg', contador: 1 },

  { id: 4, name: 'Orgulho e Preconceito', autor: 'Jane Austen', preco: 19.00, sinapse: 'Elizabeth Bennet vive com sua mãe, pai e irmãs no campo, na Inglaterra. Por ser uma das filhas mais velhas, ela enfrenta uma crescente pressão de seus pais para se casar. Quando Elizabeth é apresentada ao belo e rico Darcy, faíscas voam. Embora haja uma química óbvia entre os dois, a natureza excessivamente reservada de Darcy ameaça a relação.', capa: 'public/images/orgulhoepreconceito.jpg', contador: 1 },

  { id: 5, name: 'Romeu e Julieta', autor: 'William Shakespeare', preco: 37.00, sinapse: 'Romeu e Julieta é uma das mais famosas histórias de amor da literatura. Ela se passa na cidade italiana de Verona, no século 16. Romeu Montecchio e Julieta Capuleto são dois jovens que acabam se apaixonando perdidamente, mas há uma barreira que impede os dois de ficarem juntos: suas famílias são grandes rivais e não permitiriam nunca que os dois se casassem. O ódio entre os Montecchio e os Capuleto não será suficiente para afastar Romeu de Julieta, nesta história que nos faz acreditar no amor eterno.', capa: 'public/images/romeu-e-julieta.jpg', contador: 1, favoritado: false, },

  { id: 6, name: 'O Morro dos Ventos Uivantes', autor: 'Emily Brontë', preco: 29.00, sinapse: 'Único romance da escritora inglesa Emily Brontë, O morro dos ventos uivantes retrata uma trágica história de amor e obsessão em que os personagens principais são a obstinada e geniosa Catherine Earnshaw e seu irmão adotivo, Heathcliff. Grosseiro, humilhado e rejeitado, ele guarda apenas rancor no coração, mas tem com Catherine um relacionamento marcado por amor e ódio.', capa: 'public/images/o-morro-dos-ventos-uivantes.jpg', contador: 1 },

  { id: 7, name: 'Moby-Dick', autor: 'Herman Melville', preco: 31.00, sinapse: 'O livro traz o relato de um marinheiro letrado, Ishmael, sobre a última viagem de um navio baleeiro de Nantucket, o Pequod, que parte da costa leste dos Estados Unidos - com sua tripulação multiétnica - rumo ao Pacífico Sul, onde encontra o imenso cachalote branco que, no passado, arrancara a perna do vingativo capitão Ahab. Ao longo de 135 capítulos, Herman Melville (1819-1891) explora com brilhantismo e ironia os mais variados gêneros literários: da narrativa de viagens ao teatro shakespeareano, do sermão à poesia popular, passando pela descrição científica e a meditação filosófica.', capa: 'public/images/Moby_Dick.jpg', contador: 1 },

  { id: 8, name: 'O Retrato de Dorian Gray', autor: 'Oscar Wilde', preco: 29.00, sinapse: '"O Retrato de Dorian Gray", de Oscar Wilde, conta a história de Dorian Gray, um jovem bonito que tem seu retrato pintado por Basil Hallward. Dorian se torna obcecado com a ideia de manter-se eternamente jovem e o retrato reflete os pecados de Dorian, envelhecendo e marcando-o enquanto ele permanece imune aos efeitos do tempo.', capa: 'public/images/oretratodedoriangray.jpg', contador: 1 },

  { id: 9, name: 'Razão e Sensibilidade', autor: 'Jane Austen', preco: 27.00, sinapse: 'Quando o pai de Elinor Dashwood morre, as finanças de sua família vão mal das pernas. Após a mudança dos Dashwood para um chalé em Devonshire, a irmã de Elinor, Marianne, fica dividida entre o belo John Willoughby e um coronel mais velho, Brandon. Enquanto isso, as esperanças românticas de Elinor com Edward Ferrars são prejudicadas devido ao seu compromisso.', capa: 'public/images/razaoesensibilidade.jpg', contador: 1 },

  { id: 10, name: 'Crime e Castigo', autor: 'Fiódor Dostoiévski', preco: 50.00, sinapse: 'Raskólnikov é um jovem intelectual que decide matar a agiota Aliena Ivánovna. Ao refletir sobre as motivações de seu crime, ele julga que a morte da mulher pode ajudar a outras pessoas. No entanto, o personagem busca mesmo é atingir um estado amoral.', capa: 'public/images/crimeecastigo.jpg', contador: 1 },

  { id: 11, name: 'Persuasão', autor: 'Jane Austen', preco: 20.00, sinapse: 'A senhorita Elliot, filha de um importante, porém falido baronete, de repente se vê obrigada a conviver com um amor do passado. Anos antes, Anne aceitara se casar com Frederick Wentworth; contudo, pelo fato de ele não ser rico nem influente, ela foi persuadida pela família e por uma grande amiga a romper o noivado.', capa: 'public/images/persuasao.jpg', contador: 1 },

  { id: 12, name: 'Hamlet', autor: 'William Shakespeare', preco: 33.00, sinapse: 'Neste clássico da literatura mundial, um jovem príncipe se reúne com o fantasma de seu pai, que alega que seu próprio irmão, agora casado com sua viúva, o assassinou. O príncipe cria um plano para testar a veracidade de tal acusação, forjando uma brutal loucura para traçar sua vingança.', capa: 'public/images/hamlet.webp', contador: 1 },

  { id: 13, name: 'O Fantasma da Ópera', autor: 'Gaston Leroux', preco: 29.90, sinapse: 'Enquanto estranhos acontecimentos assombram a Ópera de Paris, a jovem Christine começa a ouvir uma voz que identifica como a do Anjo da Música que a guiará ao sucesso. O dono dessa voz, entretanto, é um homem enigmático que de fato a ensina a cantar como uma estrela, mas logo, tomado por ciúme e rancor, a arrasta aos sinistros porões do teatro. Paixão e música pouco a pouco se convertem em medo e dor, imprimindo um tom intenso e arrepiante a este romance inesquecível.', capa: 'public/images/ofantasmadaopera.jpg', contador: 1 },

  { id: 14, name: 'Drácula', autor: 'Bram Stoker', preco: 18.00, sinapse: 'O jovem advogado inglês Jonathan Harker é enviado por seu patrão à Transilvânia, no leste da Europa, para atender um misterioso cliente. Ao chegar, descobre que seu anfitrião é, na realidade, um poderoso vampiro: o conde Drácula. Consegue então fugir para a Inglaterra. Lá, ao lado de sua noiva, Mina, e do Professor Van Helsing, Jonathan travará uma batalha de vida e morte contra o poder maligno de Drácula. Adaptação de Fiona Macdonald do Drácula, de Bram Stoker, a mais célebre e aterrorizante história de vampiros de todos os tempos.', capa: 'public/images/dracula.jpg', contador: 1 },

  { id: 15, name: 'Frankenstein', autor: 'Mary Shelley', preco: 21.90, sinapse: 'Victor Frankenstein desde muito jovem se dedicou aos estudos da filosofia e das ciências naturais. Até que, em uma experiência bem-sucedida (que lhe sugou a energia e o afastou do convívio dos seus entes queridos), ele foi capaz de dar vida a um ser de feições e trejeitos assustadores. A partir de então, criador e criatura passam a viver um jogo de perseguição repleto de sangue e horror.', capa: 'public/images/frankenstein.webp', contador: 1 },
]);
function sorteando() {
  const sorteio = Math.floor(Math.random() * listaDeLivros.value.length);
  return listaDeLivros.value[sorteio];
}

let livroSelecionado = ref(sorteando());
</script>

<template>
     <header>
      <div class="logo">
        <a href="index.html">
          <img src="../public/images/logo.png" alt="">
        </a>
      </div>
      <div class="pesquisa">
        <input type="text" placeholder="Pesquisar" v-model="pesquisando">
        <span class="fa-solid fa-magnifying-glass" style="color: #ca8e82;" @click="limpar"></span>
      </div>
      <ul class="menu">
        <li>Termos</li>
        <li>Equipe</li>
        <li>Envio</li>
        <li>Devoluções</li>
        <li>
          <a href="#">
            <span class="fa-solid fa-cart-shopping"></span>
          </a>
        </li>
        <li class="coracao">
          <a href="#">
            <span class="fa-solid fa-heart"></span>
          </a>
        </li>
        <li>
          <a href="#">
            <span class="fa-solid fa-user"></span>
          </a>
        </li>
      </ul>
    </header>
    <main>
      <section class="exibicao">
        <div class="texto">
          <p class="livroAbril">Livro de Abril</p>
          <h1 class="nome">{{ livroSelecionado.name }}</h1>
          <p class="autor">{{ livroSelecionado.autor }}</p>
          <p class="sinapse">{{ livroSelecionado.sinapse }}</p>

        </div>
        <div>
          <p class="capa"><img class="principal" :src="livroSelecionado.capa" alt="#"></p>
        </div>
      </section>
    </main>
</template>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0vw 0 0 0;
  border-bottom: #f2d6ce solid 1px;
  padding-bottom: 2vw;

}

div.logo {
  margin-left: 3vw;
  margin-top: 1vw;
}

.logo img {
  height: 6vw;
  width: 6vw;
  border-radius: 100%;
}

header ul {
  display: flex;
  margin: 0 6vw 0 0;
}

header li {
  margin: 0 2vw;
}

header li p {
  color: #292421;
}

input {
  border: none;
  background-color: #f2d6ce;
  padding: 0.5vw 10vw 0.5vw 0.5vw;
  outline: none;
  font-family: "Nunito", sans-serif;
  color: #ca8e82;
}

input::placeholder {
  color: #ca8e82;
  font-family: "Nunito", sans-serif;
}

div.pesquisa {
  display: flex;
  align-items: center;
  background-color: #f2d6ce;
  padding: 0 1vw;
  border-radius: 10vw;
  margin: 0 2vw 0 3vw;
}

li span {
  font-size: 1vw;
}

li.coracao span {
  border-right: #f2d6ce solid 2px;
  border-left: #f2d6ce solid 2px;
  padding: 0 2vw 0 2vw;
}
header li span {
  color: #ca8e82;
}

header li:hover span {
  color: #a07168;

}

header li:hover {
  color: #a16e6e;
  cursor: pointer;
}

header span:hover {
  color: #a16e6e;
  cursor: pointer;
}
img.principal {
  flex: 1 1 400px;
  width: 14vw;
  height: 19vw;
}

section.exibicao {
  display: flex;
  margin: 3vw 0 0 0;
  border-bottom: #f2d6ce solid 1px;
  padding-bottom: 3vw;
}

section.exibicao div.texto {
  margin-left: 15vw;
}

section.exibicao p.livroAbril {
  margin: 2vw 0 0 0;
  color: #ca8e82;
  border: #ca8e82 solid 1.5px;
  padding: 0.7vw;
  font-size: 1vw;
  font-family: "Nunito", sans-serif;
  width: 15%;
  font-weight: 600;
  text-align: center;
}

section.exibicao h1 {
  margin: 3vw 0 0 0;
  font-weight: 600;
  font-size: 3rem;
  font-family: "DM Serif Display", serif;

}

section.exibicao p.autor {
  margin-top: 1vw;
  font-size: 1.2rem;
}
p.sinapse {
  margin-top: 2vw;
  width: 90%;
  color: #292421;
}

div p.capa {
  margin: 3vw 15vw 0 2vw;
}

div p.capa img {
  width: 20vw;
  height: 30vw;
  box-shadow: 4px 4px 6px black;
}

</style>
