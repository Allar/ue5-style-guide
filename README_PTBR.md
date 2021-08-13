# [Gamemakin](https://gamemak.in) UE4 - Guia de Estilo() {

*Uma abordagem bastante razoável para Unreal Engine 4*

Inspirado pelo [Guia de Estilo Airbnb Javascript](https://github.com/airbnb/javascript).

[![Analytics](https://ga-beacon.appspot.com/UA-80567399-1/repo?useReferrer)](#)

## Nota de tradução

Foram mantidos os nomes e expressões em inglês comumente usadas na Unreal Engine e.x. "texture", "material", "asset", etc.

## Aviso de Repo

O repo original agora está localizado em https://github.com/Allar/ue5-style-guide. O branch padrão deste repositório foi renomeado `main`.

## Atualmente, é para UE4.
## Documentação do Guia de Estilo e Linter

Mais documentação técnicas sobre o Linter e o Guia de Estilo pode ser encontrada na página: [LeiaOsDocumentos](https://ue4-style-guide.readthedocs.io/en/latest/).

## Debata este guia de estilo

Gamemakin LLC tem um canal Discord público em http://discord.gamemak.in com um canal #linter se você gostaria de debater sobre o Guia de Estilo e o plugin Linter.

## Link para este documento

Cada seção deste Guia de Estilo é numerada para facilitar a referência e o link. Você pode vincular a qualquer seção diretamente acrescentando uma hashtag e o número da seção ao final de http://ue4.style
Por exemplo, se você deseja enviar a alguém o primeiro princípio deste Guia de Estilo, você deve colocar `#0.1`, resultando em http://ue4.style#0.1.

## Forks e Traduções

Se você fez um fork ou tradução que não é adequada para uma solicitação pull neste repo, envie uma solicitação pull para adicionar sua fork ou tradução aqui.

* [Tradução para Coreano](https://github.com/ymkim50/ue4-style-guide/blob/master/README_Kor.md) por ymkim50
* [Tradução para Russo](https://github.com/CosmoMyzrailGorynych/ue4-style-guide-rus/blob/master/README.md) por CosmoMyzrailGorynych
* [Tradução para Japonês](https://github.com/akenatsu/ue4-style-guide/blob/master/README.jp.md) por akenatsu
* [Tradução para Chinês](https://github.com/skylens-inc/ue4-style-guide/blob/master/README.md) por Beijing Skylens Tech.
* [Tradução para Português do Brasil](https://github.com/danlvr/ue5-style-guide/blob/main/README_PTBR.md) por danlvr.

## Terminologia Importante

<a name="terms-level-map"></a>
##### Levels/Maps

A palavra 'map' geralmente se refere ao que a pessoa chama de 'level' e pode ser usado indistintamente. Veja a história deste termo [aqui](https://en.wikipedia.org/wiki/Level_(video_gaming)).

##### Identifiers
Um `Identifier` é qualquer coisa que se pareça ou sirva como um "nome". Por exemplo, o nome de um "asset", ou o nome de um "material", ou a propriedade de um "blueprint", uma variável, ou um nome de pasta, ou para um nome de uma linha de tabela de dados, etc...

<a name="terms-cases"></a>
##### Caixa Alta e Caixa Baixa

Existem algumas maneiras diferentes de você `NomearComCaixaAltaOuCaixaBaixa`. Aqui estão alguns tipos mais comuns:

> ###### PascalCase
>
> Capitalize cada palavra e remova todos os espaços, e.x. `DesertEagle`, `GuiaDeEstilos`, `UmaSerieDePalavras`.
> 
> ###### camelCase
>
> A primeira letra é sempre minúscula mas todas as palavras seguintes começam com maiúsculas, e.x. `desertEagle`, `guiaDeEstilos`, `umaSerieDePalavras`.
>
> ###### Snake_case
>
> As palavras podem começar arbitrariamente com letras maiúsculas ou minúsculas, mas as palavras são separadas por um sublinhado, e.g. `desert_Eagle`, `Guia_de_Estilos`, `uma_Serie_de_Palavras`.

<a name="terms-var-prop"></a>
##### Variáveis / Propriedades

As palavras 'variável' e 'propriedade' na maioria dos contextos são intercambiáveis. No entanto, se ambas forem usados juntos no mesmo contexto considere:

<a name="terms-property"></a>
###### Propriedade
Normalmente se refere a uma variável definida em uma classe. Por exemplo, se `BP_Barril` tinha uma variável `bExplodiu`, `bExplodiu` pode ser referido como uma propriedade de `BP_Barril`. 

Quando no contexto de uma classe, muitas vezes é usado para implicar o acesso a dados previamente definidos.

<a name="terms-variable"></a>
###### Variável
Normalmente se refere a uma variável definida como um argumento de função ou uma variável local dentro de uma função.

Quando no contexto de uma classe, é freqüentemente usado para transmitir um debate sobre sua definição e o que ela conterá.

<a name="0"></a>
## 0. Princípios

Esses princípios foram adaptados de [guida de estilo idomatic.js](https://github.com/rwaldron/idiomatic.js/).

<a name="0.1"></a>
### 0.1 Se o seu projeto UE4 já tem um Guia de Estilo, você deve segui-lo.

Se você estiver trabalhando em um projeto ou com uma equipe que possui um guia de estilo pré-existente, ele deve ser respeitado. Qualquer inconsistência entre um guia de estilo existente e este guia, deve-se seguir o existente.

Os guias de estilo devem ser documentos vivos. Você deve propor alterações de guia de estilo a um guia de estilo existente, bem como a este guia, se achar que a alteração beneficia todos os seus usos.

> #### "Discussões sobre o estilo são desnecessárias. Deve sempre haver um Guia de Estilo e você deve segui-lo."
> [_Rebecca Murphey_](https://rmurphey.com)

<a name="0.2"></a>
### 0.2 Toda estrutura, assets e código em qualquer projeto Unreal Engine 4 devem parecer que foram criados por uma única pessoa, não importa quantas pessoas contribuíram.

Mudar de um projeto para outro não deve causar uma reaprendizagem de estilo e estrutura. A conformidade com um Guia de Estilo remove suposições e ambigüidades desnecessárias.

Também permite uma criação e manutenção mais produtivas, pois não é necessário pensar no estilo. Simplesmente siga as instruções. Este guia de estilo foi escrito com as práticas recomendadas em mente, o que significa que, ao seguir este guia de estilo, você também minimizará problemas difíceis de rastrear.

<a name="0.3"></a>
### 0.3 Amigos não deixam amigos terem estilo ruim.

Se você vir alguém trabalhando contra um guia de estilo ou sem nenhum guia de estilo, tente corrigi-lo.

Ao trabalhar em uma equipe ou discutir em uma comunidade, como a [Unreal Slackers](http://join.unrealslackers.org/), é muito mais fácil ajudar e pedir ajuda quando as pessoas são consistentes. Ninguém gosta de ajudar a desemaranhar o "espaguete" do Blueprint de alguém ou lidar com assets que tenham nomes que eles não conseguem entender.

Se você está ajudando alguém cujo trabalho segue um Guia de Estilo diferente, mas consistente e lógico, você deve ser capaz de se adaptar a ele. Se eles não estiverem de acordo com nenhum Guia de Estilo, indique-os aqui.

<a name="0.4"></a>
### 0.4 Uma equipe sem um Guia de Estilo não é a minha equipe.

Ao ingressar em uma equipe Unreal Engine 4, uma de suas primeiras perguntas deve ser "Você tem um Guia de Estilo?". Se a resposta for não, você deve duvidar da capacidade deles de trabalhar em equipe.

<a name="0.5"></a>
### 0.5 Não quebre a lei

A Gamemakin LLC não é composta por advogados, mas não introduza ações e comportamentos ilegais em um projeto, incluindo, mas não se limitando a:

* Não distribua conteúdo para o qual você não tem os direitos de distribuição
* Não infrinja o material protegido por direitos autorais ou marca registrada de outra pessoa
* Não roube conteúdo
* Siga as restrições de licenciamento de conteúdo, por exemplo atributo quando as atribuições são necessárias

<a name="00"></a>
## 00. Opiniões Globalmente Impostas

@TODO: Faça esta a Seção 1 e atualize este documento de acordo. Ou talvez não?

<a name="00.1"></a>
### 00.1 Caracteres Proibidos

#### Identifiers

Em qualquer `Identifier` de qualquer tipo, **nunca** use o seguinte, a menos que seja obrigado:

* Espaço em branco de qualquer tipo
* Barras invertidas `\`
* Símbolos e.x. `#!@$%`
* Qualquer caractere Unicode

Um `Identifier` deve ter apenas os seguintes caracteres, quando possível (expressão regular `[A-Za-z0-9_]+`)

* ABCDEFGHIJKLMNOPQRSTUVWXYZ
* abcdefghijklmnopqrstuvwxyz
* 1234567890
* _ (moderadamente)


O motivo para isso é que garantirá a maior compatibilidade de todos os dados em todas as plataformas em todas as ferramentas e ajudará a evitar o tempo de inatividade devido ao tratamento potencialmente incorreto de caracteres para identificadores em códigos que você não controla.

<a name="toc"></a>
## Índice

> 1. [Convenções de nomenclatura de assets](#anc)
> 1. [Estrutura de Diretório](#structure)
> 1. [Blueprints](#bp)
> 1. [Static Meshes](#s)
> 1. [Particle Systems](#ps)
> 1. [Levels / Maps](#levels)
> 1. [Textures](#textures)

<a name="anc"></a>
<a name="1"></a>
## 1. Convenções de Nomenclatura de Assets

As convenções de nomenclatura devem ser tratadas como lei. Um projeto que está em conformidade com uma convenção de nomenclatura pode ter seus assets gerenciados, pesquisados, analisados e mantidos com uma facilidade incrível.

Geralmente são prefixadas com um acrônimo do tipo de asset seguido por um sublinhado (_).

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 Nome Base do Asset - `Prefixo_NomeBaseDoAsset_Variante_Sufixo`

Todos os assets devem ter um _Nome Base do Asset_. Um nome de asset básico representa um agrupamento lógico de assets relacionados. Qualquer asset que faça parte deste grupo lógico deve seguir o padrão de  `Prefixo_NomeBaseDoAsset_Variante_Sufixo`.

Mantendo o padrão `Prefixo_NomeBaseDoAsset_Variante_Sufixo` em mente e usar o bom senso geralmente é suficiente para garantir bons nomes de assets. Aqui estão algumas regras detalhadas sobre cada elemento.

`Prefixo` e `Sufixo` devem ser determinados pelo tipo de asset por meio do seguinte tabelas de [Modificador do Nome do Asset](#asset-name-modifiers).

`NomeBaseDoAsset` deve ser determinado por um nome curto e facilmente reconhecível relacionado ao contexto desse grupo de assets. Por exemplo, se você tivesse um personagem chamado Bob, todos os assets de Bob teriam o `NomeBaseDoAsset` de `Bob`.

Para variações únicas e específicas de assets, `Variante` é um nome curto e facilmente reconhecível que representa o agrupamento lógico de assets que são um subconjunto do nome de base de um asset. Por exemplo, se Bob tinha várias skins, essas skins ainda deveriam usar `Bob` assim como `NomeBaseDoAsset` mas inclua um reconhecível `Variante`. Uma skin 'Evil' seria referida como `Bob_Evil` e uma skin 'Retro' seria referida como `Bob_Retro`.

Para variações únicas, mas genéricas de assets, `Variante` é um número de dois dígitos começando em `01`. Por exemplo, se você tem um Ambient Designer gerando rochas indefinidas, eles seriam nomeadas `Rocha_01`, `Rocha_02`, `Rocha_03`, etc. Exceto em raras exceções, você nunca deve exigir um número de variante de três dígitos. Se você tiver mais de 100 assets, deve considerar organizá-los com nomes de base diferentes ou usando vários nomes de variantes.

Dependendo de como suas variantes de assets são feitas, você pode encadear nomes de variantes. Por exemplo, se você estiver criando assets de piso para um projeto Arch Viz, você deve usar o nome de base `Piso` com variantes em cadeia, como `Piso_Marmore_01`, `Piso_Bordo_01`, `Piso_Tile_Quadrados_01`.

<a name="1.1-examples"></a>
#### 1.1 Exemplos

##### 1.1e1 Bob

| Tipo de Asset           | Nome do Asset                                              |
| ----------------------- | ---------------------------------------------------------- |
| Skeletal Mesh           | SK_Bob                                                     |
| Material                | M_Bob                                                      |
| Texture (Diffuse/Albedo)| T_Bob_D                                                    |
| Texture (Normal)        | T_Bob_N                                                    |
| Texture (Evil Diffuse)  | T_Bob_Evil_D                                               |

##### 1.1e2 Rocha

| Tipo de Asset           | Nome do Asset                                              |
| ----------------------- | ---------------------------------------------------------- |
| Static Mesh (01)        | S_Rocha_01                                                 |
| Static Mesh (02)        | S_Rocha_02                                                 |
| Static Mesh (03)        | S_Rocha_03                                                 |
| Material                | M_Rocha                                                    |
| Material Instance (Neve)| MI_Rocha_Neve                                              |

<a name="asset-name-modifiers"></a>
<a name="1.2"></a>
### 1.2 Modificadores de Nome de Asset

Ao nomear um asset, use essas tabelas para determinar o prefixo e sufixo a ser usado com ele [Nome Base do Asset](#base-asset-name).

#### Sections

> 1.2.1 [Mais comum](#anc-common)

> 1.2.2 [Animações](#anc-animations)

> 1.2.3 [Inteligência Artificial](#anc-ai)

> 1.2.4 [Blueprints](#anc-bp)

> 1.2.5 [Materials](#anc-materials)

> 1.2.6 [Textures](#anc-textures)

> 1.2.7 [Miscelâneas](#anc-misc)

> 1.2.8 [Paper 2D](#anc-paper2d)

> 1.2.9 [Física](#anc-physics)

> 1.2.10 [Som](#anc-sounds)

> 1.2.11 [Interface de Usuário](#anc-ui)

> 1.2.12 [Efeitos](#anc-effects)

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 Mais comum

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Mapas           |            |            | [Deve estar em uma pasta chamada Maps.](#2.4) |
| Level (Persistente)     |            | _P         |                                  |
| Level (Audio)           |            | _Audio     |                                  |
| Level (Iluminação)      |            | _Lighting  |                                  |
| Level (Geometria)       |            | _Geo       |                                  |
| Level (Gameplay)        |            | _Gameplay  |                                  |
| Blueprint               | BP_        |            |                                  |
| Material                | M_         |            |                                  |
| Static Mesh             | S_         |            | Muitos usam SM_. Usamos S_.      |
| Skeletal Mesh           | SK_        |            |                                  |
| Texture                 | T_         | _?         | Veja [Textures](#anc-textures)   |
| Particle System         | PS_        |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-animations"></a>
<a name="1.2.2"></a>
#### 1.2.2 Animações

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Aim Offset              | AO_        |            |                                  |
| Aim Offset 1D           | AO_        |            |                                  |
| Animation Blueprint     | ABP_       |            |                                  |
| Animation Composite     | AC_        |            |                                  |
| Animation Montage       | AM_        |            |                                  |
| Animation Sequence      | A_         |            |                                  |
| Blend Space             | BS_        |            |                                  |
| Blend Space 1D          | BS_        |            |                                  |
| Level Sequence          | LS_        |            |                                  |
| Morph Target            | MT_        |            |                                  |
| Paper Flipbook          | PFB_       |            |                                  |
| Rig                     | Rig_       |            |                                  |
| Skeletal Mesh           | SK_        |            |                                  |
| Skeleton                | SKEL_      |            |                                  |

<a name="anc-ai"></a>
<a name="1.2.3"></a>
### 1.2.3 Inteligência Artificial

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_       |            |                                  |
| Behavior Tree           | BT_        |            |                                  |
| Blackboard              | BB_        |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_    |            |                                  |
| Environment Query       | EQS_       |            |                                  |
| EnvQueryContext         | EQS_       | Contexto   |                                  |

<a name="anc-bp"></a>
<a name="1.2.4"></a>
### 1.2.4 Blueprints

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Blueprint               | BP_        |            |                                  |
| Blueprint Component	  | BP_	       | Component  | E.x. BP_InventoryComponent       |
| Blueprint Function Library | BPFL_   |            |                                  |
| Blueprint Interface     | BPI_       |            |                                  |
| Blueprint Macro Library | BPML_      |            | Não use bibliotecas de macro, se possível. |
| Enumeration             | E          |            | Sem sublinhado.                  |
| Structure               | F or S     |            | Sem sublinhado.                  |
| Tutorial Blueprint      | TBP_       |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-materials"></a>
<a name="1.2.5"></a>
### 1.2.5 Materials

| Tipo de Asset                 | Prefixo    | Suffixo    | Notas                            |
| ----------------------------- | ---------- | ---------- | -------------------------------- |
| Material                      | M_         |            |                                  |
| Material (Post Process)       | PP_        |            |                                  |
| Material Function             | MF_        |            |                                  |
| Material Instance             | MI_        |            |                                  |
| Material Parameter Collection | MPC_       |            |                                  |
| Subsurface Profile            | SP_        |            |                                  |
| Physical Materials            | PM_        |            |                                  |
| Decal                         | M_, MI_    | _Decal     |                                  |

<a name="anc-textures"></a>
<a name="1.2.6"></a>
### 1.2.6 Textures

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _O         |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Metallic)      | T_         | _M         |                                  |
| Texture (Packed)        | T_         | _*         | Veja as notas abaixo sobre [pacotes](#anc-textures-packing). |
| Texture Cube            | TC_        |            |                                  |
| Media Texture           | MT_        |            |                                  |
| Render Target           | RT_        |            |                                  |
| Cube Render Target      | RTC_       |            |                                  |
| Texture Light Profile   | TLP        |            |                                  |

<a name="anc-textures-packing"></a>
<a name="1.2.6.1"></a>
#### 1.2.6.1 Pacote de textura
É uma prática comum compactar várias camadas de dados de textura em uma única textura. Um exemplo disso é agregar "Emissive", "Roughness", "Ambient Occlusion" juntos como os canais Vermelho, Verde e Azul de uma textura, respectivamente. Para determinar o sufixo, basta empilhar as letras de sufixo fornecidas de cima, e.g. `_ERO`.

> É geralmente aceitável incluir uma camada Alfa/Opacidade no canal Alfa de Difusão/Albedo e, como essa é uma prática comum, adicionar `A` ao sufixo` _D` é opcional.

Englobar 4 canais de dados em uma textura (RGBA) não é recomendado, exceto para uma máscara Alfa/Opacidade no canal Alfa de Difusão/Albedo, pois uma textura com um canal alfa incorre em mais sobrecarga do que uma sem.

<a name="anc-misc"></a>
<a name="1.2.7"></a>
### 1.2.7 Miscelâneas

| Tipo de Asset              | Prefixo    | Suffixo    | Notas                            |
| -------------------------- | ---------- | ---------- | -------------------------------- |
| Animated Vector Field      | VFA_       |            |                                  |
| Camera Anim                | CA_        |            |                                  |
| Color Curve                | Curve_     | _Color     |                                  |
| Curve Table                | Curve_     | _Table     |                                  |
| Data Asset                 | *_         |            | O prefixo deve ser baseado na classe. |
| Data Table                 | DT_        |            |                                  |
| Float Curve                | Curve_     | _Float     |                                  |
| Foliage Type               | FT_        |            |                                  |
| Force Feedback Effect      | FFE_       |            |                                  |
| Landscape Grass Type       | LG_        |            |                                  |
| Landscape Layer            | LL_        |            |                                  |
| Matinee Data               | Matinee_   |            |                                  |
| Media Player               | MP_        |            |                                  |
| Object Library             | OL_        |            |                                  |
| Redirector                 |            |            | Estes devem ser consertados o mais rápido possível.  |
| Sprite Sheet               | SS_        |            |                                  |
| Static Vector Field        | VF_        |            |                                  |
| Substance Graph Instance   | SGI_       |            |                                  |
| Substance Instance Factory | SIF_       |            |                                  |
| Touch Interface Setup      | TI_        |            |                                  |
| Vector Curve               | Curve_     | _Vector    |                                  |

<a name="anc-paper2d"></a>
<a name="1.2.8"></a>
### 1.2.8 Paper 2D

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Paper Flipbook          | PFB_       |            |                                  |
| Sprite                  | SPR_       |            |                                  |
| Sprite Atlas Group      | SPRG_      |            |                                  |
| Tile Map                | TM_        |            |                                  |
| Tile Set                | TS_        |            |                                  |

<a name="anc-physics"></a>
<a name="1.2.9"></a>
### 1.2.9 Física

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Physical Material       | PM_        |            |                                  |
| Physics Asset	          | PHYS_      |            |                                  |
| Destructible Mesh       | DM_        |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.10"></a>
### 1.2.10 Som

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Dialogue Voice          | DV_        |            |                                  |
| Dialogue Wave           | DW_        |            |                                  |
| Media Sound Wave        | MSW_       |            |                                  |
| Reverb Effect           | Reverb_    |            |                                  |
| Sound Attenuation       | ATT_       |            |                                  |
| Sound Class             |            |            | Sem prefixo/sufixo. Deve ser colocado em uma pasta chamada SoundClasses |
| Sound Concurrency       |            | _SC        | Deve ter o nome de uma SoundClass |
| Sound Cue               | A_         | _Cue       |                                  |
| Sound Mix               | Mix_       |            |                                  |
| Sound Wave              | A_         |            |                                  |

<a name="anc-ui"></a>
<a name="1.2.11"></a>
### 1.2.11 Interface de Usuário

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |
| Slate Brush             | Brush_     |            |                                  |
| Slate Widget Style      | Style_     |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-effects"></a>
<a name="1.2.12"></a>
### 1.2.12 Efeitos

| Tipo de Asset           | Prefixo    | Suffixo    | Notas                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Particle System         | PS_        |            |                                  |
| Material (Post Process) | PP_        |            |                                  |

**[⬆ Voltar ao topo](#table-of-contents)**


<a name="2"></a>
<a name="structure"></a>
## 2. Estrutura do Diretório de Conteúdo

Tão importante quanto os nomes de assets, o estilo da estrutura de diretório de um projeto deve ser considerado lei. As convenções de nomenclatura de assets e a estrutura do diretório de conteúdo andam de mãos dadas, e a violação de qualquer uma delas causa um caos desnecessário.

Existem várias maneiras de definir o conteúdo de um projeto UE4. Nesse estilo, usaremos uma estrutura que depende mais dos recursos de filtragem e pesquisa do Navegador de Conteúdo para aqueles que trabalham com assets para encontrar assets de um tipo específico, em vez de outra estrutura comum que agrupa tipos de assets com pastas.

> Se você estiver usando o prefixo [convenção de nomenclatura] (# 1.2) acima, usar pastas para conter assets de tipos semelhantes, como `Meshes`,` Textures` e `Materials` é uma prática redundante, pois os tipos de assets já são classificados por prefixo, bem como podem ser filtrado no Navegador de Conteúdo.

<a name="2e1"><a>
### 2e1 Exemplo de Estrutura de Conteúdo do Projeto
<pre>
|-- Content
    |-- <a href="#2.2">GenericShooter</a>
        |-- Art
        |   |-- Industrial
        |   |   |-- Ambient
        |   |   |-- Machinery
        |   |   |-- Pipes
        |   |-- Nature
        |   |   |-- Ambient
        |   |   |-- Foliage
        |   |   |-- Rocks
        |   |   |-- Trees
        |   |-- Office
        |-- Characters
        |   |-- Bob
        |   |-- Common
        |   |   |-- <a href="#2.7">Animations</a>
        |   |   |-- Audio
        |   |-- Jack
        |   |-- Steve
        |   |-- <a href="#2.1.3">Zoe</a>
        |-- <a href="#2.5">Core</a>
        |   |-- Characters
        |   |-- Engine
        |   |-- <a href="#2.1.2">GameModes</a>
        |   |-- Interactables
        |   |-- Pickups
        |   |-- Weapons
        |-- Effects
        |   |-- Electrical
        |   |-- Fire
        |   |-- Weather
        |-- <a href="#2.4">Maps</a>
        |   |-- Campaign1
        |   |-- Campaign2
        |-- <a href="#2.8">MaterialLibrary</a>
        |   |-- Debug
        |   |-- Metal
        |   |-- Paint
        |   |-- Utility
        |   |-- Weathering
        |-- Placeables
        |   |-- Pickups
        |-- Weapons
            |-- Common
            |-- Pistols
            |   |-- DesertEagle
            |   |-- RocketPistol
            |-- Rifles
</pre>

Os motivos para essa estrutura estão listados nas subseções a seguir.

### Seções

> 2.1 [Nomes de pasta](#structure-folder-names)

> 2.2 [Pasta de Nível Superior](#structure-top-level)

> 2.3 [Pastas de desenvolvedor](#structure-developers)

> 2.4 [Maps](#structure-maps)

> 2.5 [Core](#structure-core)

> 2.6 [`Assets` e `AssetTypes`](#structure-assettypes)

> 2.7 [Conjuntos Grandes](#structure-large-sets)

> 2.8 [Biblioteca de Materiais](#structure-material-library)


<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Nomes de pasta

Essas são regras comuns para nomear qualquer pasta na estrutura de conteúdo.

<a name="2.1.1"></a>
#### 2.1.1 Sempre use PascalCase[<sup>*</sup>](#terms-cases)

PascalCase refere-se a iniciar um nome com uma letra maiúscula e, em vez de usar espaços, todas as palavras seguintes também começam com uma letra maiúscula. Por exemplo, `DesertEagle`, `RocketPistol`, e `UmaSerieDePalavras`.

Veja [Casos](#terms-cases).

<a name="2.1.2"></a>
#### 2.1.2 Nunca Use Espaços

Reforçando [2.1.1](#2.1.1), nunca use espaços. Os espaços podem fazer com que várias ferramentas de engenharia e processos em lote falhem. Idealmente, a raiz do seu projeto também não deve contém espaços e está localizada em algum lugar como `D:\Project` em vez de `C:\Users\My Name\My Documents\Unreal Projects`.

<a name="2.1.3"></a>
#### 2.1.3 Nunca Use Caracteres Unicode e Outros Símbolos

Se um dos personagens do jogo se chama 'Zoë', o nome da pasta deve ser `Zoe`. Caracteres Unicode podem ser piores do que [Espaços](#2.1.2) para a ferramenta de engenharia e algumas partes do UE4 que também não oferecem suporte a caracteres Unicode em caminhos.

Relacionado a isso, se o seu projeto tiver [problemas inexplicáveis](https://answers.unrealengine.com/questions/101207/undefined.html) e o nome de usuário do seu computador tem um caractere Unicode (ou seja, seu nome é `Zoë`), qualquer projeto localizado na pasta `My Documents` sofrerá com esse problema. Freqüentemente, mover seu projeto para outra pasta como `D:\Project` corrigirá esses problemas.

Usando outros caracteres fora `a-z`, `A-Z`, e `0-9` como `@`, `-`, `_`, `,`, `*`, e `#` também pode levar a problemas inesperados e difíceis de rastrear em outras plataformas, source controls e ferramentas de engenharia mais fracas. 

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 Use Uma Pasta de Nível Superior Para Assets Específicos do Projeto

Todos os assets de um projeto devem existir em uma pasta com o nome do projeto. Por exemplo, se o nome do seu projeto for 'Generic Shooter', _todo_ todo o seu conteúdo deve existir em `Content/GenericShooter`.

> A pasta `Developers` não é para assets dos quais seu projeto depende e, portanto, não é específica do projeto. Consulte [Pastas de desenvolvedor] (# 2.3) para obter detalhes sobre isso.

Existem várias razões para esta abordagem.

<a name="2.2.1"></a>
#### 2.2.1 Sem Assets Globais

Freqüentemente, nos guias de estilo de código está escrito que você não deve poluir o namespace global e isso segue o mesmo princípio. Quando assets podem existir fora de uma pasta de projeto, geralmente se torna muito mais difícil impor um layout de estrutura estrito, pois assets que não estão em uma pasta encorajam o mau comportamento de não ter que organiza-los.

Todo asset deve ter um propósito, caso contrário, ele não pertence a um projeto. Se um asset é um teste experimental e não deve ser usado pelo projeto, deve ser colocado em uma pasta [`Developer`](#2.3).

<a name="2.2.2"></a>
#### 2.2.2 Reduza Conflitos de Migração

Ao trabalhar em vários projetos, é comum que uma equipe copie assets de um projeto para outro, caso tenham feito algo útil para ambos. Quando isso ocorre, a maneira mais fácil de realizar a cópia é usar a funcionalidade Migrar do navegador de conteúdo, pois ela copiará não apenas o asset selecionado, mas todas as suas dependências.

Essas dependências podem facilmente causar problemas. Se os assets de dois projetos não tiverem uma pasta de nível superior e acontecerem de terem assets nomeados de forma semelhante ou já migrados anteriormente, uma nova migração pode apagar acidentalmente quaisquer alterações nos assets existentes.

Esse também é o principal motivo pelo qual a equipe do Marketplace da Epic aplica a mesma política para assets enviados.

Após uma migração, a fusão segura de assets pode ser feita usando a ferramenta 'Substituir referências' no navegador de conteúdo com a clareza adicional de assets não pertencentes à pasta de nível superior de um projeto e claramente aguardando uma fusão. Depois que os assets são mesclados e totalmente migrados, não deve haver outra pasta de nível superior em sua árvore de conteúdo. Este método é _100% _ garantido para tornar todas as migrações que ocorrerem completamente seguras.

<a name="2.2.2e1"></a>
##### 2.2.2e1 Exemplo de Master Material

Por exemplo, digamos que você criou um Master Material em um projeto que gostaria de usar em outro projeto, então migrou esse asset. Se este asset não estiver em uma pasta de nível superior, pode ter um nome como `Content/MaterialLibrary/M_Master`. Se o projeto de destino ainda não tiver um Master Material, isso deve funcionar sem problemas.

Conforme o trabalho em um ou ambos os projetos progride, seus respectivos Master Material podem ser alterados para serem adaptados para seus projetos específicos devido ao curso de desenvolvimento normal.

O problema surge quando, por exemplo, um artista para um projeto criou um bom conjunto modular genérico de static meshes e alguém deseja incluir esse conjunto de static meshes no segundo projeto. Se o artista que criou os recursos usou Material Instances com base em `Content/MaterialLibrary/M_Master` conforme são instruídos, quando uma migração é realizada, há uma grande chance de conflito para o asset migrado anteriormente `Content/MaterialLibrary/M_Master`.

Esse problema pode ser difícil de prever e de explicar. A pessoa que migra as static meshes pode não ser a mesma pessoa que está familiarizada com o desenvolvimento de ambos os Master Material do projeto e pode nem mesmo estar ciente de que as static meshes em questão dependem de Material Instances que, então, dependem do Master Material. A ferramenta Migrar requer que toda a cadeia de dependências funcione, no entanto, será obrigada a pegar `Content/MaterialLibrary/M_Master` quando ela copia esses assets para o outro projeto e sobrescrever o asset existente.

É neste ponto que se os Master Materials para ambos os projetos forem incompatíveis de _qualquer maneira_, você corre o risco de quebrar possivelmente toda a biblioteca de Materials de um projeto, bem como quaisquer outras dependências que já possam ter sido migradas, simplesmente porque os assets não foram armazenados em uma pasta de nível superior. A simples migração de static meshes agora se torna uma tarefa muito ruim.

<a name="2.2.3"></a>
#### 2.2.3 Amostras, Modelos e Conteúdos do Marketplace Estão Livres de Riscos

Uma extensão para [2.2.2](#2.2.2), se um membro da equipe decidir adicionar conteúdo de amostra, arquivos de modelo ou assets que comprou no Marketplace, é garantido, desde que a pasta de nível superior do seu projeto tenha um nome exclusivo, que esses novos assets não interferirão em seu projeto.

Você não pode confiar que o conteúdo do marketplace está em total conformidade com a [regra de pasta de nível superior] (# 2.2). Existem muitos assets que têm a maior parte de seu conteúdo em uma pasta de nível superior, mas também possuem Conteúdo de Amostra da Epic possivelmente modificados, bem como arquivos de nível poluindo a pasta global `Content`.

Ao aderir a [2.2](#2.2), o pior conflito de marketplace que você pode ter é se dois assets de marketplace tiverem o mesmo Conteúdo de Amostra da Epic. Se todos os seus assets estiverem em uma pasta específica do projeto, incluindo conteúdo de amostra que você pode ter movido para a sua pasta, seu projeto nunca será quebrado.

#### 2.2.4 DLC, Subprojetos e Patches São Facilmente Mantidos

Se o seu projeto planeja lançar DLC ou tem vários subprojetos associados a ele que podem ser migrados ou simplesmente não preparados em uma construção, os assets relacionados a esses projetos devem ter sua própria pasta de conteúdo de nível superior separada. Isso torna muito mais fácil cozinhar DLC separados do conteúdo do projeto principal. Os subprojetos também podem ser migrados para dentro e para fora com o mínimo de esforço. Se você precisar alterar um material de um assets ou adicionar algum comportamento de substituição de asset muito específico em um patch, você pode facilmente colocar essas alterações em uma pasta de patch e trabalhar com segurança sem a chance de quebrar o projeto principal.

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Use a Pasta Developers Para Testes Locais

Durante o desenvolvimento de um projeto, é muito comum que os membros da equipe tenham uma espécie de 'sandbox' onde podem experimentar livremente sem arriscar o projeto principal. Como esse trabalho pode estar em andamento, esses membros da equipe podem querer colocar seus assets em um servidor de source control do projeto. Nem todas as equipes exigem o uso de pastas Developers, mas aquelas que as usam costumam ter um problema comum com assets enviados ao source control.

É muito fácil para um membro da equipe usar acidentalmente assets que não estão prontos para uso, o que causará problemas quando esses assets forem removidos. Por exemplo, um artista pode estar iterando em um conjunto modular de static meshes e ainda trabalhando para obter o tamanho e o encaixe da grade corretos. Se um world designer ver esses assets na pasta principal do projeto, ele pode usá-los em um nível sem saber que podem estar sujeitos a mudanças e/ou remoções. Isso causa uma grande quantidade de retrabalho para todos na equipe resolverem.

Se esses assets modulares fossem colocados em uma pasta de desenvolvedor, o world designer nunca deveria ter tido um motivo para usá-los e todo o problema nunca aconteceria. O navegador de conteúdo tem opções de exibição específicas que ocultam as pastas do desenvolvedor (elas ficam ocultas por padrão), tornando impossível o uso acidental de assets do desenvolvedor em uso normal.

Assim que os recursos estiverem prontos para uso, o artista simplesmente precisa mover os recursos para a pasta específica do projeto e corrigir os redirecionadores. Isso é essencialmente 'promover' os assets do experimental para a produção.

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 Todo Arquivo de Mapa[<sup>*</sup>](#terms-level-map) Pertence a Uma Pasta Chamada Maps

Os arquivos de mapa são incrivelmente especiais e é comum que cada projeto tenha seu próprio sistema de nomenclatura de mapa, especialmente se eles trabalharem com subníveis ou níveis de streaming. Não importa qual sistema de organização de mapas está em vigor para o projeto específico, todos os níveis devem pertencer a `/Content/Project/Maps`.

Ser capaz de dizer a alguém para abrir um mapa específico sem ter que explicar onde ele está economiza muito tempo e melhora a 'qualidade de vida' em geral. É comum que os níveis estejam dentro de subpastas de `Maps`, tal como `Maps/Campaign1/` ou `Maps/Arenas`, mas o mais importante aqui é que todos eles existem dentro `/Content/Project/Maps`.

Isso também simplifica o trabalho de cozinhar para os engenheiros. Combinar os níveis de um processo de compilação pode ser extremamente frustrante se eles tiverem que vasculhar pastas arbitrárias. Se os mapas de uma equipe estão todos em um só lugar, é muito mais difícil acidentalmente não preparar um mapa em uma construção. Ele também simplifica os scripts de construção de iluminação, bem como os processos de controle de qualidade.

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 Use uma Pasta `Core` Para Blueprints Críticos e Outros Assets

Use a pasta`/Content/Project/Core` para assets que são absolutamente fundamentais para o funcionamento de um projeto. Por exemplo, `GameMode`, `Character`, `PlayerController`, `GameState`, `PlayerState`, base e os Blueprints relacionados devem residir aqui.

Isso cria uma mensagem muito clara "não toque nestes" para os outros membros da equipe. Os que não são engenheiros devem ter muito poucos motivos para entrar na pasta `Core`. Seguindo um bom estilo de estrutura de código, os designers devem fazer seus ajustes de jogabilidade em classes filhas que expõem a funcionalidade. Os world designers devem usar Blueprints pré-fabricados em pastas designadas em vez de abusar potencialmente das classes base.

Por exemplo, se o seu projeto requer "pickups" que podem ser colocados em um nível, deve existir uma classe de "pickup" base em `Core/Pickups` que define o comportamento básico para uma "pickup". Coletas específicas, como Health ou Ammo, devem existir em uma pasta como `/Content/Project/Placeables/Pickups/`. Os designers de jogos podem definir e ajustar opções nesta pasta da maneira que quiserem, mas não devem tocar `Core/Pickups` pois eles podem interromper involuntariamente "pickups" em todo o projeto.

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 Não Crie Pastas Chamadas `Assets` ou `AssetTypes`

<a name="2.6.1"></a>
#### 2.6.1 Criar uma pasta chamada `Assets` é redundante.

Todos assets são assets.

<a name="2.6.2"></a>
#### 2.6.2 Criar uma pasta chamada `Meshes`, `Textures`, ou `Materials` é redundante.

Todos os nomes de assets são nomeados com seu tipo de asset em mente. Essas pastas oferecem apenas informações redundantes e o uso dessas pastas pode ser facilmente substituído pelo sistema de filtragem robusto e fácil de usar que o Navegador de Conteúdo oferece.

Quer apenas ver static mesh em `Environment/Rocks/`? Basta ativar o filtro Static Mesh. Se todos os assets forem nomeados corretamente, eles também serão classificados em ordem alfabética, independentemente dos prefixos. Quer visualizar static meshes e skeletal meshes? Basta ligar os dois filtros. Isso elimina a necessidade de selecionar duas pastas com `Control-Click` na visualização em árvore do navegador de conteúdo.

> Isso também estende o nome do caminho completo de um asset para muito poucos benefícios. O prefixo `S_` para uma static mesh tem apenas dois caracteres, enquanto `Meshes/`tem sete caracteres.

Não fazer isso também previne de alguém colocar uma static mesh ou uma textura em uma pasta `Materials`.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Conjunto de Assets Muito Grandes Tem Seu Próprio Layout de Pasta

Isso pode ser visto como uma pseudo-exceção para [2.6](#2.6).

Existem certos tipos de assets que possuem um grande volume de arquivos relacionados, onde cada asset tem uma finalidade única. Os dois mais comuns são assets de animação e áudio. Se você tiver mais de 15 desses assets que pertencem um ao outro, eles devem estar juntos.

Por exemplo, as animações que são compartilhadas por vários personagens devem estar em `Characters/Common/Animations` e pode ter subpastas como `Locomotion` ou `Cinematic`.

> Isso não se aplica a assets como texturas e materiais. É comum que uma pasta `Rochas` tenha uma grande quantidade de texturas se houver uma grande quantidade de pedras, no entanto, essas texturas geralmente estão relacionadas apenas a algumas pedras específicas e devem ser nomeadas apropriadamente. Mesmo que essas texturas sejam parte de uma [Biblioteca de Materials](#2.8).

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `Biblioteca de Materials`

Se o seu projeto faz uso de master materials, layered materials, ou qualquer forma de materiais reutilizáveis ou texturas que não pertençam a nenhum subconjunto de assets, esses assets devem estar localizados em `Content/Project/MaterialLibrary`.

Desta forma materials 'global' têm um lugar e são facilmente localizados.

> Isso também torna incrivelmente fácil aplicar uma política de 'use material instances only' dentro de um projeto. Se todos os artistas e assets deveriam estar usando instâncias de material, então os únicos assets materials regulares que deveriam existir estão dentro desta pasta. Você pode verificar isso facilmente procurando por base materials em qualquer pasta que não seja o `MaterialLibrary`.

A `MaterialLibrary` não precisa consistir puramente em materials. Texturas de utilitários compartilhados, funções materiais e outras coisas dessa natureza devem ser armazenadas aqui também em pastas que indicam sua finalidade. Por exemplo, texturas de ruído genéricas devem estar localizadas em `MaterialLibrary/Utility`.

Qualquer material de teste ou depuração deve estar dentro de `MaterialLibrary/Debug`. Isso permite que os materiais de depuração sejam facilmente retirados de um projeto antes do envio e torna incrivelmente aparente se os assets de produção os estão usando se forem mostrados erros de referência.

<a name="2.9"></a>
<a name="structure-no-empty-folders"></a>
### 2.9 Sem Pastas Vazias

Simplesmente não deve haver pastas vazias. Eles confundem o navegador de conteúdo.

Se você descobrir que o navegador de conteúdo tem uma pasta vazia que não pode ser excluída, faça o seguinte:
1. Certifique-se de usar o controle de origem.
1. Execute imediatamente Fix Up Redirectors em seu projeto.
1. Navegue até a pasta no disco e exclua os assets dentro dela.
1. Feche o editor.
1. Certifique-se de que seu estado de source control está sincronizado (ou seja, se estiver usando Perforce, execute um Reconcile Offline Work em seu diretório de conteúdo)
1. Abra o editor. Confirme se tudo ainda está funcionando conforme o esperado. Caso contrário, reverta, descubra o que deu errado e tente novamente.
1. Certifique-se de que a pasta já foi removida.
1. Envie as alterações para o source control.

**[⬆ Voltar ao topo](#table-of-contents)**


<a name="3"></a>
<a name="bp"></a>
## 3. Blueprints

Esta seção se concentrará nas classes do Blueprint e em seus aspectos internos. Quando possível, as regras de estilo estão em conformidade com [Epic's Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard).

Lembre-se: Blueprinting comporta mal os erros, cuidado! (Frase por [KorkuVeren](http://github.com/KorkuVeren))

### Sections

> 3.1 [Compilando](#bp-compiling)

> 3.2 [Variáveis](#bp-vars)

> 3.3 [Funções](#bp-functions)

> 3.4 [Gráficos](#bp-graphs)

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 Compilando

Todos os blueprints devem ser compilados com nenhum aviso e nenhum erro. Você deve corrigir os avisos e erros do blueprint imediatamente, pois eles podem rapidamente se transformar em um comportamento inesperado muito assustador.

*Não* envie projetos corrompidos ao source control. Se você deve armazená-los no source control, arquive-os.

Projetos corrompidos podem causar problemas que se manifestam de outras maneiras, como referências quebradas, comportamento inesperado, falhas de cozimento e recompilação desnecessária frequente. Um projeto quebrado tem o poder de quebrar todo o seu jogo.

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 Variáveis

As palavras `variable` e `property` podem ser usadas alternadamente.

#### Seções

> 3.2.1 [Nomeação](#bp-vars)

> 3.2.2 [Editável](#bp-vars-editable)

> 3.2.3 [Categorias](#bp-vars-categories)

> 3.2.4 [Acesso](#bp-vars-access)

> 3.2.5 [Avançado](#bp-vars-advanced)

> 3.2.6 [Transiente](#bp-vars-transient)

> 3.2.7 [Config](#bp-vars-config)

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 Nomenclatura

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 Substantivos

Todos os nomes de variáveis que não são booleans devem ser substantivos claros, não ambíguos e descritivos.

<a name="3.2.1.2"></a>
<a name="bp-var-naming-case"></a>
##### 3.2.1.2 PascalCase

Todas as variáveis não booleanas devem estar na forma de [PascalCase](#terms-cases).

<a name="3.2.1.2e"></a>
###### 3.2.1.2e Exemplos:

* `Score`
* `Kills`
* `TargetPlayer`
* `Range`
* `CrosshairColor`
* `AbilityID`

<a name="3.2.1.3"></a>
<a name="bp-var-bool-prefix"></a>
##### 3.2.1.3  Prefix `b` Para Boolean 

Todos os booleans devem ser nomeados em PascalCase, mas prefixados com uma minúscula `b`.

Exemplo: Use `bDead` e `bEvil`, **não use** `Dead` ou `Evil`.

Editores Blueprint UE4 sabem não colocar o `b` em exibições user-friendly da variável.

<a name="3.2.1.4"></a>
<a name="bp-var-bool-names"></a>
##### 3.2.1.4 Nomes de Booleans 

<a name="3.2.1.4.1"></a>
###### 3.2.1.4.1 Informações Gerais e Condições Independentes

Todos os booleans devem ser nomeados como adjetivos descritivos, quando possível, se representarem informações gerais. Não inclua palavras que expressem a variável como uma pergunta, como `Is`. Isso é reservado para funções.

Exemplo: Use `bDead` e `bHostile` **não use** `bIsDead` ou `bIsHostile`.

Tente não usar verbos como `bRunning`. Os verbos tendem a levar a estados complexos.

<a name="3.2.1.4.2"></a>
###### 3.2.1.4.2 Condições Complexas

Não use booleans para representar condições complexas e/ou dependentes. Isso torna a adição e remoção das condições complexas mais difíceis de ler. Em vez disso, use uma enumeração.

Exemplo: Ao definir uma arma, **não** use `bReloading` e `bEquipping` se uma arma não pode recarregar e ser equipada. Defina uma enumeração chamada `EWeaponState` e usar uma variável com este tipo chamada `WeaponState` em vez disso. Isso torna muito mais fácil adicionar novos estados às armas.

Exemplo: **Não** use `bRunning` se você também precisa de `bWalking` ou `bSprinting`. Isso deve ser definido como uma enumeração com nomes de estado claramente definidos.

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 Contexto Deve Ser Considerado

Todos os nomes de variáveis não devem ser redundantes com seu contexto, pois todas as referências de variáveis no Blueprint sempre terão contexto.

<a name="3.2.1.5e"></a>
###### 3.2.1.5e Exemplos:

Considere um Blueprint chamado `BP_PlayerCharacter`.

**Ruim**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

Todas essas variáveis são nomeadas de forma redundante. Está implícito que a variável pertence ao `BP_PlayerCharacter`  porque é o `BP_PlayerCharacter` que está definindo essas variáveis.

**Bom**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

<a name="3.2.1.6"></a>
<a name="bp-vars-naming-atomic"></a>
##### 3.2.1.6  _Não_ Inclua Nomes de Tipo Atômico

Variáveis atômicas ou primitivas são variáveis que representam dados em sua forma mais simples, como booleans, integers, floats e enumerações.

Strings e vectors são considerados atômicos em termos de estilo ao trabalhar com Blueprints, no entanto, eles não são tecnicamente atômicos.

> Enquanto vectors consiste de três floats, vectors muitas vezes podem ser manipulados como um todo, assim como rotators.

> _Não_ considere Text Variables como atômicas, elas estão escondendo a funcionalidade de localização. O tipo atômico de uma string de caracteres é `String`, não `Text`.

Variáveis atômicas não devem ter seu nome de tipo em seu nome.

Exemplo: Use `Score`, `Kills`, e `Description` **não use** `ScoreFloat`, `FloatKills`, `DescriptionString`.

A única exceção a esta regra é quando uma variável representa 'um número de' algo a ser contado _e_ quando usar um nome difícil de ler sem um tipo de variável.

Exemplo: Um gerador de cerca precisa gerar um número X de postes. Armazene X em `NumPosts` ou `PostsCount` em vez de `Posts` como `Posts` pode potencialmente ser lido como um Array de um tipo de variável chamado `Post`.

<a name="3.2.1.7"></a>
<a name="bp-vars-naming-complex"></a>
##### 3.2.1.7 Inclua Nomes de Tipo Não Atômico

Variáveis não atômicas ou complexas são variáveis que representam dados como uma coleção de variáveis atômicas. Structs, Classes, Interfaces, e primitivas with com comportamento oculto, como `Text` e `Name` todos se qualificam sob esta regra.

> Enquanto um Array de um tipo de variável atômica é uma lista de variáveis, Arrays não altera a 'atomicidade' de um tipo de variável.

Essas variáveis devem incluir seu nome de tipo, ainda considerando seu contexto.

Se uma classe possui uma instância de uma variável complexa, e.x. se um `BP_PlayerCharacter` possui um `BP_Hat`, deve ser armazenado como o tipo de variável, sem nenhuma modificação de nome.

Exemplo: Use `Hat`, `Flag`, e `Ability` **não use** `MyHat`, `MyFlag`, e `PlayerAbility`.

Se uma classe não possui o valor que uma variável complexa representa, você deve usar um substantivo junto com o tipo de variável.

Exemplo: Se um `BP_Turret` tem a capacidade de mirar um `BP_PlayerCharacter`, deve armazenar seu alvo como `TargetPlayer` como quando no contexto de `BP_Turret` deve ficar claro que é uma referência a outro tipo de variável complexa que não possui.


<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Arrays

Arrays segue as mesmas regras de nomenclatura acima, mas deve ser nomeado como um substantivo no plural.

Exemplo: Use `Targets`, `Hats`, e `EnemyPlayers`, **não use** `TargetList`, `HatArray`, `EnemyPlayerArray`.


<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 Variáveis Editáveis

Todas as variáveis que são seguras para alterar o valor de para configurar o comportamento de um blueprint devem ser marcadas como `Editable`.

Por outro lado, todas as variáveis que não são seguras para alteração ou não devem ser expostas aos designers _não_ devem ser marcadas como editáveis, a menos que por razões de engenharia a variável deva ser marcada como `Expose On Spawn`.

Não marque variáveis arbitrariamente como `Editable`.

<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 Tooltips

Todas variáveis `Editable`, incluindo aqueles marcados como editáveis, apenas para que possam ser marcados como `Expose On Spawn`, deve ter uma descrição em seus campos de `Tooltip` que explique como a alteração desse valor afeta o comportamento do blueprint.

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
##### 3.2.2.2 Sliders e Intervalos de Valor

Todas variáveis `Editable` deve fazer uso de um slider e um intervalo de valor se houver um valor para o qual uma variável _não_ deve ser definida.

Exemplo: Um blueprint que gera postes de cerca pode ter uma variável editável chamada `PostsCount` e um valor de -1 não faria nenhum sentido. Use os campos de intervalo para marcar 0 como o mínimo.

Se uma variável editável é usada em um Construction Script, deve ter um "Slider Range" razoável definido para que alguém não possa acidentalmente atribuir a ele um grande valor que poderia travar o editor.

Um "Value Range" só precisa ser definido se os limites de um valor forem conhecidos. Enquanto um "Slider Range" evita entradas acidentais de um grande número, um indefinido "Value Range" permite que um usuário especifique um valor fora do "Slider Range" que pode ser considerado 'perigoso', mas ainda válido.

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 Categorias

Se uma classe tem apenas um pequeno número de variáveis, as categorias não são obrigatórias.

Se uma class tem uma quantidade moderada de variáveis (5-10), todas variáveis `Editable` deve ter uma categoria não padrão atribuída. Uma categoria comum é `Config`.

Se uma class tem uma grande quantidade de variáveis, todas variáveis `Editable` deve ser categorizado em subcategorias usando a categoria `Config` como a categoria base. Variáveis não editáveis devem ser categorizadas em categorias descritivas que descrevem seu uso.

> Você pode definir subcategorias usando a barra vertical `|`, e.x. `Config | Animations`.

Exemplo: Um conjunto de variáveis de classe de arma pode ser organizado como:

	|-- Config
	|	|-- Animations
	|	|-- Effects
	|	|-- Audio
	|	|-- Recoil
	|	|-- Timings
	|-- Animations
	|-- State
	|-- Visuals

<a name="3.2.4"></a>
<a name="bp-vars-access"></a>
#### 3.2.4 Nível de acesso variável

Em C ++, as variáveis têm um conceito de nível de acesso. Público significa que qualquer código fora da classe pode acessar a variável. Protegido significa que apenas a classe e quaisquer classes filhas podem acessar essa variável internamente. Privado significa que apenas esta classe e nenhuma classe filha pode acessar esta variável.

Blueprints atualmente não tem um conceito definido de acesso protegido.

Trate a variável `Editable` como variáveis públicas. Trate as variáveis não editáveis como variáveis protegidas.

<a name="3.2.4.1"></a>
<a name="bp-vars-access-private"></a>
##### 3.2.4.1 Variáveis Privadas

A menos que se saiba que uma variável só deve ser acessada dentro da classe em que está definida e nunca em uma classe filha, não marque as variáveis como privadas. Até que as variáveis possam ser marcadas `protected`, reserve particular para quando você tiver certeza absoluta de que deseja restringir o uso de classes filhas.

<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
#### 3.2.5 Display Avançado

Se uma variável deve ser editável, mas muitas vezes intocada, marque-a como `Advanced Display`. Isso torna a variável oculta, a menos que a seta de exibição avançada seja clicada.

Para encontrar a opção `Advanced Display`, ela é listada como uma variável avançada exibida na lista de detalhes da variável.

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6 Variáveis Transientes

Variáveis transientes são variáveis que não precisam ter seu valor salvo e carregado, e possuem um valor inicial igual a zero ou nulo. Isso é útil para referências a outros objetos e atores cujo valor não é conhecido até o tempo de execução. Isso evita que o editor salve uma referência a ele e acelera o salvamento e o carregamento da classe de blueprint.

Por causa disso, todas as variáveis transientes sempre devem ser inicializadas como zero ou nulas. Fazer o contrário resultaria em erros difíceis de depurar.

<a name="3.2.7"></a>
<a name="bp-vars-config"></a>
#### 3.2.8 Variáveis de configuração

Não use a flag `Config Variable`. Isso torna mais difícil para os designers controlar o comportamento do blueprint. Variáveis de configuração só devem ser usadas em C ++ para variáveis raramente alteradas. Pense neles como variáveis `Advanced Advanced Display`.

<a name="3.3"></a>
<a name="bp-functions"></a>
### 3.3 Functions, Events, e Event Dispatchers

Esta seção descreve como você deve criar functions, events, e event dispatchers. Tudo o que se aplica a funções também se aplica a events, salvo indicação contrária.

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Nomenclatura de função

A nomenclatura de functions, events, e event dispatchers são extremamente importante. Com base apenas no nome, certas suposições podem ser feitas sobre as funções. Por exemplo:

* É uma função "pure"?
* Está buscando informações de estado?
* É um handler?
* É um RPC?
* Qual é seu propósito?

Essas perguntas e muito mais podem ser respondidas quando as funções são nomeadas apropriadamente.

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 Todas as Funções Devem Ser Verbos

Todas as funções e events realizam alguma forma de ação, seja para obter informações, calcular dados ou fazer algo explodir. Portanto, todas as funções devem começar com verbos. Eles devem ser redigidos no tempo presente sempre que possível. Eles também devem ter algum contexto sobre o que estão fazendo.

Funções `OnRep`, event handlers, e event dispatchers são uma exceção a esta regra.

Bons exemplos:

* `Fire` - Bom exemplo se estiver em uma classe de Personagem/Arma, pois tem contexto. Ruim se estiver em um Barril / Gramado / qualquer classe ambígua.
* `Jump` - Bom exemplo se em uma classe de Personagem, caso contrário, precisa de contexto.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" é um verbo.](http://writingexplained.org/is-is-a-verb)

Maus exemplos:

* `Dead` - Está morto? Vai morrer?
* `Rock`
* `ProcessData` - Ambíguas, essas palavras não significam nada.
* `PlayerState` - Os substantivos são ambíguos.
* `Color` - Verbo sem contexto ou substantivo ambíguo.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Funções Com Propriedade "RepNotify" Sempre `OnRep_Variable`

Todas as funções replicadas com variáveis de notificação devem ter o formato `OnRep_Variable`. Isso é forçado pelo editor Blueprint. Se você está escrevendo um C ++ `OnRep` no entanto, ele também deve seguir esta convenção ao expô-lo para Blueprints.

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Funções de Informação Que Retornam Bool Devem Fazer Perguntas

Ao escrever uma função que não altera o estado ou modifica qualquer objeto e é puramente para: obter informações, estado ou calcular um valor sim/não. Ela deve fazer uma pergunta. Isso também deve seguir [a regra do verbo](#bp-funcs-naming-verbs).

Isso é extremamente importante, pois se uma pergunta não for feita, pode-se presumir que a função executa uma ação e está retornando se essa ação foi bem-sucedida.

Bons exemplos:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" é um verbo.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" é pretérito de "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Use "was" quando se refere a 'quadro anterior' ou 'estado anterior'.
* `CanReload` - ["Can" é um verbo.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Maus exemplos:

* `Fire` - Está em chamas? Vai atirar? Atire?
* `OnFire` - Pode ser confundido com o event dispatcher para disparo.
* `Dead` - Está morto? Vai morrer?
* `Visibility` - É visível? Definir visibilidade? Uma descrição das condições de vôo?

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Event Handlers e Dispatchers Deve Começar Com `On`

Qualquer função que lida com um event ou despacha um event deve começar com `On` e continue a seguir [a regra do verbo](#bp-funcs-naming-verbs). O verbo pode mover-se para o final, no entanto, se o tempo passado for melhor lido.

[Colocações](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation) da palavra `On` estão isentos de seguir a regra do verbo.

`Handle` não é permitido. É 'irreal' usar `On` ao invés de `Handle`, enquanto outras estruturas podem preferir usar `Handle` ao invés de `On`.

Bons exemplos:

* `OnDeath` - Colocação comum em jogos
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Maus exemplos:

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 Chamadas de Procedimento Remoto (RPC) Devem Ser Prefixadas com Destino

Sempre que um RPC é criado, deve ser prefixado com um `Server`, `Client`, ou `Multicast`. Sem exceções.

Após o prefixo, siga todas as outras regras relacionadas à nomenclatura de funções.

Bons exemplos:

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

Maus exemplos:

* `FireWeapon` - Não indica que seja algum tipo de RPC.
* `ServerClientBroadcast` - Confuso.
* `AllNotifyDeath` - Use `Multicast`, nunca `All`.
* `ClientWeapon` - Sem verb, ambíguo.


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 Todas as Funções Devem Ter "Return Nodes"

Todas as funções devem ter return nodes, sem exceções.

Return nodes significam que uma função concluiu sua execução. Como os projetos podem ser preenchidos com `Sequence`, `ForLoopWithBreak`, e reroute nodes reversos, fluxo de execução explícito é importante para leitura, manutenção e depuração mais fáceis dos mesmos.

O compilador Blueprint é capaz de seguir o fluxo de execução e irá avisá-lo se houver um branch de seu código com um retorno não tratado ou fluxo incorreto se você usar return nodes.

Em situações como quando um programador pode adicionar um alfinete a um Sequence node ou adicionar lógica após a conclusão de um "loop for", mas a iteração do loop pode retornar mais cedo, o que geralmente pode resultar em um erro acidental no fluxo de código. Os avisos do compilador Blueprint alertarão a todos sobre esses problemas imediatamente.

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 Nenhuma Função Deve Ter Mais de 50 Nós

Simplesmente, nenhuma função deve ter mais de 50 nós. Qualquer função desse tamanho deve ser dividida em funções menores para facilitar a leitura e manutenção.

Os seguintes nós não são contados, pois são considerados como não aumentando a complexidade da função:

* Comentários
* Route
* Cast
* Obtendo uma Variable
* Quebrando um Struct
* Funções Entry
* Self

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 Todas As Funções Públicas Devem Ter Uma Descrição

Esta regra se aplica mais a blueprints públicas ou do marketplace, para que outras pessoas possam navegar e consumir sua API de blueprint com mais facilidade.

Simplesmente, qualquer função que tenha um especificador de acesso de Public deve ter sua descrição preenchida.

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 Todas Funções de Plugin 'Static' e `BlueprintCallable` Personalizadas Deve Ser Categorizado Pelo Nome do Plugin

Se o seu projeto inclui um plugin que define funções `static` `BlueprintCallable`, ele devem ter sua categoria definida para o nome do plugin ou uma categoria de subconjunto do nome do plugin.

Por exemplo, `Zed Camera Interface` ou `Zed Camera Interface | Image Capturing`.

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Gráficos Blueprint

Esta seção cobre coisas que se aplicam a todos os gráficos do Blueprint.

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 Sem "Espaguete"

Os fios devem ter começo e fim claros. Você nunca deve ter que desembaraçar mentalmente os fios para dar sentido a um gráfico. Muitas das seções a seguir são dedicadas à redução do "espaguete".

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.2 Alinhe Fios, Não Nodes

Sempre alinhe os fios, não os nodes. Você nem sempre pode controlar o tamanho e a localização do pino em um node, mas você sempre pode controlar a localização de um node e, assim, controlar os fios. Fios retos fornecem fluxo linear claro. Fios ondulados desgastam muito a mente. Você pode endireitar os fios usando o comando "Straighten Connections" com os nodes BP selecionados. Atalho: Q

Bom exemplo: os topos dos nodes são escalonados para manter uma linha executiva branca perfeitamente reta.
![Alinhado Por Fios](https://raw.githubusercontent.com/Allar/ue5-style-guide/main/images/bp-graphs-align-wires-good.png "Alinhado Por Fios")

Mau exemplo: Os topos dos nodes são alinhados, criando uma linha executiva branca ondulada.
![Ruim](https://raw.githubusercontent.com/Allar/ue5-style-guide/main/images/bp-graphs-align-wires-bad.png "Ondulado")

Exemplo aceitável: Certos nodes podem não cooperar, não importa como você usa as ferramentas de alinhamento. Nessa situação, tente minimizar a oscilação trazendo o node para mais perto.
![Aceitável](https://raw.githubusercontent.com/Allar/ue5-style-guide/main/images/bp-graphs-align-wires-acceptable.png "Aceitável")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 Linhas de Execução Branca São De Alta Prioridade

Se você alguma vez tiver que decidir entre endireitar uma linha executiva branca linear ou endireitar linhas de dados de algum tipo, sempre endireite a linha executiva branca.

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 Os Gráficos Devem Ser Comentadas Razoavelmente 

Os blocos de nodes devem ser incluídos em comentários que descrevam seu comportamento de nível superior. Embora cada função deva ser bem nomeada para que cada node individual seja facilmente legível e compreensível, grupos de nodes que contribuem para um propósito devem ter seu propósito descrito em um bloco de comentário. Se uma função não tiver muitos blocos de nodes e ficar claro que os nodes estão servindo a um propósito direto no objetivo da função, eles não precisam ser comentados, pois o nome e a descrição da função devem ser suficientes.

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 Os Gráficos Devem Lidar Com Error de Casting Onde Apropriado

Se uma função ou evento presumir que uma conversão sempre é bem-sucedida, ele deve relatar apropriadamente uma falha na lógica se o casting falhar. Isso permite que outras pessoas saibam por que algo que "deveria funcionar" não funciona. Uma função também deve tentar uma recuperação normal após um cast com falha se for conhecido que a referência que está sendo lançada pode falhar durante o cast.

Isso não significa que cada node de cast deve ter sua falha tratada. Em muitos casos, especialmente eventos relacionados a coisas como colisões, espera-se que o fluxo de execução termine silenciosamente em um cast com falha.

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 Os Gráficos Não Devem Ter Nodes Pendentes / Soltos / Mortos

Todos os nodes em todos os gráficos do blueprint devem ter um propósito. Você não deve deixar nodes de blueprint pendurados por aí que não têm propósito ou não são executados.

**[⬆ Voltar ao topo](#table-of-contents)**


<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Static Meshes

Esta seção se concentrará em assets Static Mesh e seus internos.

### Seções

> 4.1 [UVs](#s-uvs)

> 4.2 [LODs](#s-lods)

> 4.3 [Encaixe Modular Sem Socket](#s-modular-snapping)

> 4.4 [Deve Ter Colisão](#s-collision)

> 4.5 [Escala Correta](#s-scaled)

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 UVs Static Mesh 

Se o Linter está reportando maus UVs e você não consegue rastreá-los, abra o arquivo resultante `.log` no seu projeto `Saved/Logs` para obter detalhes exatos sobre o motivo da falha. Espero que incluam essas mensagens no relatório Lint no futuro.

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 Todos Meshes Devem Ter UVs

Bem simples. Todos os meshes, independentemente de como devem ser usadas, não devem ter UVs faltando.

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 Todos Meshes Não deve ter sobreposição UVs de Lightmaps

Bem simples. Todas os meshes, independentemente de como devem ser usadas, devem ter UVs válidos sem sobreposição.

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs Devem Ser Configurados Corretamente

Esta é uma verificação subjetiva por projeto, mas como regra geral, qualquer meshe que pode ser vista em distâncias variáveis deve ter LODs adequados.

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Assests Modulares Sem Soquete Devem Se Encaixar na Grade de Forma Limpa

Esta é uma verificação subjetiva por asset, no entanto, quaisquer assets modulares sem soquete devem se encaixar perfeitamente com base nas configurações de grade do projeto.

Fica a critério do projeto se encaixar com base em uma grade de 2 ou em uma grade de base 10. No entanto, se você estiver criando assets modulares sem soquete para o marketplace, o requisito da Epic é que eles se encaixem perfeitamente quando a grade for configurada para 10 unidades ou mais.

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 Todos Meshes Devem Ter Colisão

Independentemente de um assets ser usado para colisão em um level, todos os meshes devem ter a colisão adequada definida. Isso ajuda o mecanismo com coisas como cálculos de limites, oclusão e iluminação. A colisão também deve ser bem formada para o asset.

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 Todos Meshes Deve Ser Dimensionado Corretamente

Esta é uma verificação subjetiva por projeto; no entanto, todos os assets devem ser dimensionados corretamente para o projeto. Os level designers ou autores de blueprint não devem ter que ajustar a escala dos meshes para que sejam confirmadas no editor. Redimencionar meshes na engine deve se tratadas como uma substituição de escala, não uma correção de escala.

**[⬆ Voltar ao topo](#table-of-contents)**


<a name="5"></a>
<a name="Niagara"></a>
<a name="ng"></a>
## 5. Niagara

Esta seção se concentrará em assets Niagara e seus internos.

### Seções

> 5.1 [Regras de Nomenclatura](#ng-rules)

<a name="5.1"></a>
<a name="ng-rules"></a>
### 5.1 Sem Espaços, Nunca

Conforme mencionado em [00.1 Identificadores Proibidos](#00), espaços e todos os caracteres de espaço em branco são proibidos em identificadores. Isso é especialmente verdadeiro para os sistemas Niagara, pois torna o trabalho com as coisas significativamente mais difícil, senão impossível, ao trabalhar com HLSL ou outros meios de script dentro do Niagara e ao tentar fazer referência a um identificador.

(Contribuição original por [@dunenkoff](https://github.com/Allar/ue5-style-guide/issues/58))


**[⬆ Voltar ao topo](#table-of-contents)**


<a name="6"></a>
<a name="Levels"></a>
<a name="levels"></a>
## 6. Levels / Maps

[Veja a Nota de Terminologia](#terms-level-map) sobre "levels" vs "maps".

Esta seção se concentrará em assets de Level e seus internos.

### Seções

> 6.1 [Sem Erros ou Avisos](#levels-no-errors-or-warnings)

> 6.2 [A Iluminação Deve Ser Construída](#levels-lighting-should-be-built)

> 6.3 [Nenhum "Z Fighting" Visível ao Jogador](#evels-no-visible-z-fighting)

> 6.4 [Regras Específicas de Marketplace](#evels-levels-mp-rules)

<a name="6.1"></a>
<a name="levels-no-errors-or-warnings"></a>
### 6.1 Sem Erros ou Avisos

Todos os levels devem carregar sem erros ou avisos. Se um level for carregado com erros ou avisos, eles devem ser corrigidos imediatamente para evitar problemas em cascata.

Você pode executar uma verificação de mapa em um level aberto no editor usando o comando de console "map check".

Observação: o Linter é ainda mais rígido nisso do que o editor atualmente, e detectará erros de carregamento que o editor resolverá sozinho.

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 A Iluminação Deve Ser Construída

É normal que, durante o desenvolvimento, os levels ocasionalmente não tenham iluminação. Ao fazer um teste/building interna/de envio ou qualquer building a ser distribuída, no entanto, a iluminação deve sempre ser construída.

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 No Player Visible Z Fighting

Nenhum level deve ter [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) em todas as áreas visíveis ao jogador. 

<a name="6.4"></a>
<a name="levels-mp-rules"></a>
### 6.4 Regras Específicas de Marketplace

Se um projeto for vendido no Marketplace UE4, deve seguir essas regras.

<a name="6.4.1"></a>
<a name="levels-mp-rules-overview"></a>
### 6.4.1 Level de Overview 

Se o seu projeto contém assets que devem ser visualizados ou demonstrados, você deve ter um mapa dentro do seu projeto que contém o nome "Overview".

Esse mapa overview, se estiver visualizando assets, deve ser configurado de acordo com [As Diretrizes da Epic](http://help.epicgames.com/customer/en/portal/articles/2592186-marketplace-submission-guidelines-preparing-your-assets#Required%20Levels%20and%20Maps).

Por exemplo, `InteractionComponent_Overview`.

<a name="6.4.2"></a>
<a name="levels-mp-rules-demo"></a>
### 6.4.2 Level Demo

Se o seu projeto contém assets que devem ser demonstrados ou vêm com algum tipo de tutorial, você deve ter um mapa dentro do projeto que contém o nome "Demo". Este nível também deve conter documentação de alguma forma que ilustre como usar seu projeto. Veja o projeto Exemplos de Conteúdo da Epic para bons exemplos de como fazer isso.

Se o seu projeto for uma mecânica de jogo ou outra forma de sistema em oposição a um pacote de arte, isso pode ser o mesmo que seu mapa "Overview".

Por exemplo, `InteractionComponent_Overview_Demo`, `ExplosionKit_Demo`.

**[⬆ Voltar ao topo](#table-of-contents)**


<a name="7"></a>
<a name="textures"></a>
## 7. Texturas

Esta seção se concentrará em assets de textura e suas propriedades.

### Seções

> 7.1 [Dimensões são poderes de 2](#textures-dimension)

> 7.2 [A densidade da textura deve ser uniforme](#textures-dimension)

> 7.3 [As texturas não devem ser maiores que 8192](#textures-max-size)

> 7.4 [Grupos de textura corretos](#textures-textures-group)

<a name="7.1"></a>
<a name="textures-dimensions"></a>
### 7.1 Dimensões são poderes de 2

Todas as texturas, exceto as texturas de IU, devem ter suas dimensões em múltiplos de potências de 2. As texturas não precisam ser quadradas.

Por exemplo, `128x512`,` 1024x1024`, `2048x1024`,` 1024x2048`, `1x512`.

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 A densidade da textura deve ser uniforme

Todas as texturas devem ter um tamanho apropriado para seu caso de uso padrão. A densidade de textura apropriada varia de projeto para projeto, mas todas as texturas dentro desse projeto devem ter uma densidade consistente.

Por exemplo, se a densidade da textura de um projeto é de 8 pixels por 1 unidade, uma textura que deve ser aplicada a um cubo de 100x100 unidades deve ser 1024x1024, pois é a potência mais próxima de 2 que corresponde à densidade da textura do projeto.

<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 As texturas não devem ser maiores que 8192

Nenhuma textura deve ter uma dimensão que exceda 8192 em tamanho, a menos que você tenha um motivo muito explícito para fazer isso. Freqüentemente, usar uma textura tão grande é simplesmente um desperdício de recursos.

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 As texturas devem ser agrupadas corretamente

Cada textura possui uma propriedade "Texture Group" usada para LOADing, e isso deve ser definido corretamente com base em seu uso. Por exemplo, todas as texturas da IU devem pertencer ao grupo de textura da IU.

**[⬆ Voltar ao topo](#table-of-contents)**


## Principais Contribuintes

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)

## Licença

Copyright (c) 2016 Gamemakin LLC

Veja [LICENSE](/LICENSE)

**[⬆ Voltar ao topo](#table-of-contents)**


## Emendas

Recomendamos que você crie um fork deste guia e altere as regras para se adequar ao Guia de Estilo de sua equipe. Abaixo, você pode listar algumas alterações ao Guia de Estilo. Isso permite que você atualize periodicamente seu guia de estilo sem ter que lidar com conflitos de mesclagem.

# };
