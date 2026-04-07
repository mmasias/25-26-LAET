# BNF / EBNF

> El lenguaje para describir lenguajes

**1960 · John Backus & Peter Naur · Metalenguaje (gramática formal)**

## ¿Por qué?

En 1958, Backus necesitaba especificar la sintaxis de ALGOL 58 de forma precisa y no ambigua. El lenguaje natural es insuficiente para ese propósito: dos personas pueden interpretar la misma frase de modo distinto. BNF fue la primera notación formal para describir gramáticas libres de contexto, el mismo nivel que Chomsky había formalizado matemáticamente ese mismo año de forma independiente.

## ¿Qué?

Backus-Naur Form. Notación para gramáticas libres de contexto (Tipo 2 de Chomsky). Describe la sintaxis de lenguajes mediante reglas de producción. EBNF añade cuantificadores opcionales y repetición, eliminando la necesidad de recursión para expresar patrones simples.

## ¿Para qué?

Especificación formal de lenguajes de programación, protocolos y formatos. Documentación de parsers. Análisis de ambigüedad gramatical. En lingüística computacional, es la notación base para escribir gramáticas formales del lenguaje natural.

## ¿Cómo?

> Copiar / Pegar / Ver en [LivePreview - Railroad Diagram Generator](https://bottlecaps.de/rr/ui)

### Sintaxis

| Construcción | Significado |
|---|---|
| `<símbolo> ::= definición` | regla de producción |
| `A \| B` | alternativa |
| `{ A }` | cero o más (EBNF) |
| `[ A ]` | opcional (EBNF) |
| `"terminal"` | token literal |

### Ejemplo(s)

#### Gramática para oraciones simples en español

```bnf
oracion ::= sn sv
sn      ::= det n sadj?
sv      ::= v ( sn | sadj )?

sadj    ::= adv? adj

det     ::= "el" | "la" | "los" | "las" | "un" | "una"
n       ::= "gato" | "perro" | "lingüista" | "corpus"
v       ::= "duerme" | "analiza" | "construye"
adj     ::= "rápido" | "complejo" | "preciso"
adv     ::= "muy" | "bastante" | "poco"
```

#### Expresiones aritméticas

```bnf
expression ::= term ( ( '+' | '-' ) term )*
term       ::= factor ( ( '*' | '/' ) factor )*
factor     ::= number | '(' expression ')'
number     ::= digit+
digit      ::= '0' | '1' | '2' | '3' | '4' | '5' | '6' | '7' | '8' | '9'
```

> ***2Think:***
>
> Resulta interesante que la jerarquía `expression → term → factor` no es arbitraria: codifica precedencia de operadores sin decirlo explícitamente:
> 
> - `factor` es lo más profundo - números y paréntesis. Máxima prioridad.
> - `term` agrupa multiplicaciones y divisiones. Prioridad media.
> - `expression` agrupa sumas y restas. Mínima prioridad.
> 
> Cuando el parser procesa `3 + 4 * 2`, la estructura del árbol que genera esta gramática produce automáticamente `3 + (4 * 2)` y no `(3 + 4) * 2`. No porque haya una regla que diga "multiplicación antes que suma" - sino porque la jerarquía de producciones lo impone estructuralmente.
> 
> La precedencia no está declarada. Está esculpida en la forma de la gramática.

#### La U

##### Una asignatura

```bnf
nota_total          ::= evaluacion_continua examen_final

examen_final        ::= parte_teoria parte_practica
parte_teoria        ::= pregunta_desarrollo+ | pregunta_test+
parte_practica      ::= ejercicio_codigo | ejercicio_papel

evaluacion_continua ::= evaluacion+
evaluacion          ::= prueba_parcial | entrega | proyecto
prueba_parcial      ::= pregunta_desarrollo+ | pregunta_test+
entrega             ::= entrega_individual | entrega_grupal
proyecto            ::= memoria anexo*

pregunta_desarrollo ::= "desarrollo" | "ensayo" | "caso_practico"
pregunta_test       ::= "verdadero_falso" | "opcion_multiple" | "emparejamiento"
ejercicio_codigo    ::= "depuracion" | "implementacion" | "analisis"
ejercicio_papel     ::= "traza" | "diagrama" | "pseudocodigo"
memoria             ::= "introduccion" "desarrollo" "conclusiones"
anexo               ::= "codigo_fuente" | "diagramas" | "referencias"
```

##### La carrera

```bnf
expediente          ::= curso_academico+

curso_academico     ::= cuatrimestre cuatrimestre
cuatrimestre        ::= matricula calificaciones

matricula           ::= asignatura+
asignatura          ::= asignatura_obligatoria | asignatura_optativa | tfg

calificaciones      ::= calificacion_asignatura+
calificacion_asignatura ::= convocatoria+

convocatoria        ::= aprobada | suspendida | no_presentado
aprobada            ::= "aprobado" | "notable" | "sobresaliente" | "matricula_honor"
suspendida          ::= "suspenso"
no_presentado       ::= "no_presentado"

asignatura_obligatoria ::= creditos_asignatura
asignatura_optativa    ::= creditos_asignatura
tfg                    ::= creditos_tfg tribunal

creditos_asignatura ::= "3ECTS" | "6ECTS" | "9ECTS"
creditos_tfg        ::= "12ECTS" | "15ECTS"
tribunal            ::= vocal vocal vocal presidente
```

#### Mario Bros

```bnf
juego               ::= partida+

partida             ::= mundo+
mundo               ::= nivel+ castillo
nivel               ::= segmento+ meta
castillo            ::= segmento+ jefe

segmento            ::= terreno enemigo* objeto* trampa*

terreno             ::= plataforma+ fondo
plataforma          ::= plataforma_fija | plataforma_movil | plataforma_destructible
plataforma_movil    ::= plataforma_horizontal | plataforma_vertical
plataforma_destructible ::= bloque_ladrillo | bloque_interrogacion

enemigo             ::= enemigo_terrestre | enemigo_aereo | enemigo_acuatico
enemigo_terrestre   ::= "goomba" | "koopa" | "planta_pirana"
enemigo_aereo       ::= "lakitu" | "para_koopa"
enemigo_acuatico    ::= "cheep_cheep" | "bloper"

objeto              ::= objeto_coleccionable | objeto_potenciador
objeto_coleccionable ::= "moneda" | "estrella_roja"
objeto_potenciador  ::= "super_seta" | "flor_fuego" | "estrella_invencible"

trampa              ::= "pozo" | "lava" | "bala_bill" | "pinchos"

jefe                ::= jefe_menor jefe_menor? bowser?
jefe_menor          ::= "bowser_falso"
bowser              ::= fase_puente fase_lava fase_final

fase_puente         ::= segmento hacha
fase_lava           ::= segmento bola_fuego+
fase_final          ::= segmento bola_fuego+ martillo+

meta                ::= asta_bandera | portal
estado_jugador      ::= "pequeno" | "super" | "fuego" | "invencible"

hacha               ::= "hacha"
bola_fuego          ::= "bola_fuego"
martillo            ::= "martillo"
fondo               ::= "exterior" | "subterraneo" | "acuatico" | "castillo"
```

#### Ultima VI

```bnf
ultima_vi           ::= britannia partida

britannia           ::= region+
region              ::= ciudad* dungeon* santuario* campo

ciudad              ::= edificio+ npc+ tienda*
edificio            ::= edificio_publico | edificio_privado | castillo
castillo            ::= "lord_british" guardia+ sala+

dungeon             ::= nivel+ jefe
nivel               ::= sala+ trampa* enemigo*
sala                ::= sala_normal | sala_trampa | sala_tesoro

santuario           ::= virtud altar
virtud              ::= "honestidad" | "compasion" | "valor" | "justicia"
                      | "sacrificio" | "honor" | "espiritualidad" | "humildad"

partida             ::= avatar inventario mision

avatar              ::= clase estadisticas reputacion
clase               ::= "paladin" | "bard" | "fighter" | "druid"
                      | "tinker" | "ranger" | "shepherd" | "mage"
estadisticas        ::= fuerza destreza inteligencia puntos_vida puntos_mana
reputacion          ::= virtud_nivel+
virtud_nivel        ::= virtud ( "0" | "1" | "2" | "3" )

mision              ::= acto+
acto                ::= acto_uno | acto_dos | acto_tres
acto_uno            ::= investigacion+ entrada_gargoyle
acto_dos            ::= artefacto+ alianza_gargoyle
acto_tres           ::= codex ritual_final
investigacion       ::= conversacion* viaje*
entrada_gargoyle    ::= dungeon_britannia combate
alianza_gargoyle    ::= diccionario_gargish conversacion_vela
ritual_final        ::= tres_partes_codex altar_codex

inventario          ::= item*
item                ::= arma | armadura | consumible | artefacto | llave
arma                ::= arma_cuerpo_cuerpo | arma_distancia
arma_cuerpo_cuerpo  ::= "espada" | "hacha" | "maza" | "daga"
arma_distancia      ::= "arco" | "ballesta" | "honda"
armadura            ::= "cuero" | "cota_malla" | "escama" | "placa" | "mitica"
consumible          ::= "comida" | "torcha" | "reagente"+ | "pocion"
artefacto           ::= "ankh" | "gema_codex" | "vela_amor" | "libro_verdad" | "campana_coraje"
llave               ::= "llave_maestra" | "llave_magia"

conversacion        ::= saludo keyword+ despedida
keyword             ::= respuesta_simple | respuesta_con_quest
respuesta_con_quest ::= keyword condicion_quest respuesta_simple
condicion_quest     ::= artefacto_requerido | virtud_requerida
saludo              ::= "id_npc"
despedida           ::= "bye" | "adios"

npc                 ::= nombre horario dialogo
horario             ::= actividad+
actividad           ::= ( "dormir" | "trabajar" | "vagar" | "comer" ) franja_horaria
franja_horaria      ::= "manana" | "tarde" | "noche"
dialogo             ::= conversacion

combate             ::= turno+
turno               ::= accion_avatar accion_enemigo*
accion_avatar       ::= atacar | huir | lanzar_hechizo | usar_item
accion_enemigo      ::= atacar | lanzar_hechizo | huir
atacar              ::= "ataque_fisico"
huir                ::= "huida"
lanzar_hechizo      ::= reagente+ hechizo
hechizo             ::= "in_lor" | "vas_flam" | "an_nox" | "rel_hur"

tres_partes_codex   ::= libro_verdad campana_coraje vela_amor
```

#### Zelda

##### Clásico

```bnf
zelda               ::= hyrule partida

hyrule              ::= region+
region              ::= campo dungeon* pueblo* secreto*
campo               ::= zona+ conexion*
zona                ::= "pradera" | "bosque" | "montaña" | "desierto" | "lago" | "pantano"
conexion            ::= portal | puente | cueva_paso
secreto             ::= arbusto_quemable | roca_movible | pared_falsa

pueblo              ::= npc+ tienda* hada?
hada                ::= fuente_hada | gran_hada
tienda              ::= tienda_objetos | tienda_escudo | tienda_flechas

dungeon             ::= sala+ sala_jefe llave_grande tesoro_corazon
sala                ::= sala_normal | sala_cerrada | sala_puzzle | sala_minijefe
sala_cerrada        ::= llave_pequeña sala_normal
sala_puzzle         ::= mecanismo+ recompensa
mecanismo           ::= "palanca" | "bloque" | "cristal" | "antorcha" | "estatua"
sala_minijefe       ::= minijefe recompensa
sala_jefe           ::= jefe objeto_dungeon

partida             ::= link inventario mision_principal

link                ::= corazones objetos_activos
corazones           ::= contenedor_corazon+
contenedor_corazon  ::= corazon_completo | cuarto_corazon
cuarto_corazon      ::= fragmento_corazon fragmento_corazon fragmento_corazon fragmento_corazon

inventario          ::= espada escudo objeto_dungeon* objeto_secundario*
espada              ::= "espada_kokiris" | "espada_maestra" | "espada_biggoron"
escudo              ::= "escudo_deku" | "escudo_hyliano" | "escudo_espejo"
objeto_dungeon      ::= "boomerang" | "hookshot" | "bomba" | "arco" | "guantes" | "lente_verdad"
objeto_secundario   ::= "ocarina" | "saco_bombas" | "carcaj" | "botella"

mision_principal    ::= acto+
acto                ::= acto_infancia | acto_adultez
acto_infancia       ::= dungeon dungeon dungeon despertar
acto_adultez        ::= dungeon dungeon dungeon dungeon despertar_final
despertar           ::= cutscene revelacion
despertar_final     ::= sage+ enfrentamiento_final
sage                ::= dungeon revelacion_sage
enfrentamiento_final ::= fase_ganon+ derrota_ganon rescate_zelda

fase_ganon          ::= objeto_dungeon_requerido combate
combate             ::= turno+
turno               ::= ataque_link | ataque_ganon | esquiva
ataque_link         ::= espada objeto_secundario?
ataque_ganon        ::= "bola_fuego" | "torbellino" | "golpe_directo"

revelacion_sage     ::= cutscene sage
cutscene            ::= dialogo+ cinemática?
```

##### Breath of wild

BotW rompe deliberadamente la gramática de Zelda.

```bnf
botw                ::= hyrule partida

hyrule              ::= region+ torre+ santuario+ korok*
region              ::= "meseta_inicial" | "akkala" | "eldin" | "lanayru"
                      | "necluda" | "faron" | "meseta_central" | "gerudo"
                      | "tabanta" | "hebra" | "bosque_kokiris"
torre               ::= region_descubierta
region_descubierta  ::= santuario* punto_interes* secreto*
santuario           ::= puzzle_santuario recompensa_santuario
puzzle_santuario    ::= combate_santuario | puzzle_fisico | puzzle_runa
recompensa_santuario ::= esfera_espiritu+
punto_interes       ::= establo | pueblo | ruina | bestia_divina?
bestia_divina       ::= region_especifica puzzle_bestia jefe_bestia
puzzle_bestia       ::= mecanismo_rotacion+ terminal+ terminal_central
jefe_bestia         ::= ganon_fragmento

partida             ::= link inventario mision?

link                ::= corazones resistencia equipo
corazones           ::= contenedor_corazon+
resistencia         ::= contenedor_resistencia+
contenedor_corazon  ::= esfera_espiritu esfera_espiritu esfera_espiritu esfera_espiritu
contenedor_resistencia ::= esfera_espiritu esfera_espiritu esfera_espiritu esfera_espiritu

equipo              ::= arma* arco? escudo?
arma                ::= arma_con_durabilidad
arma_con_durabilidad ::= ( "espada" | "hacha" | "lanza" | "claymore" | "palo" ) durabilidad
durabilidad         ::= "entera" | "dañada" | "a_punto_de_romperse"

inventario          ::= runa+ material* comida* equipo
runa                ::= "magnetismo" | "cryo" | "bomba" | "stasis" | "camera"
material            ::= material_cocina | material_crafting
comida              ::= plato efectos_comida?
efectos_comida      ::= "vida" | "resistencia" | "velocidad" | "sigilo" | "fuerza"

mision              ::= mision_principal? mision_secundaria* santuario*
mision_principal    ::= prologo bestia_divina* castillo_hyrule ganon
prologo             ::= meseta_inicial cuatro_runas
cuatro_runas        ::= santuario santuario santuario santuario
bestia_divina       ::= liberacion_bestia
ganon               ::= ganon_sin_preparacion | ganon_con_preparacion
ganon_sin_preparacion ::= enfrentamiento_directo
ganon_con_preparacion ::= bestia_divina+ enfrentamiento_directo
enfrentamiento_directo ::= fase_ganon_bestia fase_calamidad
```

El problema estructural que explota al formalizarlo:

`mision ::= mision_principal?` - el signo de interrogación lo dice todo. **La misión principal es opcional.** Se puede ir directamente a Ganon desde el minuto cinco. Ningún Zelda anterior permitía eso y ninguna gramática anterior lo hubiera escrito así.

Las diferencias estructurales respecto a Zelda clásico:

- `equipo ::= arma*` con asterisco - las armas son consumibles, no items permanentes. En Zelda clásico `espada` era un terminal fijo. Aquí es `arma_con_durabilidad` con estado.
- `bestia_divina*` en la misión principal - cero o más. Puedes derrotar a Ganon habiendo liberado ninguna, una, o las cuatro. La gramática no impone orden ni cantidad.
- `korok*` en hyrule - novecientos coleccionables opcionales diseminados. La gramática los modela como ruido de fondo del mundo, no como estructura.
- `santuario` aparece en tres niveles distintos: en `hyrule`, en `mision` y como fuente de `esfera_espiritu`. Es el átomo estructural del juego - reemplaza al dungeon clásico.

La conclusión que emerge: BotW no tiene gramática de juego. Tiene gramática de **mundo**. La diferencia es que en Zelda clásico el mundo existe para servir a la misión. En BotW la misión existe opcionalmente dentro del mundo.

Nintendo cambió la relación de dependencia. La gramática lo hace obvio en una línea.

#### 2Think

**Tesis:** Zelda breath of the wild es Ultima IV

La gramática lo confirma sin ambigüedad.

Ultima I (1981): `mundo ::= mision`. El mundo es un contenedor de la misión.

Ultima IV (1985): `partida ::= mundo mision?`. La misión emerge del mundo, no al revés. Nadie dice "ve a hacer esto". Se descubre que existe algo por recorrer y actuar en el mundo. La virtud no se impone, se encuentra.

Ultima VI (1990): `partida ::= mundo comprension`. Ni siquiera hay misión en el sentido clásico. Lo que hay es una pregunta mal planteada que el jugador tiene que reformular solo. El "enemigo" no se derrota, se comprende.

BotW (2017) llega 32 años después y la prensa lo llama revolución del mundo abierto. Garriott lo había escrito mucho antes.

La diferencia es que Garriott lo hizo con intención filosófica explícita: el sistema de virtudes, la empatía con las gárgolas, el Codex como objeto de conocimiento y no de poder. Nintendo lo hizo como diseño de juego. El resultado estructural es el mismo; la gramática subyacente, idéntica. La motivación, completamente distinta.

---

*Ver también: [Expresiones Regulares](regex.md) · [XML](xml.md) - las DTD usan notación derivada de BNF*

```bnf
regex         ::= alternacion
alternacion   ::= concatenacion ( '|' concatenacion )*
concatenacion ::= cuantificado*
cuantificado  ::= atomo cuantificador?
cuantificador ::= '*' | '+' | '?' | '{' numero '}'
atomo         ::= caracter | '.' | '(' regex ')' | '[' clase ']'
clase         ::= '^'? item+
item          ::= caracter | caracter '-' caracter
```
