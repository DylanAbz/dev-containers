# DevContainer - Stack MariaDB, Spring Boot & Angular

Ce projet fournit un environnement de développement prêt à l'emploi basé sur [DevContainers](https://containers.dev/) pour une stack complète comprenant :

- **Backend** : Java, Spring Boot, Maven
- **Frontend** : Angular, TypeScript, npm
- **Base de données** : MariaDB

## Prérequis

- [Docker](https://www.docker.com/)
- [Visual Studio Code](https://code.visualstudio.com/) ou [IntelliJ IDEA](https://www.jetbrains.com/idea/)
- Extension Dev Containers (VS Code) ou support natif dans IntelliJ IDEA

## Démarrage rapide

1. **Ouvre le projet dans ton IDE compatible DevContainer.**
2. **Lance l'ouverture dans le conteneur de développement.**
3. **Le backend et le frontend sont prêts à être développés.**

## Structure du projet

- `backend/` : Application Spring Boot (Java, Maven)
- `frontend/` : Application Angular (TypeScript, npm)
- `.devcontainer/` : Configuration DevContainer (Docker, Docker Compose)

## Services

- **dev** : Conteneur principal pour le développement (Java, Node, Angular CLI, etc.)
- **mariadb** : Base de données MariaDB persistante

## Ports exposés

- `4200` : Application Angular (frontend)
- `3307` : MariaDB (accès local si besoin)

## Commandes automatiques

À la création du conteneur :
- Installation des dépendances Angular (`npm install`)
- Build Maven du backend (`./mvnw clean install`)

## Accès à la base de données

- **Host** : `mariadb`
- **Port** : `3306` (interne au conteneur)
- **Utilisateur** : `user`
- **Mot de passe** : `pass`
- **Base** : `mydb`

## Extensions recommandées

- Java Pack
- Angular Essentials
- Prettier
- Spring Boot Tools

---

Développe, build et teste ta stack Spring/Angular/MariaDB sans configurer ton poste local !