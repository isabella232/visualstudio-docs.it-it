---
title: Assegnare Visual Studio sottoscrizioni con GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: Gestione delle sottoscrizioni nelle Visual Studio con GitHub Enterprise
ms.openlocfilehash: c174b9beb7a7a0eec6bdb65e684869bc0be7dadb
ms.sourcegitcommit: 8da735b586276c95bf566a867655e3464ab1f989
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2021
ms.locfileid: "109740664"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Gestire le sottoscrizioni di Visual Studio con GitHub Enterprise
I clienti che hanno contratti Enterprise (EA) con Microsoft sono idonei per l'acquisto di una nuova offerta di sottoscrizione che riunisce Visual Studio sottoscrizioni standard e GitHub Enterprise. Per i sottoscrittori di Visual Studio, si tratta di un modo semplice ed economico per acquisire GitHub Enterprise. 

Quando l'organizzazione acquista Visual Studio sottoscrizioni con GitHub Enterprise, ne viene eseguito il provisioning e la gestione in due parti.

## <a name="manage-visual-studio-subscriptions"></a>Gestire le sottoscrizioni di Visual Studio
Quando l'organizzazione acquista Visual Studio sottoscrizioni con GitHub Enterprise, viene effettuato immediatamente il provisioning della parte Visual Studio delle sottoscrizioni e le sottoscrizioni sono [](https://manage.visualstudio.com) disponibili per l'assegnazione e la gestione nel portale di amministrazione delle sottoscrizioni Visual Studio. Dopo aver assegnato una sottoscrizione Visual Studio con GitHub Enterprise, il sottoscrittore riceverà un messaggio di posta elettronica che informa che può accedere alla sottoscrizione Visual Studio all'indirizzo <https://my.visualstudio.com/subscriptions> .

Per altre informazioni sulla gestione delle Visual Studio, vedere questi argomenti:
- [Uso del portale di amministrazione](using-admin-portal.md)
- [Assegnare sottoscrizioni](assign-license.md)
- [Modificare le sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Sovrassegnazioni](handle-overclaimed-license.md)

> [!Important]
> Se Visual Studio sottoscrizioni con GitHub Enterprise vengono assegnate dagli amministratori della sottoscrizione Visual Studio senza prima acquistare, GitHub non riceverà una notifica che indica che si vuole creare un account GitHub Enterprise locale.  **Acquisto di almeno uno** Visual Studio sottoscrizione con GitHub Enterprise deve essere effettuata prima dell'assegnazione delle sottoscrizioni.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>Spostamento in Visual Studio con GitHub Enterprise
Se l'organizzazione acquista sottoscrizioni Visual Studio con bundle GitHub Enterprise dopo l'assegnazione delle sottoscrizioni Visual Studio Enterprise e Visual Studio Professional standard, il portale di amministrazione contiene una funzionalità che consente di spostare i sottoscrittori esistenti nel Visual Studio Enterprise corrispondente con GitHub Enterprise e/o Visual Studio Professional con sottoscrizioni GitHub Enterprise.  Ad esempio, i sottoscrittori con Visual Studio Professional sottoscrizioni verranno spostati in Visual Studio Professional con GitHub Enterprise sottoscrizioni. Nel pannello "Panoramica" della barra a sinistra verrà visualizzato il riquadro seguente:

   > [!div class="mx-imgBorder"]
   > ![Pulsante Sposta ora](_img/assign-github/move-now.png "Fare clic su &quot;Sposta adesso&quot; per aggiornare le sottoscrizioni Visual Studio con GitHub Enterprise sottoscrizioni")

> [!IMPORTANT]
> Come accennato in precedenza, i dati del sottoscrittore esistenti, la cronologia e l'ID sottoscrizione verranno mantenuti e tutti i vantaggi attivati non verranno interrotti a causa di questo spostamento.  


Quando si fa clic **sul pulsante Sposta** ora, un pannello a comparsa presenta raccomandazioni sullo spostamento delle sottoscrizioni Enterprise e/o Professional:

   > [!div class="mx-imgBorder"]
   > ![Riquadro a comparsa](_img/assign-github/fly-out.png)

In questo riquadro è possibile esaminare i sottoscrittori che hanno subito l'impatto e specificare se si vuole inviare una notifica tramite posta elettronica al termine dello spostamento.  Questo messaggio di posta elettronica informa i sottoscrittori che i vantaggi rimangono invariati e li invita a iniziare a configurare una presenza in GitHub.  

Facendo clic **sul pulsante Sposta sottoscrittori** è possibile spostare tutti i sottoscrittori consigliati o scegliere singoli utenti   da un elenco.  Dopo aver confermato le selezioni, il completamento dello spostamento della sottoscrizione potrebbe richiedere alcuni secondi. Se applicabile, è necessario eseguire questi passaggi separatamente per Professional ed Enterprise.  

## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>Come funziona il processo di configurazione di Visual Studio con GitHub Enterprise?
GitHub Enterprise viene configurato e gestito separatamente dalle sottoscrizioni di Visual Studio. Dopo una sottoscrizione Visual Studio con acquisto GitHub Enterprise, un processo di configurazione dell'account GitHub Enterprise viene avviato in parallelo con (ma separatamente) con la definizione di un contratto [in manage.visualstudio.com](https://manage.visualstudio.com). La creazione di questo account di GitHub Enterprise può richiedere del tempo. 

Dopo che l'azienda ha configurato un account di GitHub Enterprise, i sottoscrittori a cui sono state assegnate sottoscrizioni di Visual Studio con GitHub Enterprise riceveranno un messaggio di posta elettronica da GitHub che informa che le sottoscrizioni di Visual Studio sono state collegate. Dopo aver ricevuto questo messaggio di posta elettronica, i sottoscrittori possono contattare l'amministratore dell'organizzazione GitHub per ricevere un invito all'organizzazione appropriata.

Per informazioni dettagliate sulla GitHub Enterprise, fare riferimento alla documentazione [del sottoscrittore](access-github.md).   

## <a name="manage-github-enterprise-subscriptions"></a>Gestire le sottoscrizioni di GitHub Enterprise
Quando GitHub Enterprise vengono acquistate sottoscrizioni, GitHub collabora con i clienti per creare e configurare le organizzazioni che accederanno a GitHub e identificheranno gli amministratori.  Gli amministratori ricevono quindi una notifica che indica che sono stati impostati come amministratori.  

Poiché questo processo è più complesso, potrebbero essere necessario diversi giorni dopo l'acquisto delle sottoscrizioni per la configurazione completa delle organizzazioni e degli amministratori.

GitHub è disponibile come GitHub.com basato su cloud o in versione locale come GitHub Enterprise Server.  I processi per la gestione delle due versioni variano.  GitHub offre vari argomenti della Guida e guide di amministrazione che consentono di gestire GitHub Enterprise sottoscrizioni.  Segue un elenco di collegamenti ad argomenti selezionati.  

## <a name="support-resources"></a>Risorse di supporto
- Altre informazioni sull'assegnazione di GitHub in [GitHub Docs](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle)
- Per risposte a domande su un'ampia gamma di argomenti di GitHub, vedere [la Guida di GitHub.](https://help.github.com/en)
- Ottenere assistenza da altri utenti di GitHub nel [GitHub Community Forum](https://github.community/) (forum della Community GitHub).
- Per assistenza per l'amministrazione di Sottoscrizioni di Visual Studio, contattare il [supporto Visual Studio sottoscrizioni.](https://aka.ms/vsadminhelp)
- Per domande sull'IDE di Visual Studio, Azure DevOps Services o altri prodotti e servizi Visual Studio,  Visitare [Visual Studio Supporto tecnico](https://visualstudio.microsoft.com/support/).
- Ottenere [supporto tecnico](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) per GitHub Enterprise.   

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione Visual Studio sottoscrizioni.
- [Assegnare singole sottoscrizioni](assign-license.md)
- [Assegnare più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)

Per altre informazioni sulla gestione delle Visual Studio con GitHub Enterprise, vedere il portale Visual Studio [di amministrazione delle sottoscrizioni.](https://visualstudio.microsoft.com/subscriptions-administration/)