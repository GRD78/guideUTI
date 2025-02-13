
# 🎨 Guide : Transférer les rôles FSMO via l’interface graphique (GUI)

Ce guide explique **comment répartir les rôles FSMO** entre plusieurs **contrôleurs de domaine (DC)** en utilisant **l’interface graphique de Windows Server**.

---

## 🏗️ Pré-requis
- Avoir **au moins 3 contrôleurs de domaine (DC)** installés et configurés.
- Être connecté avec un compte ayant les **droits d’administration** sur Active Directory.
- Connaître le **nom des serveurs** sur lesquels vous souhaitez déplacer les rôles FSMO.

---

## 📌 Les 5 rôles FSMO
Avant de commencer, voici un rappel des **5 rôles FSMO** :
1. **Schema Master**  
2. **Domain Naming Master**  
3. **PDC Emulator**  
4. **RID Master**  
5. **Infrastructure Master**  

L’objectif est de **répartir ces rôles** entre `SRV_BOR_AD2` et `SRV_BOR_AD3`.

---

## 🎯 Étape 1 : Ouvrir la console **Active Directory Users and Computers**
1. Sur un **contrôleur de domaine**, ouvrez la console **Active Directory Users and Computers** en lançant :
   - `dsa.msc` via **Exécuter (Windows + R)**.
   - Ou en passant par le menu **Outils d’administration**.

---

## 🔄 Étape 2 : Transférer les rôles **PDC, RID et Infrastructure**
1. **Clic droit** sur le **nom du domaine** (ex: `ecotechsolutions.lan`).
2. Sélectionnez **Operations Masters**.
3. Trois onglets vont apparaître :
   - **RID** → Cliquez sur **Change**, puis sélectionnez `SRV_BOR_AD2`.
   - **PDC** → Cliquez sur **Change**, puis sélectionnez `SRV_BOR_AD2`.
   - **Infrastructure** → Cliquez sur **Change**, puis sélectionnez `SRV_BOR_AD2`.
4. **Confirmez** chaque changement.

---

## 🌍 Étape 3 : Transférer le rôle **Domain Naming Master**
1. **Ouvrir la console Active Directory Domains and Trusts** :
   - Lancez **`dssite.msc`** via Exécuter.
   - Ou ouvrez-la via **Outils d’administration**.
2. **Clic droit** sur **Active Directory Domains and Trusts** (dans le panneau de gauche).
3. Sélectionnez **Operations Master**.
4. Cliquez sur **Change** et sélectionnez `SRV_BOR_AD3`.
5. **Validez** la modification.

---

## 📜 Étape 4 : Transférer le rôle **Schema Master**
⚠️ **Ce rôle nécessite d'activer la console Active Directory Schema**.

### ✅ Activer la console "Active Directory Schema"
1. **Ouvrir une invite de commande** en tant qu’administrateur.
2. Exécuter la commande suivante :
   ```cmd
   regsvr32 schmmgmt.dll























