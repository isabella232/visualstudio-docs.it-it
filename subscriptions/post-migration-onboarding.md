---
title: Onboarding nel portale di amministrazione delle sottoscrizioni di Visual Studio dopo la migrazione dell'organizzazione
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 07/12/2018
Ms.topic: Get-Started-Article
Description: Learn how to successfully onboard your organization for Visual Studio subscriptions after migrating to the administration portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: c6f0f3de58f2f9f7d532a7b1b84520644fbdb1c7
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39234794"
---
# <a name="onboarding-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-was-migrated"></a>Onboarding nel portale di amministrazione delle sottoscrizioni di Visual Studio dopo la migrazione dell'organizzazione 

Se l'utente ha gestito sottoscrizioni di Visual Studio in Volume Licensing Service Center (VLSC) e recentemente ha visitato il sito per gestire le sottoscrizioni, noterà che la gestione delle sottoscrizioni non è più disponibile in VLSC. Il processo per gestire le sottoscrizioni era simile al seguente:

![Sottoscrizioni VLSC](_img/post-migration-onboarding/vlsc-subscriptions.png)

Quando si accede alla pagina delle sottoscrizioni, in genere si fa clic sul collegamento seguente. 

![Collegamento di riepilogo della relazione](_img/post-migration-onboarding/relationship-summary-link.png)

Questa operazione in precedenza apriva la pagina in cui era possibile gestire le sottoscrizioni.   Tuttavia ora le sottoscrizioni vengono gestite tramite un nuovo portale chiamato portale di amministrazione delle sottoscrizioni di Visual Studio.  Il contatto principale o il contatto per le comunicazioni dell'organizzazione dovrà eseguire varie operazioni nel quadro del contratto multilicenza dell'organizzazione stessa. Se il contatto principale o per le comunicazioni dell'organizzazione non ha completato questa operazione o non è più disponibile, possono verificarsi diversi scenari. Le istruzioni elencate di seguito illustrano come accedere alla gestione delle sottoscrizioni. 

È possibile riscontrare uno degli scenari seguenti:
1.  [Il contatto principale non ha completato il processo di onboarding](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2.  [Il contatto principale ha completato l'onboarding, ma non ha aggiunto l'utente come amministratore.  Le credenziali dell'utente erano elencate in VLSC.](#Primary-Contact-did-not-provide-you-administrator-access) 
3.  [Il contatto principale ha completato l'onboarding, ma non ha aggiunto l'utente come amministratore e le credenziali non erano elencate in VLSC](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> Se l'utente è il contatto principale o il contatto per le comunicazioni e non ha completato l'onboarding, dovrà eseguire la procedura nello scenario 1 per configurare l'organizzazione. 

Di seguito sono visualizzati esempi delle schermate che vengono visualizzate e i passaggi da eseguire per i diversi scenari. 

## <a name="onboarding-not-completed-by-primary-contact"></a>Onboarding non completato dal contatto principale

Se il contatto principale non ha completato l'onboarding, è probabile che venga visualizzata la schermata seguente. Se è disponibile l'accesso a [Volume Licensing Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) è possibile completare il processo e accedere alla gestione delle sottoscrizioni. È necessario il numero [PCN (Public Customer Number)](find-pcn.md) dell'organizzazione, disponibile in VLSC. 

Se il contatto principale non ha completato il processo di onboarding, è sufficiente immettere il [PCN](find-pcn.md) nel campo e selezionare "Invia invito". 

![Invia un messaggio di posta elettronica contenente l'invito](_img/post-migration-onboarding/send-invitation.png)

Dopo aver fatto clic sul pulsante per l'invio dell'invito si riceverà un messaggio di posta elettronica con un collegamento univoco per completare il processo di onboarding. Fare clic sul collegamento nel messaggio di posta elettronica, accedere con l'indirizzo di posta elettronica e, anche in questo caso, immettere il PCN. Il collegamento univoco nel messaggio di posta elettronica è l'elemento che consente l'accesso al portale di amministrazione delle sottoscrizioni di Visual Studio. Sarà quindi possibile accedere e gestire le sottoscrizioni. 

![Messaggio di posta elettronica per operazione completata](_img/post-migration-onboarding/email-success.png)


## <a name="primary-contact-did-not-provide-you-administrator-access"></a>Il contatto principale non ha fornito all'utente l'accesso come amministratore

Se il contatto principale ha completato il processo di onboarding e le credenziali dell'utente si trovavano in VLSC, ma il contatto non ha fornito all'utente l'accesso come amministratore, durante l'accesso al [portale di amministrazione delle sottoscrizioni di Visual Studio](https://manage.visualstudio.com/) viene visualizzata la notifica seguente.  Per diventare un amministratore è necessario contattare uno degli amministratori con privilegi avanzati dell'organizzazione, elencati nella schermata.

![Elenco di amministratori](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>Le credenziali dell'utente non erano incluse in VLSC prima della migrazione

Se il contatto principale ha completato il processo di onboarding ma non ha aggiunto le credenziali dell'utente e tali credenziali non erano presenti in VLSC, durante l'accesso al [portale di amministrazione delle sottoscrizioni di Visual Studio](https://manage.visualstudio.com/) viene visualizzata la notifica seguente. È necessario rivolgersi al [contatto principale](find-primary-contact.md) per ottenere l'accesso al portale. 

![Utente non trovato](_img/post-migration-onboarding/cant-find-you.png)