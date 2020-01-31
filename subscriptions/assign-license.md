---
title: Assegnare licenze a sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Informazioni su come gli amministratori possono assegnare licenze ai sottoscrittori
ms.openlocfilehash: 4ebec96f488a480ccd9b96387f2656aadd6ba2f9
ms.sourcegitcommit: 6375001ab26786af8d4d449f5846f8a49779ed18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2020
ms.locfileid: "76892181"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Assegnare licenze nel portale di amministrazione delle sottoscrizioni di Visual Studio
In qualità di amministratore delle sottoscrizioni di Visual Studio, è possibile usare il portale di amministrazione per assegnare sottoscrizioni a singoli utenti e gruppi di utenti.

Per i gruppi di utenti, è possibile assegnare le sottoscrizioni una alla volta oppure usare la funzionalità [Aggiungi in blocco](assign-license-bulk.md) per caricare in modo semplice e rapido elenchi di sottoscrittori e le relative informazioni di sottoscrizione.

## <a name="add-a-single-subscriber"></a>Aggiungere un singolo sottoscrittore
Di seguito viene descritto come assegnare una licenza di sottoscrizione di Visual Studio a un nuovo utente in modo che possa accedere ai vantaggi offerti dalla sottoscrizione.

1. Accedere al [portale di amministrazione](https://manage.visualstudio.com).
2. Per assegnare una licenza a un singolo sottoscrittore di Visual Studio, nella parte superiore della tabella selezionare **Aggiungi**.
   > [!div class="mx-imgBorder"]
   > ![Aggiungere un singolo sottoscrittore](media/add-single-subscriber.png)
3. Immettere le informazioni nei campi del modulo per il nuovo sottoscrittore. Se l'organizzazione usa Azure Active Directory, il campo **Nome** funge da funzione di ricerca per trovare le persone nella directory corrente, in modo da selezionare l'utente corretto nei risultati della ricerca. Dopo aver selezionato la persona, vengono inseriti automaticamente il nome, l'indirizzo di posta elettronica di accesso e l'indirizzo di posta elettronica di notifica.
   > [!div class="mx-imgBorder"]
   > ![Dettagli sul sottoscrittore](_img/assign-license-add/subscriber-details.png)

    Se si vuole che il sottoscrittore possa accedere ai download software quando accede al [portale delle sottoscrizioni di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), assicurarsi di lasciare selezionata la casella di attivazione/disattivazione dei download nella sezione delle **impostazioni di download**. Se si sceglie di disattivare i download, l'utente non avrà accesso ai download del software, ma potrà comunque accedere a tutti gli altri vantaggi inclusi nella sottoscrizione.
   > [!div class="mx-imgBorder"]
   > ![Accedere ai download](media/access-to-downloads.png)

    Se si vuole aggiungere le proprie note di riferimento alla sottoscrizione, è possibile aggiungerle nella sezione **Aggiungi riferimento**.
   > [!div class="mx-imgBorder"]
   > ![Aggiungere le proprie note di riferimento a ogni sottoscrizione](media/add-subscriber-reference-notes.png)

    Dopo aver selezionato le opzioni e aver immesso i dati per il sottoscrittore, scegliere **Aggiungi** nella parte inferiore di **Aggiungi sottoscrittore**.
   > [!div class="mx-imgBorder"]
   > ![Scegliere il pulsante Aggiungi](media/add-button.png)

## <a name="resend-assignment-emails"></a>Invia nuovamente i messaggi di posta elettronica di assegnazione
Dopo l'aggiunta di un Sottoscrittore, un messaggio di posta elettronica di assegnazione verrà inviato automaticamente al nuovo Sottoscrittore con ulteriori istruzioni. È possibile inviare di nuovo il messaggio di posta elettronica di assegnazione in qualsiasi momento selezionando il Sottoscrittore e facendo clic sul pulsante **Invia** di nuovo nel menu in alto.  Per inviare di nuovo i messaggi di posta elettronica a più utenti, tenere premuto il tasto **CTRL** mentre si selezionano i sottoscrittori.  Quando si fa clic sul pulsante **Invia** di nuovo, viene visualizzata una finestra di dialogo in cui viene chiesto di confermare che si desidera inviare nuovamente a tali Sottoscrittori.  

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere molti utenti,  vedere le informazioni su come assegnare sottoscrizioni a [più sottoscrittori](assign-license-bulk.md).
- Per ulteriori informazioni, vedere  Contattare il [supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).

