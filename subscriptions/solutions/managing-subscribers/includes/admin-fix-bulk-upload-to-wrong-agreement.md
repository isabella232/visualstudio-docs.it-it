---
title: Risolvere i problemi di caricamento in blocco
description: L'amministratore con privilegi super o l'amministratore ha pensato di assegnare gli utenti al nuovo contratto, ma ha aggiunto gli utenti al contratto errato.
ms.topic: include
ms.assetid: 273f5f7a-739e-4de0-b7f7-d0bdd616e059
author: CaityBuschlen
ms.author: cabuschl
ms.date: 06/01/2021
user.type: admin
tags: bulk, upload
subscription.type: vl, cloud, retail, partner
sap.id: b84fffb5-3363-eb7d-224e-1c63faf4067b
ms.openlocfilehash: a8338378828ad9297004d1bf41ea77346405c39f
ms.sourcegitcommit: 364e106fcbf4fb6af534e81d8b700901f79f4ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2021
ms.locfileid: "129013247"
---
## <a name="how-do-i-fix-a-bulk-upload-to-use-the-correct-agreement"></a>Ricerca per categorie corretto un caricamento in blocco per usare il contratto corretto?

Se si carica in blocco per errore il contratto errato, seguire questa procedura per risolvere il problema.

Prima di tutto, assicurarsi di caricare i sottoscrittori nel contratto corretto e quindi eliminare i sottoscrittori dall'altro contratto. È possibile eliminare in blocco o risolvere il problema per un singolo utente tramite il portale di amministrazione.

## <a name="individual-users"></a>Singoli utenti

1. Nella pagina [Sottoscrittori del portale di](https://manage.visualstudio.com/subscribers)amministrazione trovare i sottoscrittori che è necessario rimuovere facendo clic sul nome della colonna e sull'ordinamento. È anche possibile usare l'opzione di filtro per trovare più facilmente gli utenti.
2. Dopo aver trovato i sottoscrittori da rimuovere, selezionare la casella di controllo accanto agli utenti. Non esiste alcun limite al numero di utenti che è possibile selezionare contemporaneamente. È anche possibile selezionare il primo utente in un elenco da rimuovere, quindi premere MAIUSC e infine selezionare l'ultimo utente nell'elenco. Questi passaggi selezionano tutti gli utenti nell'elenco. È anche possibile selezionare l'icona del segno di spunta nella parte superiore dell'elenco per selezionare tutti gli utenti. 
3. Selezionare **Elimina** nella parte superiore della griglia e quindi confermare l'eliminazione.

## <a name="azure-active-directory-azure-ad-group"></a>Azure Active Directory (Azure AD)

Se gli utenti sono stati aggiunti tramite un gruppo Azure AD, è necessario rimuovere gli utenti direttamente Azure AD gruppo. Dopo la rimozione degli utenti dal gruppo, possono essere richieste fino a 24 ore prima che l'eliminazione sia visibile nel portale di amministrazione. 

## <a name="impact-of-moving-subscriptions"></a>Impatto dello spostamento delle sottoscrizioni

Quando i sottoscrittori vengono spostati in un nuovo contratto, ricevono un nuovo ID sottoscrizione. Questa modifica interrompe il collegamento con la sottoscrizione di Azure associata al vantaggio del credito Azure mensile. Quando il collegamento viene interrotto, la sottoscrizione di Azure precedente è soggetta a disattivazione finale. Per evitare interruzioni, i sottoscrittori devono creare una nuova sottoscrizione di Azure usando il vantaggio nella nuova sottoscrizione di Visual Studio e quindi trasferire eventuali asset di Azure esistenti dalla sottoscrizione di [Azure](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription) precedente a quella nuova.