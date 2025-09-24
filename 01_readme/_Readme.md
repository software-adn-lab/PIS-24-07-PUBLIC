# Integrantes
Personas que conforman el equipo de investigación y que han contribuido directamente al desarrollo del estudio.
## Director
```dataview
list
from #Integrante 
where rol = "Director"
```
## Codirector
```dataview
list
from #Integrante 
where rol = "Codirector"
```
## Colaboradores
```dataview
list
from #Integrante 
where rol = "Colaborador"
```
## Asistentes de investigación
```dataview
list
from #Integrante 
where rol = "Asistente de investigación"
```
# Título del proyecto
Construcción de un artefacto para la detección de antipatrones en el ciclo de vida de desarrollo de software.
# Motivación
```dataviewjs
const page = dv.pages()
    .where(p => p.tipo === "motivación")
    .first();

    const content = await dv.io.load(page.file.path);
    const cleaned = content.replace(/^---[\s\S]*?---/, "").trim();
    dv.paragraph(`${cleaned}`);

```
# Objetivos
Se presentan las metas que guían la investigación, tanto generales como específicas.
## Objetivo general
```dataviewjs
const page = dv.pages()
    .where(p => p.tipo === "objetivo general")
    .first();

    const content = await dv.io.load(page.file.path);
    const cleaned = content.replace(/^---[\s\S]*?---/, "").trim();
    dv.paragraph(`[[${page.file.name}|${cleaned}]]`);

```
## Objetivos específicos

```dataviewjs
const pages = dv.pages()
    .where(p => p.tipo === "objetivo específico");
let i = 1;
for (let page of pages) {
    const content = await dv.io.load(page.file.path);
    const cleaned = content.replace(/^---[\s\S]*?---/, "").trim();

    dv.paragraph(`${i}. [[${page.file.name}|${cleaned}]]`);
    i++
}
```
