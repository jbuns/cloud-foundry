---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tutoriel d'initiation
{: #getting-started}

L'environnement {{site.data.keyword.cfee_full}} est une plateforme cloud pour l'hébergement d'applications et de services dans le cloud. {{site.data.keyword.cfee_full_notm}} facilite la mise à l'échelle des applications à mesure de l'augmentation de la consommation, en simplifiant le contexte d'exécution, le middleware et l'infrastructure de sorte que vous puissiez vous concentrer sur le développement d'applications.
{: shortdesc}

Ce tutoriel d'initiation montre comment créer un environnement {{site.data.keyword.cfee_full_notm}}, ajouter des utilisateurs, créer une organisation et des espaces, déployer des applications et lier ces applications à des services.

## Comprendre les droits
{: #permissions}

Pour travailler avec des instances d'{{site.data.keyword.cfee_full_notm}}, les utilisateurs du service doivent disposer des droits appropriés. Pour plus d'informations, voir [Droits](/docs/cloud-foundry/permissions.html).

## Etape 1 : Veillez à ce que le compte {{site.data.keyword.Bluemix_notm}} puisse créer des ressources d'infrastructure
{: #accountprep-environment}

Les instances CFEE sont déployées dans des ressources d'infrastructure, qui sont des noeuds worker Kubernetes issus du service de conteneur IBM. [Préparez votre compte IBM Cloud](/docs/cloud-foundry/prepare-account.html) de sorte qu'il puisse créer les ressources d'infrastructure nécessaires à une instance CFEE.

## Etape 2 : Créez votre instance CFEE
{: #creating-environment}

Avant de créer votre environnement CFEE, vérifiez que vous vous trouvez dans le compte {{site.data.keyword.Bluemix_notm}} sous lequel vous voulez créer l'environnement et que vous disposez des règles d'accès requises (étape 1 ci-dessus).

1. Ouvrez le [catalogue](https://console.bluemix.net/catalog) {{site.data.keyword.Bluemix_notm}}.
2. Recherchez le service {{site.data.keyword.cfee_full_notm}} dans le catalogue et cliquez dessus pour ouvrir la page de présentation du service.
3. Le premier écran de la page de création présente les principales fonctions du service. Cliquez sur **Continuer**
4. Configurez l'instance à créer comme suit :
    * Sélectionnez un plan (la disponibilité des plans peut être restreinte en phase bêta).
    * Entrez un **Nom** pour l'instance de service.
    * Sélectionnez un **Emplacement** où l'instance de service doit être mise à disposition.
    * Sélectionnez le **Nombre de cellules** pour l'environnement Cloud Foundry.
    * Sélectionnez le **Type de machine**, qui détermine la taille des cellules Cloud Foundry (unité centrale et mémoire).
    * Sélectionnez un **Groupe de ressources** sous lequel l'environnement est regroupé. Seuls les groupes de ressources auxquels vous avez accès dans le compte IBM Cloud en cours sont répertoriés dans le menu déroulant _Groupes de ressources_, ce qui signifie que vous devez détenir le droit d'accès à au moins un groupe de ressources du compte pour pouvoir créer une instance CFEE.
5. Eventuellement, ouvrez la section **Infrastructure** pour afficher les propriétés du cluster Kubernetes qui prend en charge l'instance CFEE. Le **nombre de noeuds worker** est égal au nombre de cellules plus 2 (deux des noeuds worker Kubernetes mis à disposition prennent en charge le plan de contrôle CFEE).
6. Le **Récapitulatif de la commande**, sur la droite de la page, indique le coût de l'instance CFEE et le total estimé.
7. Cliquez sur **Créer** pour ouvrir le tableau de bord de l'environnement et afficher le statut et la progression de l'opération de création.
8. Une fois la mise à disposition lancée, l'environnement est affiché dans le tableau de bord {{site.data.keyword.Bluemix_notm}} et dans le [tableau de bord des environnements Cloud Foundry](https://console.bluemix.net/dashboard/cloudfoundry?filter=cf_environments).  Le statut indique quand la mise à disposition est terminée.

Le processus automatisé de création de l'environnement déploie l'infrastructure dans un cluster Kubernetes et la configure de sorte qu'elle soit prête pour utilisation. Ce processus prend entre 90 et 120 minutes.

**Remarque :** le cluster Kubernetes dans lequel l'environnement est déployé s'affiche dans le [tableau de bord {{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/dashboard/apps/). Pour plus d'informations, voir la [ documentation du service de conteneur {{site.data.keyword.Bluemix_notm}}](/docs/containers/cs_why.html#cs_ov).

## Etape 3: Créez des organisations et des espaces

Une fois l'environnement {{site.data.keyword.cfee_full_notm}} créé, voir [Création d'organisations et d'espaces](/docs/cloud-foundry/orgs-spaces.html) pour savoir comment structurer l'environnement en créant des organisations et des espaces. Dans un environnement {{site.data.keyword.cfee_full_notm}}, les applications sont limitées à des espaces spécifiques. Un espace existe lui-même au sein d'une organisation spécifique. Les membres d'une organisation se partagent un plan d'établissement des quotas, des applications, des instances de service et des domaines personnalisés.

**Remarque :** la page _Organisations Cloud Foundry_ accessible via le menu **_Gérer > Compte > Organisations Cloud Foundry_** de l'en-tête IBM Cloud du haut est conçue exclusivement pour les organisations IBM Cloud publiques, **pas pour les organisations CFEE**. Les organisations CFEE sont gérées dans la page _Organisations_ d'une instance CFEE. Ouvrez l'interface utilisateur CFEE et cliquez sur la page **_Organisations_** pour créer et gérer des organisations pour cet environnement CFEE.

## Etape 4 : Ajoutez des utilisateurs aux organisations et espaces

[Ajoutez des utilisateurs](/docs/cloud-foundry/add-users.html) à ces organisations et espaces avec des affectations de rôles spécifiques qui contrôlent leur niveau d'accès. Pour pouvoir devenir membres d'organisations et d'espaces d'un environnement CFEE, les utilisateurs doivent préalablement obtenir un droit d'accès à l'instance CFEE. Voir [Droits](/docs/cloud-foundry/permissions.html).

## Etape 5 : Déployez et affichez des applications

Lorsque vous êtes prêt, vous pouvez [déployer l'application](/docs/cloud-foundry/deploy-apps.html) à l'aide de l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}.  Affichez dans l'interface utilisateur la liste des applications déployées dans un espace CFEE spécifique ou globalement dans toutes les instances CFEE. Vous pouvez également démarrer, arrêter ou supprimer des applications dans ces vues.

## Etape 6 : Créez des alias et des instances de service

Créez des [alias de service](/docs/cloud-foundry/add-serv-inst.html) à partir des instances de service disponibles dans le compte IBM Cloud afin de les optimiser dans vos applications CFEE.

## Etape 7 : Liez des applications à des instances de service

[Liez votre application](/docs/cloud-foundry/binding.html) à un alias d'instance de service afin d'utiliser les fonctions du service.

## Etape 8 : Installez la console Stratos pour gérer les applications (facultatif)

La console Stratos est un outil Web open source qui fonctionne avec Cloud Foundry. L'application de console Stratos peut éventuellement être installée et utilisée dans un environnement CFEE spécifique afin de gérer ses organisations, ses espaces et ses applications.

Les utilisateurs dotés du rôle d'administrateur ou d'éditeur IBM Cloud dans l'instance CFEE peuvent installer l'application de console Stratos dans cette instance CFEE.

Pour installer l'application de console Stratos :

1. Ouvrez l'instance CFEE dans laquelle vous voulez installer la console Stratos.
2. Cliquez sur **Installer la console Stratos** dans la page de présentation. Le bouton ne s'affiche que pour les utilisateurs ayant des droits d'administrateur ou d'éditeur sur cette instance CFEE.
3. Dans la boîte de dialogue Installer la console Stratos, sélectionnez une option d'installation. Vous pouvez installer l'application de console Stratos sur le plan de contrôle CFEE ou dans l'une des cellules. Sélectionnez une version de la console Stratos ainsi que le nombre d'instances de l'application à installer. Si vous installez l'application de console Stratos dans une cellule, vous êtes invité à indiquer l'organisation et l'espace où déployer l'application.
4. Cliquez sur **Installer**.

L'installation de l'application prend environ 5 minutes. Une fois l'installation terminée, un bouton **Console Stratos** s'affiche dans la page de présentation à la place du bouton _Installer la console Stratos_. Le bouton _Console Stratos_ permet de démarrer la console et il est disponible pour tous les utilisateurs ayant accès à l'instance CFEE. Les affectations d'appartenance à une organisation et à un espace sont susceptibles de limiter les possibilités d'affichage et de gestion d'un utilisateur dans la console Stratos.

Pour démarrer la console Stratos :

1. Ouvrez l'instance CFEE dans laquelle la console Stratos a été installée.
2. Cliquez sur **Console Stratos** dans la page de présentation.
3. La console Stratos s'ouvre dans un onglet de navigateur distinct. A la première ouverture de la console, vous êtes invité à accepter deux avertissements consécutifs en raison de certificats autosignés.
4. Cliquez sur **Connexion** pour ouvrir la console. Aucune donnée d'identification n'est requise puisque l'application utilise vos données d'identification {{site.data.keyword.Bluemix_notm}}.

Vos possibilités d'affichage et de gestion dépendent de vos rôles et appartenances aux organisations et espaces.