
**Titre** : {{title}}
**Date :** 20/08/2024
**Auteur/Source :** [Article](https://datascientest.com/pl-sql-tout-comprendre)
**Sujet :** PL/SQL
**Type de Note :** #type #Lecture
**MOC :** 
**Mots-clés :** #Article
**En lien** :
***
## Contexte et Résumé
Dans le domaine des bases de données relationnelles, [Oracle](https://datascientest.com/qui-est-oracle-principal-challenger-dazure-aws-et-google-cloud) se distingue non seulement par la robustesse de ses systèmes de gestion, mais également par les outils avancés qu'il offre aux développeurs pour optimiser, automatiser et sécuriser les opérations sur les données. Au sein de ces outils se trouve PL/SQL (Procedural Language/Structured Query Language), un langage de programmation puissant conçu pour s'intégrer avec SQL, le langage de requête standard pour les bases de données relationnelles.

PL/SQL étend les capacités de [SQL](https://datascientest.com/sql-tout-savoir) en y ajoutant des fonctionnalités procédurales telles que les boucles, les conditions et les exceptions, permettant ainsi aux développeurs de créer des scripts pour la gestion des bases de données. 

Ce langage, essentiel pour tout développeur travaillant avec Oracle, a pour objectif de **combiner les commandes de gestion de base de données avec un langage de programmation procédural**. Il fournit des solutions de programmation plus complètes pour la création d’applications critiques fonctionnant sur la base de données Oracle.

---

## Point Clé
### Concept Clé : Les raisons d’apprendre PL/SQL
PL/SQL est un langage de programmation essentiel pour les développeurs utilisant des bases de données. Il présente de nombreux avantages : 

- **Intégration avec Oracle Database :** PL/SQL est conçu pour fonctionner de manière optimale avec [Oracle Database](https://datascientest.com/oracle-database-tout-savoir), permettant une interaction fluide et efficace avec les données stockées.
- **Intégration avec SQL :** PL/SQL est une extension du langage SQL qui permet d’écrire des requêtes SQL complexes, gérer des transactions et manipuler les données directement dans le même environnement de programmation.
- **Facilité d’utilisation :** Si vous êtes déjà familier avec SQL, vous trouverez la syntaxe de PL/SQL assez intuitive. La transition de SQL à PL/SQL est naturelle pour ceux qui ont une expérience en SQL, ce qui facilite l’apprentissage de ce langage.
- **Sécurité renforcée :** PL/SQL comprend des fonctionnalités de sécurité robustes, contrôlant ainsi l’accès aux données. Vous pouvez protéger les données sensibles en limitant l’accès direct aux tables et en créant des couches supplémentaires de sécurité.
- **Automatisation de tâches répétitives :** PL/SQL comprend des fonctionnalités (procédures, fonctions, déclencheurs) permettant d’automatiser les processus de gestion des bases de données. Cela réduit le besoin d’exécution manuelle des tâches répétitives et minimise les erreurs humaines.
- **Portabilité :** Les blocs de code PL/SQL peuvent être déplacés entre différentes bases de données Oracle sans modification.
### Concept Clé : Les différentes applications de PL/SQL

PL/SQL offre une multitude d’applications dans la gestion des bases de données. Grâce à sa flexibilité et sa puissance, il est utilisé pour divers cas d’usage tels que : 

- **Développement d’applications :** PL/SQL est utilisé pour le développement d’applications web basées sur des bases de données Oracle. 
- **Automatisation des tâches administratives :** PL/SQL permet l’automatisation des tâches courantes d’administration de bases de données, améliorant ainsi l’efficacité et la fiabilité des processus.
- **Sécurité de la base de données :** PL/SQL permet de protéger l’intégrité de la base de données.
- **Analyse et reporting :** PL/SQL est utilisé pour générer des rapports personnalisés qui répondent à des besoins spécifiques en matière de gestion de données. PL/SQL permet également de générer des données pour les tableaux de bord et les outils de visualisation.
### Concept Clé : Les bases de la syntaxe de PL/SQL

Un programme PL/SQL est structuré en blocs. Chaque bloc peut contenir trois sections principales :

- **Section déclarative (**DECLARE**) :** Cette section est utilisée pour déclarer des variables, des constantes, des curseurs et d’autres objets PL/SQL. Elle est optionnelle.
- **Section exécutable (**BEGIN**) :** Cette section contient les instructions qui seront exécutées. Elle est obligatoire.
- **Section d’exception (**EXCEPTION**) :** Cette section est utilisée pour gérer les erreurs qui peuvent survenir lors de l’exécution des instructions dans la section BEGIN. Elle est optionnelle.
---


## Détail Important
### Détail : La structures du code

#### 1. Variables et types de données :

Les variables en PL/SQL doivent être déclarées dans la section DECLARE. Les types de données utilisés pour les variables sont similaires à ceux de SQL, avec des extensions spécifiques à PL/SQL.

VARCHAR2 : Utilisé pour les chaînes de caractères.
NUMBER : Utilisé pour les nombres.
DATE : Utilisé pour les dates et heures.
```
Exemple : 
DECLARE
   v_employee_name VARCHAR2(50);
   v_salary NUMBER(10, 2);
   v_hire_date DATE;
BEGIN
   v_employee_name := ‘Jane Doe’; 
   v_salary := 60000; 
   v_hire_date := SYSDATE; 
   DBMS_OUTPUT.PUT_LINE(‘Employee: ‘ || v_employee_name || ‘hired on: ‘ || v_hire_date);
END;
```

#### 2. Structures conditionnelles :

Les structures conditionnelles permettent de tester des conditions et d’exécuter des blocs de code en fonction des résultats de ces tests.

La structure conditionnelle IF-THEN-ELSE permet d’exécuter des instructions si une condition est vraie, et éventuellement d’autres instructions si elle est fausse.
```
Exemple : 
BEGIN
   IF v_salary > 50000 THEN
      DBMS_OUTPUT.PUT_LINE(‘High salary’);
   ELSIF v_salary > 30000 THEN
      DBMS_OUTPUT.PUT_LINE(‘Medium salary’);
   ELSE
      DBMS_OUTPUT.PUT_LINE(‘Low salary’);
   END IF;
END;
```

#### 3. Boucles :

PL/SQL prend en charge plusieurs types de boucles, permettant d’exécuter des instructions de manière répétée.
FOR loop : Exécute un bloc d’instructions un nombre défini de fois.
```
Exemple : 
BEGIN
   FOR i IN 1..10 LOOP
      DBMS_OUTPUT.PUT_LINE(‘Iteration: ‘ || i);
   END LOOP;
END;
```

WHILE loop : Exécute un bloc d’instructions tant qu’une condition est vraie.
```
Exemple : 
DECLARE
   v_counter NUMBER := 1;
BEGIN
   WHILE v_counter <= 10 LOOP
      DBMS_OUTPUT.PUT_LINE(‘Counter: ‘ || v_counter);
      v_counter := v_counter + 1;
   END LOOP;
END;
```


LOOP : Exécute un bloc d’instructions indéfiniment jusqu’à ce qu’une condition de sortie soit atteinte.
```
Exemple : 
DECLARE
   v_counter NUMBER := 1;
BEGIN
   LOOP
      EXIT WHEN v_counter > 10;
      DBMS_OUTPUT.PUT_LINE(‘Counter: ‘ || v_counter);
      v_counter := v_counter + 1;
   END LOOP;
END;
```

#### 4. Procédures :

Les procédures stockées sont des sous-programmes PL/SQL qui peuvent être réutilisés pour exécuter des tâches spécifiques. 
Voici un exemple de procédure pour augmenter le salaire des employés en fonction de leur performance :
```
CREATE OR REPLACE PROCEDURE adjust_salary (emp_id NUMBER, increment NUMBER) AS  
BEGIN  
  UPDATE employees  
  SET salary = salary + increment  
  WHERE employee_id = emp_id;  
  COMMIT;
END;  
```

Cette procédure prend en entrée un identifiant d’employé et un montant d’augmentation, puis met à jour le salaire de l’employé correspondant.

Pour appeler cette procédure, il suffit de faire : 
```
BEGIN
   adjust_salary(1001, 5000);
END;
```


#### 5. Fonctions :

Les fonctions sont des sous-programmes PL/SQL qui peuvent renvoyer une valeur unique. 
Voici un exemple de fonction qui calcule la moyenne des salaires des employés :
```
CREATE OR REPLACE FUNCTION calculate_average_salary RETURN NUMBER AS  
  avg_salary NUMBER;
BEGIN  
  SELECT AVG(salary) INTO avg_salary FROM employees;  
  RETURN avg_salary;
END;  
```

Cette fonction calcule la moyenne des salaires des employés et renvoie le résultat.

#### 6. Gestion des exceptions :

La gestion des exceptions est une partie essentielle de PL/SQL, permettant de gérer les erreurs de manière élégante et d’assurer la stabilité de l’application.

Les exceptions sont gérées dans la section EXCEPTION d’un bloc PL/SQL. Il existe des exceptions prédéfinies comme NO_DATA_FOUND et TOO_MANY_ROWS, ainsi que la possibilité de définir des exceptions personnalisées.
```
Exemple : 

BEGIN
   SELECT name INTO v_employee_name FROM employees WHERE employee_id = 9999;
EXCEPTION
   WHEN NO_DATA_FOUND THEN
      DBMS_OUTPUT.PUT_LINE(‘No data found for the specified employee ID.’);
   WHEN TOO_MANY_ROWS THEN
      DBMS_OUTPUT.PUT_LINE(‘Multiple rows found for the specified employee ID.’);
   WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE(‘An unexpected error occurred: ‘ || SQLERRM);
END;
```

#### 7. Triggers :

Les triggers sont des blocs PL/SQL qui s’exécutent automatiquement en réponse à des événements spécifiques sur une table, comme l’insertion, la mise à jour ou la suppression de lignes. 

Voici un exemple de trigger qui enregistre l’historique des modifications sur une table critique :
```
CREATE OR REPLACE TRIGGER audit_trigger  
AFTER INSERT OR UPDATE OR DELETE ON employees  
FOR EACH ROW  
BEGIN  
  IF INSERTING THEN  
      INSERT INTO audit_log (action, employee_id, action_time)  
      VALUES (‘INSERT’, :NEW.employee_id, SYSDATE);  
  ELSIF UPDATING THEN  
      INSERT INTO audit_log (action, employee_id, action_time)  
      VALUES (‘UPDATE’, :NEW.employee_id, SYSDATE);  
  ELSIF DELETING THEN  
      INSERT INTO audit_log (action, employee_id, action_time)  
      VALUES (‘DELETE’, :OLD.employee_id, SYSDATE);  
  END IF;  
END;
```
Ce trigger permet de suivre toutes les modifications effectuées sur la table `employees` en enregistrant les actions dans une **table `audit_log`**.

## Conclusion

PL/SQL est un langage puissant qui permet d’**étendre les capacités de SQL** avec des fonctionnalités procédurales. Il offre des avantages significatifs en termes de performance, de gestion des erreurs, de sécurité et de portabilité. Grâce à ses structures de contrôle, ses procédures stockées, ses fonctions et ses triggers, **PL/SQL facilite la création d’applications robustes et performantes**. En comprenant et en appliquant ces concepts, les développeurs peuvent tirer pleinement parti des fonctionnalités offertes par Oracle Database pour développer des solutions efficaces et fiables.







