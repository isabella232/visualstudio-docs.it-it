---
title: Eliminare le assegnazioni di sottoscrizione di Visual Studio nel portale di amministrazione delle sottoscrizioni | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 02/18/2021
ms.topic: how-to
description: Informazioni su come gli amministratori possono eliminare le assegnazioni delle sottoscrizioni nel portale di amministrazione delle sottoscrizioni di Visual Studio
ms.openlocfilehash: efd0e149f390dd21a286b6ab7405ec36a43b8f78
ms.sourcegitcommit: 9da787bf5b4281f933dc22083dc0bdeae3bc9461
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2021
ms.locfileid: "103225976"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Eliminare assegnazioni nelle sottoscrizioni di Visual Studio
Quando un Sottoscrittore non richiede più una sottoscrizione di Visual Studio, ad esempio quando lascia l'azienda, completa un progetto o passa a un nuovo ruolo di lavoro, è possibile rimuovere la sottoscrizione e assegnarla a un altro utente. Si noti che quando si riassegna una sottoscrizione, non tutti i vantaggi del Sottoscrittore verranno reimpostati.  Il nuovo utente sarà in grado di richiedere le chiavi non richieste e di visualizzare le chiavi richieste in precedenza, ma i limiti di attestazione **non** vengono reimpostati.  Per le organizzazioni che hanno in essere contratti Enterprise, gli eventuali vantaggi usati dall'utente originale, ad esempio corsi Pluralsight, verranno reimpostati. 
> [!Important]
> Le sottoscrizioni possono essere assegnate a utenti diversi solo se sono trascorsi almeno 90 giorni dall'ultima assegnazione della sottoscrizione.  Se ad esempio una sottoscrizione è stata assegnata a un Sottoscrittore il 1 ° giugno, non può essere assegnata a un nuovo Sottoscrittore fino al 30 agosto. 

Guardare questo video o leggere per informazioni su come eliminare le assegnazioni.  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Eliminare un'assegnazione di sottoscrizione
1. Fare clic sul nome del sottoscrittore che si desidera rimuovere. Per selezionare più sottoscrittori per la rimozione, è possibile fare clic sul cerchio a sinistra del nome del Sottoscrittore per selezionarne uno.  In alternativa, è possibile tenere premuto il tasto **CTRL** e fare clic su ogni Sottoscrittore che si desidera rimuovere. Per rimuovere un intervallo di sottoscrittori, fare clic sul primo, premere il tasto **MAIUSC** e fare clic sull'ultimo.  Premere **CTRL + a** per selezionare e rimuovere tutti i sottoscrittori. In questo esempio vengono eliminati tre sottoscrittori: Amber, Kai e Madison. 
2. Per eliminare i sottoscrittori selezionati, fare clic su **Elimina**.
3. Quando viene visualizzato il messaggio che chiede di confermare l'eliminazione, fare clic su **OK**.
   > [!div class="mx-imgBorder"]
   > ![Eliminare i sottoscrittori](_img/delete-license/delete-subscribers.png "Scegliere gli utenti che si desidera eliminare e fare clic su Elimina. È possibile utilizzare i tasti CTRL e MAIUSC per selezionare più Sottoscrittori.")

   > [!NOTE]
   > L'eliminazione bulk tramite un modello non è disponibile. 
   >
   > Se sono state aggiunte assegnazioni di sottoscrizione tramite Azure Active Directory gruppi di sicurezza, potrebbero essere necessarie fino a 24 ore prima che l'eliminazione venga aggiornata nel portale di amministrazione.  Per ulteriori informazioni sull'utilizzo di gruppi di Azure Active Directory per gestire le sottoscrizioni, vedere [l'articolo](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) . 

## <a name="resources"></a>Risorse
- [Supporto delle sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="see-also"></a>Vedi anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario modificare una sottoscrizione senza eliminarla,  vedere [Modificare una sottoscrizione](edit-license.md)
- Per informazioni sull'individuazione di una sottoscrizione specifica, vedere [Cercare una sottoscrizione](search-license.md).
- Per creare un elenco di tutte le sottoscrizioni,  vedere [Esportare sottoscrizioni](exporting-subscriptions.md)