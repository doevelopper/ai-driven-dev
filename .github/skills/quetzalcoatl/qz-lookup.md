# Skill: qz-lookup — Naming Convention Lookup

**Agent:** Quetzalcoatl
**Phase:** 2 — Name
**Skill ID:** `qz-lookup`

---

## Purpose

Identify the correct persona universe and fallback chain for the given SAFe role by reading `Naming-convention.md`.

---

## Inputs

| Input | Source |
|---|---|
| Discovery Summary from `qz-discover` | Previous skill output |
| `Naming-convention.md` | Repository file |

---

## Lookup Table (from Naming-convention.md)

| SAFe Level | Role | Primary Universe | Fallback 1 | Fallback 2 |
|---|---|---|---|---|
| Portfolio | Business Owner | Olympus Gods | Egyptian Gods | Roman Gods |
| Portfolio | Enterprise Architect | Olympus Gods | Egyptian Gods | Roman Gods |
| Portfolio | Epic Owner | Olympus Gods | Egyptian Gods | Roman Gods |
| Portfolio | LPM Facilitator | Olympus Gods | Egyptian Gods | Roman Gods |
| Solution Train | STE | James Bond | Mission Impossible | Jason Bourne |
| Solution Train | Solution Manager | James Bond | Mission Impossible | Jason Bourne |
| Solution Train | Solution Architect | James Bond | Mission Impossible | Jason Bourne |
| ART | Release Train Engineer | Lord of the Rings | The Hobbit | Game of Thrones |
| ART | Product Manager | Lord of the Rings | The Hobbit | Game of Thrones |
| ART | System Architect | Lord of the Rings | The Hobbit | Game of Thrones |
| Team | Product Owner | Harry Potter | Fantastic Beasts | Chronicles of Narnia |
| Team | Scrum Master | Marvel Universe | DC Universe | Image Comics |
| Team | Developer / Tech Lead | Team Theme Comics | SM's Comic Universe | Sci-Fi |
| Team | DevOps / Platform | Team Theme Comics | SM's Comic Universe | Sci-Fi |

---

## Universe Persona Examples

### Olympus Gods
Zeus, Hera, Poseidon, Demeter, Athena, Apollo, Artemis, Hephaestus, Aphrodite, Hermes, Dionysus, Hestia, Ares, Persephone, Hecate, Nike, Iris, Morpheus, Nemesis, Tyche

### Egyptian Gods
Ra, Osiris, Isis, Horus, Anubis, Thoth, Set, Bastet, Sekhmet, Hathor, Nut, Geb, Sobek, Ptah, Khepri, Tefnut, Shu, Neith, Khnum, Wadjet

### Roman Gods
Jupiter, Juno, Neptune, Pluto, Minerva, Venus, Mars, Mercury, Diana, Vulcan, Bacchus, Ceres, Fortuna, Janus, Saturn, Vesta, Bellona, Flora, Faunus, Quirinus

### James Bond Characters
M, Moneypenny, Q, Felix Leiter, Nomi, Alec Trevelyan, Vesper Lynd, Judi Dench M, Wai Lin, Christmas Jones, Elektra King, Jinx, Miranda Frost

### Mission Impossible Characters
Ethan Hunt, Luther Stickell, Benji Dunn, Ilsa Faust, Alanna Mitsopolis, Eugene Kittridge, Erika Sloane

### Jason Bourne Characters
Jason Bourne, Marie Kreutz, Nicky Parsons, Pamela Landy, Aaron Cross, Heather Lee

### Lord of the Rings
Gandalf, Frodo, Aragorn, Legolas, Gimli, Boromir, Faramir, Galadriel, Elrond, Saruman, Théoden, Éowyn, Samwise, Merry, Pippin, Treebeard, Glorfindel

### The Hobbit
Bilbo, Thorin, Balin, Dwalin, Fíli, Kíli, Dori, Nori, Ori, Óin, Glóin, Bifur, Bofur, Bombur, Bard, Tauriel, Thranduil, Beorn

### Game of Thrones
Jon Snow, Daenerys, Tyrion, Arya, Sansa, Cersei (reserved – villain rule), Brienne, Jaime, Davos, Varys, Littlefinger (reserved), Jorah, Missandei, Grey Worm, Samwell, Ygritte

### Harry Potter
Harry, Hermione, Ron, Dumbledore, Snape, McGonagall, Neville, Luna, Ginny, Fred, George, Lupin, Tonks, Moody, Sirius, Dobby, Fleur, Cedric, Cho

### Fantastic Beasts
Newt, Tina, Queenie, Jacob, Credence, Theseus, Albus, Grindelwald (reserved – villain rule)

### Marvel Universe
Iron Man, Spider-Man, Black Widow, Captain America, Thor, Hulk, Hawkeye, Scarlet Witch, Vision, Ant-Man, Wasp, Falcon, War Machine, Black Panther, Captain Marvel, Wolverine, Storm, Cyclops, Beast, Gambit, Rogue, Deadpool

### DC Universe
Batman, Superman, Wonder Woman, Flash, Green Lantern, Aquaman, Cyborg, Green Arrow, Black Canary, Nightwing, Oracle, Batgirl, Zatanna, Martian Manhunter

---

## Output

```markdown
## Naming Lookup Result

- **Role:** [role]
- **Primary Universe:** [universe] → [list of 5 candidate names]
- **Fallback 1:** [universe] → [list of 5 candidate names]
- **Fallback 2:** [universe] → [list of 5 candidate names]
- **Ready for registry check:** ✅
```
