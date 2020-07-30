---
title: Eliminare assegnazioni di sottoscrizioni nel portale di amministrazione delle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 06/16/2020
ms.topic: how-to
description: Informazioni su come gli amministratori possono eliminare le assegnazioni di sottoscrizione
ms.openlocfilehash: 4f952f574132afbd405c82c75fcddfc952bffb48
ms.sourcegitcommit: b8ce85a6d9c7fcceaad0fba625202f5ecf8f368c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2020
ms.locfileid: "87434269"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Eliminare assegnazioni nelle sottoscrizioni di Visual Studio
Quando un sottoscrittore non ha più necessità di usare una sottoscrizione di Visual Studio, ad esempio quando lascia l'azienda, completa un progetto o passa a un nuovo incarico, è possibile rimuovere la sua sottoscrizione e assegnarla a un altro utente. Si noti che quando si riassegna una sottoscrizione, non tutti i vantaggi del Sottoscrittore verranno reimpostati.  Il nuovo utente sarà in grado di richiedere le chiavi non richieste e di visualizzare le chiavi richieste in precedenza, ma i limiti di attestazione **non** vengono reimpostati.  Per le organizzazioni che hanno in essere contratti Enterprise, gli eventuali vantaggi usati dall'utente originale, ad esempio corsi Pluralsight, verranno reimpostati. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Eliminare un'assegnazione di sottoscrizione
1. Fare clic sul nome del sottoscrittore che si desidera rimuovere. Per selezionare più sottoscrittori per la rimozione, è possibile fare clic sul cerchio a sinistra del nome del Sottoscrittore per selezionarne uno.  In alternativa, è possibile tenere premuto il tasto **CTRL** e fare clic su ogni Sottoscrittore che si desidera rimuovere. Per rimuovere un intervallo di sottoscrittori, fare clic sul primo, premere il tasto **MAIUSC** e fare clic sull'ultimo.  Premere **CTRL + a** per selezionare e rimuovere tutti i sottoscrittori. 
2. Per eliminare i sottoscrittori selezionati, fare clic su **Elimina**.
3. Quando viene visualizzato il messaggio che chiede di confermare l'eliminazione, fare clic su **OK**.
   > [!div class="mx-imgBorder"]
   > ![Eliminare i sottoscrittori](_img/delete-license/delete-subscribers.png "Scegliere gli utenti che si desidera eliminare e fare clic su Elimina. È possibile utilizzare i tasti CTRL e MAIUSC per selezionare più Sottoscrittori.")

   > [!NOTE]
   > L'eliminazione bulk tramite un modello non è disponibile. Per le organizzazioni che gestiscono le assegnazioni delle sottoscrizioni tramite Azure Active Directory gruppi di sicurezza, vedere [l'articolo](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) per altre informazioni sul modo in cui si verificano le eliminazioni.  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario modificare una sottoscrizione senza eliminarla,  vedere [Modificare una sottoscrizione](edit-license.md)
- Per informazioni sull'individuazione di una sottoscrizione specifica, vedere [Cercare una sottoscrizione](search-license.md).
- Per creare un elenco di tutte le sottoscrizioni,  vedere [Esportare sottoscrizioni](exporting-subscriptions.md)


