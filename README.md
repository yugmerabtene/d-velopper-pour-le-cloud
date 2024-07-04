### Sommaire

1. **Introduction au Cloud Computing et AWS**
    - Qu'est-ce que le Cloud Computing ?
    - Introduction à AWS
    - Historique et évolution d'AWS
    - Avantages d'utiliser AWS

2. **Premiers Pas avec AWS**
    - Création d'un compte AWS
    - Présentation de la console AWS
    - Configuration de base (utilisateurs, permissions)

3. **Les Services de Base d'AWS**
    - Amazon EC2 (Elastic Compute Cloud)
    - Amazon S3 (Simple Storage Service)
    - Amazon RDS (Relational Database Service)
    - Amazon VPC (Virtual Private Cloud)

4. **Gestion des Identités et des Accès (IAM)**
    - Utilisateurs et groupes IAM
    - Politiques IAM
    - Pratiques recommandées pour IAM

5. **Déploiement et Gestion des Applications avec AWS Elastic Beanstalk**
    - Introduction à Elastic Beanstalk
    - Déploiement d'une application
    - Gestion de l'environnement

6. **Automatisation avec AWS CloudFormation**
    - Introduction à CloudFormation
    - Création et gestion des stacks
    - Automatisation des ressources AWS

7. **Surveillance et Gestion des Logs**
    - Introduction à CloudWatch
    - Création d'alertes et de tableaux de bord
    - Gestion des logs avec CloudWatch Logs

8. **Introduction aux Bases de Données avec AWS**
    - Amazon RDS
    - Amazon DynamoDB
    - Amazon Aurora

9. **Sécurité et Conformité**
    - Meilleures pratiques de sécurité sur AWS
    - AWS Compliance
    - Outils de sécurité AWS

10. **Coûts et Optimisation**
    - Comprendre la tarification AWS
    - Outils d'optimisation des coûts
    - Pratiques recommandées pour réduire les coûts

11. **Projet Final**
    - Spécifications du projet
    - Étapes de réalisation
    - Déploiement et présentation

### Module 1: Introduction au Cloud Computing et AWS

#### Qu'est-ce que le Cloud Computing ?

Le cloud computing est la livraison de services informatiques à la demande, tels que le stockage, la puissance de calcul, les bases de données, le réseau, les logiciels, via Internet. Les avantages incluent l'élasticité, la flexibilité, l'économie de coûts et l'amélioration de la performance.

#### Introduction à AWS

Amazon Web Services (AWS) est une plateforme de services cloud qui propose plus de 200 services complets, tels que le calcul, le stockage, les bases de données, l'analytique, les services de développement, l'intelligence artificielle, l'Internet des objets (IoT), la sécurité, et bien plus encore.

#### Historique et Évolution d'AWS

AWS a été lancé en 2006 avec des services comme S3 et EC2. Depuis, il a évolué pour devenir une plateforme cloud leader avec une adoption massive dans diverses industries.

#### Avantages d'utiliser AWS

- **Évolutivité**: Augmentez ou réduisez vos capacités de manière flexible selon vos besoins.
- **Fiabilité**: Haut niveau de disponibilité et de redondance des services.
- **Sécurité**: Infrastructure sécurisée et nombreuses certifications de conformité.
- **Économie de coûts**: Modèle de tarification à l'utilisation qui permet de contrôler les dépenses.

### Module 2: Premiers Pas avec AWS

#### Création d'un compte AWS

1. Accédez au site [AWS](https://aws.amazon.com/).
2. Cliquez sur "Create an AWS Account".
3. Suivez les instructions pour créer votre compte.

#### Présentation de la console AWS

La console AWS est l'interface web permettant de gérer et d'utiliser tous les services AWS. Elle offre une interface graphique intuitive pour configurer et surveiller les ressources.

#### Configuration de base (utilisateurs, permissions)

1. **Utilisateurs et Groupes**:
    - Créez des utilisateurs individuels pour chaque personne ayant accès à votre compte AWS.
    - Assignez des utilisateurs à des groupes pour gérer les permissions de manière centralisée.

2. **Permissions**:
    - Utilisez IAM pour créer des politiques de permissions.
    - Appliquez des politiques aux utilisateurs et groupes pour contrôler l'accès aux services et ressources AWS.

```bash
# Pour créer un utilisateur IAM avec AWS CLI
aws iam create-user --user-name MonNouvelUtilisateur

# Pour créer un groupe IAM avec AWS CLI
aws iam create-group --group-name MonNouveauGroupe

# Pour attacher une politique à un groupe IAM avec AWS CLI
aws iam attach-group-policy --group-name MonNouveauGroupe --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

# Pour ajouter un utilisateur à un groupe avec AWS CLI
aws iam add-user-to-group --user-name MonNouvelUtilisateur --group-name MonNouveauGroupe
```

### Exercices

1. **Création d'un Compte AWS**:
    - Créez un compte AWS.
    - Explorez la console AWS et identifiez les services mentionnés dans ce module.

2. **Configuration IAM**:
    - Créez un utilisateur IAM avec des permissions limitées.
    - Créez un groupe IAM avec une politique attachée et ajoutez un utilisateur à ce groupe.

### Module 3: Les Services de Base d'AWS

#### Amazon EC2 (Elastic Compute Cloud)

EC2 fournit des instances de serveur virtuel, appelées instances, pour héberger des applications.

1. **Lancer une Instance EC2**:
    - Accédez à la console EC2.
    - Cliquez sur "Launch Instance".
    - Sélectionnez une AMI (Amazon Machine Image).
    - Choisissez un type d'instance.
    - Configurez les détails de l'instance, le stockage, et les balises.
    - Configurez un groupe de sécurité.
    - Lancez l'instance et connectez-vous à l'aide de SSH.

```bash
# Pour lancer une instance EC2 avec AWS CLI
aws ec2 run-instances --image-id ami-0abcdef1234567890 --count 1 --instance-type t2.micro --key-name MonClesEC2 --security-group-ids sg-0123456789abcdef0
```

#### Amazon S3 (Simple Storage Service)

S3 est un service de stockage d'objets hautement évolutif et durable.

1. **Créer un Bucket S3**:
    - Accédez à la console S3.
    - Cliquez sur "Create bucket".
    - Configurez les paramètres du bucket (nom, région).
    - Créez le bucket.

```bash
# Pour créer un bucket S3 avec AWS CLI
aws s3api create-bucket --bucket mon-nouveau-bucket --region us-west-1 --create-bucket-configuration LocationConstraint=us-west-1
```

2. **Charger et Gérer des Objets S3**:
    - Téléchargez un fichier dans le bucket.
    - Configurez les permissions d'objet.

```bash
# Pour télécharger un fichier dans un bucket S3 avec AWS CLI
aws s3 cp mon-fichier.txt s3://mon-nouveau-bucket/

# Pour configurer les permissions d'un objet S3 avec AWS CLI
aws s3api put-object-acl --bucket mon-nouveau-bucket --key mon-fichier.txt --acl public-read
```

### Exercices

1. **Déploiement d'une Instance EC2**:
    - Lancez une instance EC2.
    - Connectez-vous à l'instance et installez un serveur web (Apache, Nginx).

```bash
# Connectez-vous à l'instance EC2 avec SSH
ssh -i "MonClesEC2.pem" ec2-user@ec2-xx-xxx-xxx-xx.compute-1.amazonaws.com

# Installez Apache sur l'instance EC2 (exemple pour Amazon Linux)
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

2. **Gestion de Stockage avec S3**:
    - Créez un bucket S3.
    - Téléchargez plusieurs fichiers et configurez leurs permissions.

### Module 4: Gestion des Identités et des Accès (IAM)

#### Utilisateurs et Groupes IAM

IAM permet de gérer l'accès aux services et ressources AWS en créant des utilisateurs et des groupes, et en leur assignant des politiques.

1. **Créer des Utilisateurs IAM**:
    - Accédez à la console IAM.
    - Créez un utilisateur avec des permissions spécifiques.

2. **Créer des Groupes IAM**:
    - Créez un groupe et assignez une politique de permissions.

```bash
# Pour créer un utilisateur IAM avec AWS CLI
aws iam create-user --user-name MonNouvelUtilisateur

# Pour créer un groupe IAM avec AWS CLI
aws iam create-group --group-name MonNouveauGroupe

# Pour attacher une politique à un groupe IAM avec AWS CLI
aws iam attach-group-policy --group-name MonNouveauGroupe --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

# Pour ajouter un utilisateur à un groupe avec AWS CLI
aws iam add-user-to-group --user-name MonNouvelUtilisateur --group-name MonNouveauGroupe
```

#### Politiques IAM

Les politiques définissent les permissions et sont écrites en JSON. Elles peuvent être attachées à des utilisateurs, groupes ou rôles.

1. **Créer une Politique IAM**:
    - Utilisez le cré

ateur de politique visuel ou éditez le JSON directement.
    - Attachez la politique à un utilisateur ou un groupe.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::example_bucket/*"
    }
  ]
}
```

```bash
# Pour créer une politique IAM avec AWS CLI
aws iam create-policy --policy-name MonNouvellePolitique --policy-document file://mon_nouvelle_politique.json
```

### Exercices

1. **Gestion des Utilisateurs IAM**:
    - Créez plusieurs utilisateurs avec différentes permissions.
    - Créez un groupe avec des politiques spécifiques et ajoutez des utilisateurs.

### Module 5: Déploiement et Gestion des Applications avec AWS Elastic Beanstalk

#### Introduction à Elastic Beanstalk

Elastic Beanstalk simplifie le déploiement et la gestion des applications dans le cloud. Il prend en charge plusieurs langages de programmation.

#### Déploiement d'une Application

1. **Créer un Environnement Elastic Beanstalk**:
    - Accédez à la console Elastic Beanstalk.
    - Créez une application et un environnement.
    - Déployez une application (ex: application web en Node.js ou Python).

```bash
# Installer l'outil EB CLI
pip install awsebcli

# Initialiser une application Elastic Beanstalk
eb init -p python-3.7 mon-application

# Créer un environnement Elastic Beanstalk et déployer l'application
eb create mon-environnement-dev
eb deploy
```

#### Gestion de l'Environnement

1. **Surveiller et Gérer l'Environnement**:
    - Utilisez les outils intégrés pour surveiller la performance.
    - Mettre à jour l'application avec de nouvelles versions.

```bash
# Pour surveiller l'environnement
eb status

# Pour mettre à jour l'application
eb deploy
```

### Exercices

1. **Déploiement d'une Application Web**:
    - Créez et déployez une application web simple en utilisant Elastic Beanstalk.
    - Surveillez et mettez à jour l'application.

### Module 6: Automatisation avec AWS CloudFormation

#### Introduction à CloudFormation

CloudFormation permet de modéliser et de provisionner des ressources AWS à l'aide de templates.

#### Création et Gestion des Stacks

1. **Créer un Stack CloudFormation**:
    - Écrivez un template CloudFormation (en JSON ou YAML).
    - Déployez le stack en utilisant la console CloudFormation.

```yaml
# Exemple de template CloudFormation en YAML
Resources:
  MyBucket:
    Type: "AWS::S3::Bucket"
    Properties:
      BucketName: "mon-nouveau-bucket"
```

```bash
# Pour déployer un stack CloudFormation avec AWS CLI
aws cloudformation create-stack --stack-name MonNouveauStack --template-body file://mon_template.yaml
```

#### Automatisation des Ressources AWS

1. **Utiliser des Templates Préexistants**:
    - Explorez les templates AWS CloudFormation disponibles.
    - Modifiez et déployez un template pour répondre à vos besoins.

### Exercices

1. **Création de Templates CloudFormation**:
    - Écrivez un template pour déployer une application web avec une base de données.
    - Déployez le stack et vérifiez les ressources créées.

### Module 7: Surveillance et Gestion des Logs

#### Introduction à CloudWatch

CloudWatch est un service de surveillance pour les ressources AWS et les applications.

#### Création d'Alertes et de Tableaux de Bord

1. **Configurer CloudWatch**:
    - Créez des alarmes pour surveiller les métriques (ex: CPU, utilisation de mémoire).
    - Créez des tableaux de bord personnalisés pour visualiser les métriques.

```bash
# Pour créer une alarme CloudWatch avec AWS CLI
aws cloudwatch put-metric-alarm --alarm-name "AlarmeCPU" --metric-name "CPUUtilization" --namespace "AWS/EC2" --statistic "Average" --period 300 --threshold 70 --comparison-operator "GreaterThanThreshold" --dimensions "Name=InstanceId,Value=i-0123456789abcdef0" --evaluation-periods 2 --alarm-actions "arn:aws:sns:us-west-1:123456789012:MonTopic"

# Pour créer un tableau de bord CloudWatch avec AWS CLI
aws cloudwatch put-dashboard --dashboard-name "MonTableauDeBord" --dashboard-body file://mon_tableau_de_bord.json
```

#### Gestion des Logs avec CloudWatch Logs

1. **Configurer CloudWatch Logs**:
    - Activez la collecte des logs pour vos instances EC2 ou autres services.
    - Créez des filtres de logs et configurez des actions basées sur les logs.

```bash
# Pour créer un groupe de logs CloudWatch
aws logs create-log-group --log-group-name MonGroupeDeLogs

# Pour créer un flux de logs CloudWatch
aws logs create-log-stream --log-group-name MonGroupeDeLogs --log-stream-name MonFluxDeLogs

# Pour mettre en place une politique de rétention de logs
aws logs put-retention-policy --log-group-name MonGroupeDeLogs --retention-in-days 14
```

### Exercices

1. **Surveillance des Instances EC2**:
    - Configurez des alarmes CloudWatch pour une instance EC2.
    - Créez un tableau de bord pour visualiser les métriques.

2. **Gestion des Logs**:
    - Configurez CloudWatch Logs pour une application.
    - Créez des filtres de logs et configurez des actions.

### Module 8: Introduction aux Bases de Données avec AWS

#### Amazon RDS

RDS est un service de base de données relationnelle géré qui prend en charge plusieurs moteurs de base de données.

1. **Créer une Instance RDS**:
    - Accédez à la console RDS.
    - Créez une nouvelle instance de base de données.

```bash
# Pour créer une instance RDS avec AWS CLI
aws rds create-db-instance --db-instance-identifier MonInstanceRDS --db-instance-class db.t2.micro --engine mysql --master-username admin --master-user-password MonMotDePasse --allocated-storage 20
```

#### Amazon DynamoDB

DynamoDB est un service de base de données NoSQL géré.

1. **Créer une Table DynamoDB**:
    - Accédez à la console DynamoDB.
    - Créez une nouvelle table avec une clé primaire.

```bash
# Pour créer une table DynamoDB avec AWS CLI
aws dynamodb create-table --table-name MaTable --attribute-definitions AttributeName=Id,AttributeType=S --key-schema AttributeName=Id,KeyType=HASH --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
```

### Exercices

1. **Déploiement d'une Base de Données RDS**:
    - Créez et configurez une instance RDS.
    - Connectez-vous à la base de données et effectuez des opérations CRUD.

```sql
-- Exemple de commandes SQL pour MySQL
CREATE DATABASE MaBaseDeDonnees;
USE MaBaseDeDonnees;
CREATE TABLE Utilisateurs (ID INT AUTO_INCREMENT PRIMARY KEY, Nom VARCHAR(255), Email VARCHAR(255));
INSERT INTO Utilisateurs (Nom, Email) VALUES ('Alice', 'alice@example.com'), ('Bob', 'bob@example.com');
SELECT * FROM Utilisateurs;
```

2. **Gestion d'une Table DynamoDB**:
    - Créez une table DynamoDB.
    - Effectuez des opérations de lecture et d'écriture.

```bash
# Pour ajouter un élément à une table DynamoDB avec AWS CLI
aws dynamodb put-item --table-name MaTable --item '{"Id": {"S": "001"}, "Nom": {"S": "Alice"}, "Email": {"S": "alice@example.com"}}'

# Pour lire un élément d'une table DynamoDB avec AWS CLI
aws dynamodb get-item --table-name MaTable --key '{"Id": {"S": "001"}}'
```

### Module 9: Sécurité et Conformité

#### Meilleures Pratiques de Sécurité sur AWS

1. **Gestion des Permissions et Accès**:
    - Utilisez IAM pour contrôler l'accès.
    - Activez l'authentification multi-facteurs (MFA).

```bash
# Pour activer MFA pour un utilisateur IAM avec AWS CLI
aws iam enable-mfa-device --user-name MonUtilisateur --serial-number arn:aws:iam::123456789012:mfa/MonUtilisateur --authentication-code1 123456 --authentication-code2 654321
```

2. **Chiffrement des Données**:
    - Utilisez le chiffrement côté serveur pour S3.
    - Chiffrez les bases de données RDS.

```bash
# Pour activer le chiffrement côté serveur pour un bucket S3 avec AWS CLI
aws s3api put-bucket-encryption --bucket mon-nouveau-bucket --server-side-encryption-configuration '{"Rules": [{"ApplyServerSideEncryptionByDefault": {"SSEAlgorithm": "AES256"}}]}'

# Pour créer une instance RDS avec chiffrement activé avec AWS CLI
aws rds create-db-instance --db-instance-identifier MonInstanceRDS --db-instance-class db.t2.micro --engine mysql --master-username admin --master-user-password MonMotDePasse --allocated-storage 20

 --storage-encrypted
```

#### AWS Compliance

1. **Certification et Conformité**:
    - Familiarisez-vous avec les certifications et programmes de conformité AWS.
    - Utilisez AWS Artifact pour accéder aux rapports de conformité.

### Exercices

1. **Implémentation de la Sécurité**:
    - Configurez MFA pour les utilisateurs IAM.
    - Activez le chiffrement pour un bucket S3 et une base de données RDS.

### Module 10: Coûts et Optimisation

#### Comprendre la Tarification AWS

1. **Modèles de Tarification**:
    - Tarification à l'utilisation.
    - Tarification par abonnement et réservations.

#### Outils d'Optimisation des Coûts

1. **AWS Cost Explorer**:
    - Utilisez Cost Explorer pour analyser les coûts.
    - Créez des alertes de coût pour surveiller les dépenses.

```bash
# Pour activer les alertes de budget avec AWS CLI
aws budgets create-budget --account-id 123456789012 --budget '{"BudgetName": "MonBudget", "BudgetLimit": {"Amount": "1000", "Unit": "USD"}, "TimeUnit": "MONTHLY", "BudgetType": "COST"}'
```

#### Pratiques Recommandées pour Réduire les Coûts

1. **Optimisation des Ressources**:
    - Arrêtez les instances non utilisées.
    - Utilisez des instances réservées et des plans d'épargne.

```bash
# Pour arrêter une instance EC2 avec AWS CLI
aws ec2 stop-instances --instance-ids i-0123456789abcdef0
```

### Exercices

1. **Analyse et Optimisation des Coûts**:
    - Utilisez AWS Cost Explorer pour analyser les coûts de votre compte.
    - Identifiez et mettez en œuvre des mesures d'optimisation des coûts.

### Module 11: Projet Final

#### Spécifications du Projet

1. **Déploiement d'une Application Web Complète**:
    - Utilisez les services AWS pour déployer une application web avec une base de données et un stockage S3.
    - Implémentez des mesures de sécurité et de surveillance.

#### Étapes de Réalisation

1. **Planification**:
    - Définissez les composants de l'application et les services AWS nécessaires.
    - Créez un plan de déploiement détaillé.

2. **Déploiement**:
    - Déployez les composants de l'application en suivant le plan de déploiement.
    - Configurez les services AWS pour répondre aux exigences de l'application.

3. **Tests et Validation**:
    - Testez l'application pour s'assurer qu'elle fonctionne correctement.
    - Validez la sécurité et la performance de l'application.

#### Déploiement et Présentation

1. **Documentation**:
    - Documentez le processus de déploiement et les configurations.
    - Préparez une présentation pour expliquer le projet et les décisions prises.

2. **Présentation Finale**:
    - Présentez le projet à un public (professeurs, collègues, etc.).
    - Répondez aux questions et recevez des retours pour améliorer le projet.

### Exercices

1. **Réalisation du Projet Final**:
    - Suivez les étapes de réalisation pour déployer l'application.
    - Documentez et préparez la présentation du projet.

