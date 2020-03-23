---
title: Eliminare assegnazioni di sottoscrizioni nel portale di amministrazione delle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Informazioni su come gli amministratori possono eliminare le assegnazioni di sottoscrizione
ms.openlocfilehash: 6ed64f5c05f77bea7f157eee9e29bbb05aa8730d
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "78263246"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Eliminare assegnazioni nelle sottoscrizioni di Visual Studio
Quando un sottoscrittore non ha più necessità di usare una sottoscrizione di Visual Studio, ad esempio quando lascia l'azienda, completa un progetto o passa a un nuovo incarico, è possibile rimuovere la sua sottoscrizione e assegnarla a un altro utente. Si prega di notare che quando si riassegna un abbonamento, non tutti i vantaggi per gli abbonati verranno reimpostati.  Il nuovo utente sarà in grado di richiedere le chiavi non richieste e di visualizzare le chiavi richieste in precedenza, ma i limiti di attestazione **non** vengono reimpostati.  Per le organizzazioni che hanno in essere contratti Enterprise, gli eventuali vantaggi usati dall'utente originale, ad esempio corsi Pluralsight, verranno reimpostati. 

## <a name="delete-a-subscription-assignment"></a>Eliminare un'assegnazione di sottoscrizioneDelete a subscription assignment
1. Fare clic sul nome del sottoscrittore che si desidera rimuovere. Per selezionare più sottoscrittori per la rimozione, è possibile fare clic sul cerchio a sinistra del nome dell'abbonato per selezionarli.  In alternativa, è possibile tenere premuto il tasto **CTRL** e fare clic su ogni sottoscrittore che si desidera rimuovere.  Premere **CTRL e A** per selezionare e rimuovere tutti i sottoscrittori. 
2. Per eliminare i sottoscrittori selezionati, fare clic su **Elimina**.
3. Quando viene visualizzato il messaggio che chiede di confermare l'eliminazione, fare clic su **OK**.
   > [!div class="mx-imgBorder"]
   > ![Eliminare i sottoscrittori](_img/delete-license/delete-subscribers.png)

   > [!NOTE]
   > L'eliminazione in blocco tramite un modello non è disponibile. Per le organizzazioni che gestiscono le assegnazioni di sottoscrizione tramite i gruppi di sicurezza di Azure Active Directory, vedere [l'articolo](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) per altre informazioni su come si verificano le eliminazioni.  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario modificare una sottoscrizione senza eliminarla,  vedere [Modificare una sottoscrizione](edit-license.md)
- Per informazioni sull'individuazione di una sottoscrizione specifica, vedere [Cercare una sottoscrizione](search-license.md).
- Per creare un elenco di tutte le sottoscrizioni,  vedere [Esportare sottoscrizioni](exporting-subscriptions.md)


