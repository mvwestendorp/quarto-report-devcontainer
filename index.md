---
title: "Workflow"
---

## Concepten

- Reproduceerbaarheid
	- Rapporten & analyses te reproduceren o.b.v. code + database
	- Identieke developer environments (nu voor R packages via renv, preferentieel over te gaan naar containers)
	- Versie controle voor bijhouden wijzigingen (potentieel voor gebruik collaboratie tools in Git ecosysteem)
- Tekst en code in 1 bestand
	- Visuele editor voor tekst aanpassingen (voor het betrekken domein experts) -> Rstudio / VS code
	- Code geintegreerd met tekst
- Veiligheid en performantie
	- Beperken verwerking van gevoelige gegevens op laptops

## Requirements

1. Versie controle: git repo
2. Data toegang: database connectie via bijv. ODBC (duckdb in voorbeeld)
3. R / Python environment: Python / R omgeving met (selectie van) packages

# Workflow

Twee voorname workflows:

1. Geparametriseerde audit rapporten o.b.v. tekst & code voor figuren/modellen/tabellen
2. Ad hoc analyses: statistische modellen, dashboards, ...

## Geparametriseerde rapporten

In samenwerking met domein experts die instaan voor de tekst.

Integratie van code in Quarto waardoor tabellen/figuren/modellen met de tekst integreren.

- Openen van project
	- heden: als project in IDE op lokale pc
	- doel: dev environment (cfr. devcontainer/codespaces/gitpod/...) lokaal dan wel on-premise of cloud
- Aanpassingen in tekst of code 
	- heden: visuele editor in Rstudio op lokale pc's
	- doel: visuele editor in VS Code of RStudio in dev environment
- Preview van wijzigingen
- Commit naar repo
	- heden: vooral voor bijhouden wijziging door data analist/scientist
	- doel: faciliteren van samenwerking tussen analisten (branches, PRs)
	- doel: CI pipeline voor uitvoeren tests en valide rapport generatie
- Delen van tussentijdse resultaten
	- heden: genereren op lokale pc en html bestanden delen via gedeelde schijf
	- doel: CD voor interne publicatie van rapporten (cfr. GitHub Pages)

### Genereren finale geparametriseerde rapporten

Creatie van jobs voor individuele rapporten (100 verschillende entiteiten evt. in 2 talen)

Heden: een R script die sequentieel rapporten genereert op lokale laptop

Doel: offloading via batch jobs naar cluster

## Intern rapport met dashboarding

Een analoge workflow bestaat vooral voor data science/statistiek werkzaamheden rond exploratory data analysis (EDA) en het ontwikkelen statistische modellen (voornamelijk clustering, regressie, mixed models en machine learning).

Hiervoor is het nuttig om dashboards te kunnen gebruiken met een back-end (bijv. Shiny, Dash, ...).
Voordeel vs. Power-BI is hergebruik van bestaande code, versie controle voor dashboard en cost-benefit van aanvullend leren van Power-BI.
