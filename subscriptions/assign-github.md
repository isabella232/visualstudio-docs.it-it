---
title: Bundle di Visual Studio + GitHub | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/23/2019
ms.topic: conceptual
description: Gestione delle sottoscrizioni nel bundle Visual Studio + GitHub
ms.openlocfilehash: 875f91f19aee33d290933e6a5455a4dead78d6f0
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783629"
---
# <a name="managing-visual-studio-subscriptions-with-github-enterprise"></a>Gestione delle sottoscrizioni di Visual Studio con GitHub Enterprise

I clienti che dispongono di contratti Enterprise (EA) con Microsoft hanno il diritto di acquistare un nuovo bundle di sottoscrizioni che riunisce le sottoscrizioni standard di Visual Studio e di GitHub Enterprise. Per i sottoscrittori di Visual Studio, si tratta di un modo semplice ed economico per acquisire GitHub Enterprise. 

Quando l'organizzazione acquista sottoscrizioni di Visual Studio con GitHub Enterprise, il loro provisioning e la gestione vengono suddivisi in due parti.

## <a name="managing-visual-studio-subscriptions"></a>Gestione delle sottoscrizioni di Visual Studio

Quando l'organizzazione acquista sottoscrizioni di Visual Studio con GitHub Enterprise, il provisioning della porzione Visual Studio delle sottoscrizioni viene eseguito immediatamente e le sottoscrizioni sono disponibili nel portale [Subscriptions Administration](https://manage.visualstudio.com) di Visual Studio, da cui possono essere assegnate e gestite. 

Per altre informazioni sulla gestione delle sottoscrizioni, consultare questi argomenti:
- [Uso del portale di amministrazione](using-admin-portal.md)
- [Assegnare sottoscrizioni](assign-license.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Sovrassegnazioni](handle-overclaimed-license.md)

> [!Important]
> Se le sottoscrizioni di Visual Studio con GitHub Enterprise sono assegnate dagli amministratori delle sottoscrizioni di Visual Studio e non ne è mai stata acquistata una, queste non risulteranno visibili agli amministratori di GitHub Enterprise dell'organizzazione. Per fare in modo che le sottoscrizioni di GitHub Enterprise siano visibili, è necessario effettuare un acquisto che includa **almeno una** sottoscrizione di Visual Studio Professional con GitHub Enterprise o di Visual Studio Enterprise con GitHub Enterprise la prima volta che le sottoscrizioni vengono assegnate.  
>
> È responsabilità del cliente rimanere conforme ai requisiti di licenza per questa sottoscrizione verificando che per ogni sottoscrizione di GitHub assegnata sia presente una sottoscrizione di Visual Studio con GitHub corrispondente assegnata nel portale di gestione.

## <a name="managing-github-enterprise-subscriptions"></a>Gestione delle sottoscrizioni di GitHub Enterprise

Quando vengono acquistate sottoscrizioni di GitHub Enterprise, GitHub collabora con i clienti per creare e configurare le organizzazioni che accederanno a GitHub e per identificare gli amministratori.  Gli amministratori saranno informati del loro incarico tramite notifica.  

Poiché questo processo è più complesso, dopo l'acquisto delle sottoscrizioni potrebbero trascorrere diversi giorni prima della completa configurazione delle organizzazioni e degli amministratori.

GitHub è disponibile come GitHub.com basato su cloud o in versione locale come GitHub Enterprise Server.  I processi per la gestione delle due versioni variano.  GitHub offre un'ampia gamma di argomenti della Guida e di guide di amministrazione per aiutare gli utenti a gestire le sottoscrizioni di GitHub Enterprise.  Segue un elenco di collegamenti ad argomenti selezionati.  

### <a name="githubcom"></a>GitHub.com 

Per altre informazioni sulla gestione di GitHub.com, consultare gli argomenti seguenti in [GitHub Help](https://help.github.com/en) (Guida di GitHub).
- [Elenco completo degli argomenti della Guida](https://help.github.com/en)
- [Managing membership in your organization](https://help.github.com/en/articles/managing-membership-in-your-organization) (Gestione dell'appartenenza all'interno dell'organizzazione)
> - [Inviting users to join your organization](https://help.github.com/en/articles/inviting-users-to-join-your-organization) (Invito agli utenti a unirsi all'organizzazione)
> - [Removing users from teams/organizations](https://help.github.com/en/articles/removing-a-member-from-your-organization) (Rimozione di utenti da team/organizzazioni)
> - [Reinstating a former member of your organization](https://help.github.com/en/articles/reinstating-a-former-member-of-your-organization) (Reintegro di un ex membro dell'organizzazione)
- [Managing access using roles](https://help.github.com/en/articles/managing-peoples-access-to-your-organization-with-roles) (Gestione degli accessi tramite i ruoli)
- [Organizing users into teams](https://help.github.com/en/articles/organizing-members-into-teams) (Organizzazione degli utenti in team)
- [Managing access to your organization's repositories](https://help.github.com/en/articles/managing-access-to-your-organizations-repositories) (Gestione dell'accesso ai repository dell'organizzazione)

### <a name="github-enterprise-server"></a>GitHub Enterprise Server

La Guida di GitHub offre una serie di guide di amministrazione per rispondere a domande e fornire suggerimenti sulla gestione dell'implementazione di GitHub Enterprise Server nell'organizzazione.

- [Visualizzazione di tutte le guide di amministrazione](https://help.github.com/en/enterprise/2.16/admin)
- [User Management](https://help.github.com/en/enterprise/2.16/admin/user-management) (Gestione degli utenti)
> - [Organizations and teams](https://help.github.com/en/enterprise/2.16/admin/user-management/organizations-and-teams) (Organizzazioni e team)
> > - [Creating organizations](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-organizations) (Creazione di organizzazioni)
> > - [Creating teams](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-teams) (Creazione di team)
> > - [Adding people to teams](https://help.github.com/en/enterprise/2.16/admin/user-management/adding-people-to-teams) (Aggiunta di utenti ai team)
> > - [Removing people from teams and organizations](https://help.github.com/en/enterprise/2.16/admin/user-management/removing-users-from-teams-and-organizations) (Rimozione di utenti da team e organizzazioni)
> - [User security](https://help.github.com/en/enterprise/2.16/admin/user-management/user-security) (Sicurezza utente)
- [Installing and configuring GitHub Enterprise Server](https://help.github.com/en/enterprise/2.16/admin/installation) (Installazione e configurazione di GitHub Enterprise Server)

## <a name="support-resources"></a>Risorse di supporto

- È possibile trovare risposte a domande su un'ampia gamma di argomenti relativi a GitHub in [GitHub Help](https://help.github.com/en) (Guida di GitHub).
- Ottenere assistenza da altri utenti di GitHub nel [GitHub Community Forum](https://github.community/) (forum della Community GitHub).
- Per assistenza per le vendite, le sottoscrizioni, gli account e la fatturazione per le sottoscrizioni di Visual Studio, contattare il [servizio di supporto per le sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/) di Visual Studio.
- Per domande sull'IDE di Visual Studio, Azure DevOps Services o altri prodotti e servizi Visual Studio,  visitare il [sito del supporto di Visual Studio](https://visualstudio.microsoft.com/support/).
- Ottenere [supporto tecnico](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) per GitHub Enterprise.   

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla gestione delle sottoscrizioni di Visual Studio con GitHub Enterprise, consultare il [portale di amministrazione delle sottoscrizioni](https://visualstudio.microsoft.com/subscriptions-administration/) di Visual Studio.
