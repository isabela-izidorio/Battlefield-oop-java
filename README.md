# Turn-Based Combat Simulator | Simulador de Combate por Turnos

A Java-based turn-based combat simulator focused on practical Object-Oriented Programming (OOP): Inheritance, Polymorphism, Interfaces, and Encapsulation.

Simulador de combate por turnos desenvolvido em Java, com foco na aplicação prática de POO: Herança, Polimorfismo, Interfaces e Encapsulamento.

> Study project | Projeto de estudo

## Business Rules | Regras de Negócio

### Character Core | Núcleo de Personagem

- **Resources | Recursos:** All characters start with 100 HP and 100 Energy.
- **Data Integrity | Integridade:** HP and Energy cannot have negative values.
- **Damage | Dano:** Defending characters receive 50% less damage. Defense resets after being attacked.

### Fighters | Lutadores

#### Witch | Bruxa

- **Element | Elemento:** Can operate with one of five elements: Fire, Water, Earth, Air, or Aether.
- **Defense | Defesa:** Can spend energy to defend any other character.
- **Soul Drain | Dreno de Alma:** Special ability deals damage and restores her own HP.

#### Demon | Demônio

- **Evil Level | Nível de Maldade:** Damage scales with Evil Level, from 1 to 10.
- **Rage | Fúria:** Gains +10 damage when HP falls below 30.
- **Sacrifice | Sacrifício:** Special ability deals massive damage at the cost of the Demon's own HP.

#### Passive Characters | Personagens Passivos

**Villager | Aldeão:** Has no combat abilities and does not implement the `Lutador` interface. Interactions are limited to dialogues and specific professions, such as Blacksmith and Carpenter.

## Class Diagram | Diagrama de Classes

```
                    +-----------------------+
                    |     <<Abstract>>      |
                    |      Personagem       |
                    +-----------------------+
                    | - nome: String        |
                    | - vida: int           |
                    | - energia: int        |
                    | - estaDefendendo: bln |
                    +-----------------------+
                    | + receberDano()       |
                    | + gastarEnergia()     |
                    +-----------+-----------+
                                |
        ________________________|________________________
       |                        |                        |
 (Inheritance)             (Inheritance)            (Inheritance)
       |                        |                        |
+--------------------+   +--------------------+   +-----------------+
|        Aldeao      |   |        Bruxa       |   |     Demonio     |
+--------------------+   +--------------------+   +-----------------+
| - profissao: String|   | - elemento: String |   | - maldade: int  |
+--------------------+   +--------------------+   +-----------------+
| + interagir()      |   | +defenderTerceiro()|   |                 |
+--------------------+   +-----+--------------+   +-----+-----------+
                               |                        |
                               |      (Implements)      |
                               \___________  ___________/
                                           |
                                           v
                                +-----------------------+
                                |     <<Interface>>     |
                                |        Lutador        |
                                +-----------------------+
                                | + atacar(alvo)        |
                                | + usarEspecial(alvo)  |
                                | + defender()          |
                                +-----------------------+
```

## OOP Concepts | Conceitos de POO

- **Inheritance | Herança** — Specialized characters inherit from `Personagem`.
- **Polymorphism | Polimorfismo** — Different characters implement behaviors in their own way.
- **Interfaces | Interfaces** — Combat abilities are defined by the `Lutador` interface.
- **Encapsulation | Encapsulamento** — Character attributes and resource management are controlled by the base class.
