---
title: Ricerca per categorie i sottoscrittori in blocco?
description: L'amministratore o l'amministratore con privilegi più importanti desiderano altri dettagli su come usare la funzionalità in blocco.
ms.topic: include
ms.assetid: 3b450a79-47d2-4434-899d-bea29a0271e1
author: CaityBuschlen
ms.author: cabuschl
ms.date: 06/01/2021
user.type: admin
tags: bulk
subscription.type: vl, cloud, retail, partner
sap.id: b84fffb5-3363-eb7d-224e-1c63faf4067b
ms.openlocfilehash: d837b52d57a212f7519adfbc027eadbcf5f45dab
ms.sourcegitcommit: 364e106fcbf4fb6af534e81d8b700901f79f4ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2021
ms.locfileid: "129013242"
---
## <a name="how-do-i-assign-subscribers-in-bulk"></a>Ricerca per categorie i sottoscrittori in blocco?

Sono disponibili due opzioni per l'assegnazione in blocco dei sottoscrittori.
- È possibile [eseguire il caricamento bulk usando un Excel .](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-bulk-add-to-assign-subscriptions)
- Se l'organizzazione ha un tipo di contratto in grado di assegnare sottoscrizioni, è possibile usare Azure Active Directory [(Azure AD) di gruppo](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions).

## <a name="use-bulk-upload"></a>Usare il caricamento in blocco
1. Assicurarsi che il contratto che deve essere aggiornato sia selezionato nel menu a discesa del contratto.
2. Selezionare **Aggiungi** e quindi scegliere **Modifica in blocco nel** menu a discesa. Seguire le istruzioni nella finestra popup.
3. Dopo aver esportato il Excel, apportare le modifiche necessarie nel file, quindi salvare e caricare il file. Quando si apportano modifiche, tenere presente che i GUID non possono essere modificati.
4. Selezionare **OK** per avviare la modifica in blocco.

Se il modello contiene errori, il caricamento non riesce. Vengono visualizzati gli errori, quindi è possibile correggere il modello e riprovare.

## <a name="use-azure-ad-groups"></a>Usare Azure AD gruppi
L Azure AD per il caricamento bulk è attualmente disponibile solo per le organizzazioni con contratti che possono essere overclaim.
1. Assicurarsi che il contratto che deve essere aggiornato sia selezionato nel menu a discesa del contratto.
2. Selezionare **Aggiungi,** quindi scegliere Azure Active Directory **gruppo** dal menu a discesa.
3. Immettere il nome del Azure AD che si desidera aggiungere nel campo del modulo. Quando si digita il nome, la ricerca viene aggiornata per visualizzare i gruppi Azure AD all'interno dell'organizzazione.
4. Quando si seleziona il gruppo, il campo viene popolato automaticamente con il nome del gruppo. È possibile visualizzare gli utenti in tale gruppo prima di apportare modifiche.
5. Selezionare **Aggiungi** e quindi **Conferma.**
6. A tutti gli utenti futuri aggiunti al gruppo Azure AD viene automaticamente data una sottoscrizione. La sottoscrizione di tutti gli utenti rimossi dal gruppo è stata rimossa.