---
title: Esportare le informazioni sulla sottoscrizione Visual Studio sottoscrizioni| Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 14e4cffb-a695-436c-b269-7820f7411f4e
ms.date: 08/31/2021
ms.topic: conceptual
description: Informazioni su come esportare un elenco di sottoscrittori e i dettagli delle assegnazioni delle sottoscrizioni.
ms.openlocfilehash: 4df633618cb419c3bbd7a47d961385d131f73859
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123965503"
---
# <a name="export-subscription-information"></a>Esportare le informazioni sulla sottoscrizione
Nel portale Sottoscrizioni di Visual Studio [administration è](https://manage.visualstudio.com)possibile esportare un elenco dei sottoscrittori e i dettagli sulle relative assegnazioni. Queste informazioni includono nome, indirizzo di posta elettronica, indirizzo di posta elettronica alternativo, livello della sottoscrizione, data di assegnazione, stato di attivazione, data di scadenza, campo di riferimento, abilitazione o meno dei download, paese, lingua, stato della sottoscrizione e GUID della sottoscrizione.  L'elenco viene esportato come file CSV che può essere facilmente aperto in Microsoft Excel per la creazione di grafici, pivot e altri artefatti.

La presenza di tutte le informazioni sul sottoscrittore in un'unica posizione può essere utile per eseguire operazioni come:
- Ottenere una panoramica complessiva delle sottoscrizioni usate in base a team e/o posizione nell'intera organizzazione.
- Sviluppare piani e budget per i futuri acquisti di sottoscrizioni. 
- Invitare gli utenti cui sono assegnate sottoscrizioni a procedere all'attivazione.
- Intervenire in modo proattivo prima dello scadere delle sottoscrizioni.  
- Identificare la posizione in cui le sottoscrizioni possono essere sovraallocato. 
- Assegnare le sottoscrizioni usando l'ID sottoscrizione per controllare la data di scadenza dei sottoscrittori nelle sottoscrizioni. 

## <a name="export-your-subscriptions"></a>Esportare le sottoscrizioni
Per eseguire l'esportazione:
1. Accedere al [portale di amministrazione](https://manage.visualstudio.com).
2. Selezionare la scheda **Esporta** per scaricare il file nel computer locale. Il file include il nome del contratto che contiene le sottoscrizioni utente e la data dell'esportazione.
> [!div class="mx-imgBorder"]
> ![Esportare sottoscrittori](_img/exporting-subscriptions/exporting-subscriptions.png "Fare clic su Esporta per scaricare un elenco completo delle sottoscrizioni assegnate.")
3. L'elenco esportato verrà visualizzato nel percorso normale per i file scaricati nel computer in .csv formato di file. Il nome file includerà il numero di contratto e la data in cui è stato esportato l'elenco.  

## <a name="resources"></a>Risorse
- [Supporto delle sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Per altre informazioni sulla gestione delle sottoscrizioni, vedere questi utili argomenti:
    - [Sottoscrizioni scadute](handle-expired-license.md)
    - [Sovrassegnazioni](handle-overclaimed-license.md)
    - [Utilizzo massimo](maximum-usage.md)
