# Odoo Distribution ERP

> Projet de portfolio — ERP de distribution de produits optiques avec module d'approbation de marge personnalisé.

## Stack technique
- **Odoo 17.0 Community**
- **PostgreSQL 15**
- **Docker Compose**
- **Python 3** (module sale_margin_approval)

## Démarrage rapide

`ash
# 1. Cloner le dépôt
git clone https://github.com/othmanegamghal/Odoo-Distribution-ERP-Gestion-commerciale-et-validation-des-marges.git
cd Odoo-Distribution-ERP-Gestion-commerciale-et-validation-des-marges

# 2. Configurer les secrets
cp .env.example .env
# Remplacer les valeurs d'exemple et reporter les mêmes mots de passe dans config/odoo.conf

# 3. Démarrer les conteneurs
docker-compose up -d

# 4. Ouvrir Odoo
# http://localhost:8069
# Créer la base de données depuis l'interface
# Mot de passe maître : valeur admin_passwd définie dans config/odoo.conf
`

## Module custom : sale_margin_approval

Circuit d'approbation des devis dont la marge estimée est inférieure au seuil configuré.

### États d'un devis
| État | Signification |
|---|---|
| Non requise | Marge >= seuil |
| À demander | Marge < seuil |
| En attente | Demande soumise au responsable |
| Approuvée | Dérogation accordée |
| Refusée | Demande rejetée |

### Installation du module
`ash
docker exec odoo17_app odoo -d NOM_DB -i sale_margin_approval --stop-after-init
`

### Lancer les tests
`ash
docker exec odoo17_app odoo -d NOM_DB -i sale_margin_approval --test-enable --stop-after-init
`

## Structure du projet
`
odoo-distribution-erp/
├── docker-compose.yml
├── config/odoo.conf
├── addons/sale_margin_approval/
├── docs/
└── demo/
`

## Scénario de démonstration
Voir [docs/demo-scenario.md](docs/demo-scenario.md)
