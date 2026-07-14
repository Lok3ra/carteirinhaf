# Gestão Escolar

## Estrutura

- `index.html` — sistema principal
- `calendarios/calendario_2026.json` — calendário central oficial de 2026
- `modelos/` — modelos de importação Excel

## Atualização do calendário

Edite o calendário no sistema e use **Exportar calendário**. Depois substitua o arquivo `calendarios/calendario_2026.json` no GitHub.

O calendário central contém feriados, férias, recesso, dias substituídos, reposições, anteposições, períodos dos bimestres e regras usadas pelos módulos.

Para forçar os computadores a adotarem uma nova versão publicada, aumente o campo `versao` do JSON.
