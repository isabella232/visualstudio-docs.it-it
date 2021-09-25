---
title: Eliminare Visual Studio di sottoscrizione nel portale di amministrazione delle sottoscrizioni | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 03/21/2021
ms.topic: how-to
description: Informazioni su come gli amministratori possono eliminare le assegnazioni di sottoscrizione nel portale Sottoscrizioni di Visual Studio amministrazione
ms.openlocfilehash: 6963d3b6f3cc478eaa80672499a28bf42d094264
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428071"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Eliminare assegnazioni nelle sottoscrizioni di Visual Studio
Quando un sottoscrittore non richiede più una sottoscrizione Visual Studio, ad esempio quando lascia l'azienda, completa un progetto o passa a un nuovo ruolo processo, è possibile rimuovere la sottoscrizione e assegnarla a un altro utente. Si noti che quando si riassegna una sottoscrizione, non tutti i vantaggi del sottoscrittore verranno reimpostati.  Il nuovo utente sarà in grado di richiedere le chiavi non richieste e di visualizzare le chiavi richieste in precedenza, ma i limiti di attestazione **non** vengono reimpostati.  Per le organizzazioni che hanno in essere contratti Enterprise, gli eventuali vantaggi usati dall'utente originale, ad esempio corsi Pluralsight, verranno reimpostati. 
> [!Important]
> Le sottoscrizioni possono essere assegnate a utenti diversi solo se sono trascorsi almeno 90 giorni dall'ultima assegnazione della sottoscrizione.  Ad esempio, se una sottoscrizione è stata assegnata a un sottoscrittore il 1° giugno, non può essere assegnata a un nuovo sottoscrittore almeno fino al 30 agosto. 

Guardare questo video o leggere per informazioni su come eliminare le assegnazioni.  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Eliminare un'assegnazione di sottoscrizione
1. Fare clic sul nome del sottoscrittore che si desidera rimuovere. Per selezionare più sottoscrittori per la rimozione, è possibile fare clic sul cerchio a sinistra del nome del sottoscrittore per selezionarli.  In alternativa, è possibile tenere premuto **CTRL** e fare clic su ogni sottoscrittore da rimuovere. Per rimuovere un intervallo di sottoscrittori, fare clic sul primo, premere **MAIUSC** e fare clic sull'ultimo.  Premere **CTRL+A** per selezionare e rimuovere tutti i sottoscrittori. In questo esempio verranno eliminati tre sottoscrittori, Amber, Kai e Madison. 
2. Per eliminare i sottoscrittori selezionati, fare clic su **Elimina**.
3. Quando viene visualizzato il messaggio che chiede di confermare l'eliminazione, fare clic su **OK**.
   > [!div class="mx-imgBorder"]
   > ![Eliminare i sottoscrittori](_img/delete-license/delete-subscribers.png "Scegliere gli utenti da eliminare e fare clic su Elimina. È possibile usare i tasti CTRL e MAIUSC per selezionare più sottoscrittori.")

   > [!NOTE]
   > L'eliminazione in blocco tramite un modello non è disponibile. 
   >
   > Se sono state aggiunte assegnazioni di sottoscrizione Azure Active Directory gruppi di sicurezza, l'aggiornamento dell'eliminazione nel portale di amministrazione potrebbe richiedere fino a 24 ore.  Per [altre informazioni sull'uso](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) dei gruppi di Azure Active Directory per gestire le sottoscrizioni, vedere l'articolo. 

## <a name="resources"></a>Risorse
- [Supporto delle sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario modificare una sottoscrizione senza eliminarla,  vedere [Modificare una sottoscrizione](edit-license.md)
- Per informazioni sull'individuazione di una sottoscrizione specifica, vedere [Cercare una sottoscrizione](search-license.md).
- Per creare un elenco di tutte le sottoscrizioni,  vedere [Esportare sottoscrizioni](exporting-subscriptions.md)