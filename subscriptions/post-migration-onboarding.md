---
title: Eseguire l'onboarding nel portale di amministrazione delle sottoscrizioni di Visual Studio dopo la migrazione
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 07/12/2018
ms.topic: conceptual
description: Informazioni su come eseguire l'onboarding dopo la migrazione dell'organizzazione nel portale di amministrazione delle sottoscrizioni di Visual Studio.
searchscope: VS Subscription
ms.openlocfilehash: 3916fd762e9a2feaaa4892e4233d08a345db44a1
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954228"
---
# <a name="onboard-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-is-migrated"></a>Eseguire l'onboarding nel portale di amministrazione delle sottoscrizioni di Visual Studio dopo la migrazione dell'organizzazione

Se le sottoscrizioni di Visual Studio sono state gestite nel sito Microsoft Volume Licensing Service Center (VLSC) e di recente è stato visitato il sito per gestire le sottoscrizioni, si noterà che la gestione delle sottoscrizioni non è più disponibile in VLSC. Il processo per gestire le sottoscrizioni era simile al seguente:
> [!div class="mx-imgBorder"]
> ![Screenshot di Microsoft VLSC, con la scheda relativa alle sottoscrizioni evidenziata](_img/post-migration-onboarding/vlsc-subscriptions.png)

Tuttavia ora le sottoscrizioni vengono gestite tramite un nuovo portale chiamato portale di amministrazione delle sottoscrizioni di Visual Studio. In genere, questo processo viene eseguito dal contatto principale o dal contatto per le comunicazioni indicato nel contratto multilicenza dell'organizzazione. In caso contrario, le informazioni seguenti consentono di accedere per eseguire le operazioni di gestione delle sottoscrizioni.

Potrebbe verificarsi uno degli scenari seguenti:

1. [Il contatto principale non ha completato il processo di onboarding](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup>. 
2. [Il contatto principale ha completato l'onboarding, ma non ha aggiunto l'utente come amministratore. Le credenziali dell'utente erano elencate in VLSC.](#Primary-Contact-did-not-provide-you-administrator-access) 
3. [Il contatto principale ha completato l'onboarding, ma non ha aggiunto l'utente come amministratore. Le credenziali dell'utente non sono state indicate in VLSC.](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> Se si è il contatto principale o il contatto per le comunicazioni e non è stato completato l'onboarding, eseguire la procedura nello scenario 1 per la configurazione dell'organizzazione.

Le sezioni seguenti forniscono altre informazioni dettagliate su ognuno di questi scenari.

## <a name="onboarding-not-completed-by-primary-contact"></a>Onboarding non completato dal contatto principale

Se il contatto principale non ha completato l'onboarding, viene visualizzata la schermata seguente. Se è possibile accedere a [Volume Licensing Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx), completare il processo per ottenere l'accesso per la gestione delle sottoscrizioni. È necessario il numero [PCN (Public Customer Number)](find-pcn.md) dell'organizzazione, disponibile in VLSC.

Nel campo relativo al numero PCN, immettere il numero [PCN](find-pcn.md)e selezionare **Send Invitation Email** (Invia invito per posta elettronica).
> [!div class="mx-imgBorder"]
> ![Screenshot del portale di amministrazione delle sottoscrizioni di Visual Studio](_img/post-migration-onboarding/send-invitation.png)

Si riceverà un messaggio di posta elettronica con un collegamento univoco per completare il processo di onboarding. Fare clic sul collegamento nel messaggio di posta elettronica, accedere con l'indirizzo di posta elettronica e, anche in questo caso, immettere il numero PCN. Il collegamento univoco nel messaggio di posta elettronica è l'elemento che consente l'accesso al portale di amministrazione delle sottoscrizioni di Visual Studio. Sarà quindi possibile accedere e gestire le sottoscrizioni.
> [!div class="mx-imgBorder"]
> ![Screenshot della notifica di operazione riuscita](_img/post-migration-onboarding/email-success.png)

## <a name="primary-contact-did-not-provide-you-administrator-access"></a>Il contatto principale non ha fornito all'utente l'accesso come amministratore

Se il contatto principale ha completato il processo di onboarding e le credenziali dell'utente erano presenti in VLSC in precedenza, ma il contatto non ha fornito all'utente l'accesso, viene visualizzata la notifica seguente. Per diventare un amministratore, contattare uno degli amministratori con privilegi avanzati dell'organizzazione, elencati nella notifica.
> [!div class="mx-imgBorder"]
> ![Screenshot del portale di amministrazione delle sottoscrizioni di Visual Studio con un elenco degli amministratori con privilegi avanzati](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>Le credenziali dell'utente non erano incluse in VLSC prima della migrazione

Se il contatto principale ha completato il processo di onboarding ma non ha aggiunto l'utente e le sue credenziali non erano presenti in VLSC in precedenza, viene visualizzata la notifica seguente. Rivolgersi al [contatto principale](find-primary-contact.md) per ottenere l'accesso al portale.
> [!div class="mx-imgBorder"]
> ![Screenshot del portale di amministrazione delle sottoscrizioni di Visual Studio con una notifica che indica che non è possibile trovare l'utente](_img/post-migration-onboarding/cant-find-you.png)