---
title: Assegnare licenze alle sottoscrizioni di Visual Studio | Microsoft Docs
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 07/16/2018
ms.topic: conceptual
description: Informazioni su come gli amministratori possono assegnare licenze ai sottoscrittori
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 5307f05d39ca751453e73147cc08115bf8b9dd1a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636795"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Assegnare licenze nel portale di amministrazione delle sottoscrizioni di Visual Studio

In qualità di amministratore delle sottoscrizioni di Visual Studio, è possibile usare il portale di amministrazione per assegnare le sottoscrizioni a singoli utenti e gruppi di utenti.

Per i gruppi di utenti, è possibile assegnare le sottoscrizioni una alla volta oppure usare la funzionalità **Aggiungi in blocco** per caricare in modo semplice e rapido elenchi di sottoscrittori e le relative informazioni di sottoscrizione.

## <a name="individual-assignments"></a>Assegnazioni singole

Di seguito viene descritto come assegnare una licenza di sottoscrizione di Visual Studio a un nuovo utente in modo che possa accedere ai vantaggi offerti dalla sottoscrizione.

1. Accedere al [portale di amministrazione](https://manage.visualstudio.com).

2. Per assegnare una licenza a un singolo sottoscrittore di Visual Studio, nella parte superiore della tabella selezionare **Aggiungi**.
    > [!div class="mx-imgBorder"]
    > ![Aggiungere un singolo sottoscrittore](media\add-single-subscriber.png)

3. Immettere le informazioni nei campi del modulo per il nuovo sottoscrittore. Se l'organizzazione usa Azure Active Directory, questo campo funge da funzione di ricerca per trovare i contatti nella directory corrente per poter selezionare l'utente corretto nei risultati della ricerca. Dopo aver selezionato la persona, vengono inseriti automaticamente il nome, l'indirizzo di posta elettronica di accesso e il messaggio di posta elettronica di notifica.
    > [!div class="mx-imgBorder"]
    > ![Aggiungere un nuovo indirizzo di posta elettronica di notifica](media\add-new-subscriber-notification-email.png)

    Se si vuole che il sottoscrittore possa accedere ai download software quando accede al [portale delle sottoscrizioni di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), assicurarsi di lasciare selezionata la casella di attivazione/disattivazione dei download nella sezione delle **impostazioni di download**. Se si sceglie di disattivare i download, l'utente non avrà accesso ai download del software, ma potrà comunque accedere a tutti gli altri vantaggi inclusi nella sottoscrizione.
    > [!div class="mx-imgBorder"]
    > ![Accedere ai download](media\access-to-downloads.png)

    Se si vuole modificare la lingua delle informazioni inviate al sottoscrittore, è possibile modificarla nella sezione **Preferenze di comunicazione**.
    > [!div class="mx-imgBorder"]
    > ![Modificare la lingua usata per l'invio dei messaggi di posta elettronica di notifica](media\change-subscriber-communication-preference.png)

    Se si vuole aggiungere le proprie note di riferimento alla sottoscrizione, è possibile aggiungerle nella sezione **Aggiungi riferimento**.
    > [!div class="mx-imgBorder"]
    > ![Aggiungere le proprie note di riferimento a ogni sottoscrizione](media\add-subscriber-reference-notes.png) 

    Dopo aver selezionato le opzioni e aver immesso i dati per il sottoscrittore, scegliere **Aggiungi** nella parte inferiore di **Aggiungi sottoscrittore**.
    > [!div class="mx-imgBorder"]
    > ![Scegliere il pulsante Aggiungi](media\add-button.png)

4. Dopo aver aggiunto il sottoscrittore, viene inviato automaticamente al nuovo sottoscrittore un messaggio di posta elettronica di assegnazione con altre istruzioni. È possibile inviare nuovamente il messaggio di posta elettronica di assegnazione in qualunque momento selezionando il sottoscrittore e facendo clic sul pulsante **Invia di nuovo** nel menu superiore.
    > [!div class="mx-imgBorder"]
    > ![Inviare di nuovo il messaggio di attivazione a uno o più utenti in qualsiasi momento](media\resend-subscriber-activation-emails.png) 

## <a name="bulk-assignments"></a>Assegnazioni in blocco

1. Per aggiungere contemporaneamente più sottoscrittori, passare alla scheda **Manage Subscribers** (Gestione sottoscrittori). Nella barra multifunzione in alto, fare clic su **Aggiungi in blocco**.
    > [!div class="mx-imgBorder"]
    > ![Aggiungere più sottoscrittori](media\add-multiple-subscribers.png)

1. L'assegnazione in blocco usa un modello di Microsoft Excel per caricare i sottoscrittori. Nella finestra di dialogo Upload Multiple Subscriber (Carica più sottoscrittori), fare clic su **Download** per scaricare il modello.
    > [!div class="mx-imgBorder"]
    > ![Scaricare il modello di Excel per caricare più sottoscrittori](media\download-template-upload-subscribers.png)

    > [!NOTE]
    > Scaricare sempre la versione più recente del modello. Se si usa una versione precedente, il caricamento in blocco potrebbe non riuscire.

1. Nel foglio di calcolo Excel compilare i campi con le informazioni per gli utenti a cui si desidera assegnare le sottoscrizioni. *Riferimento* è un campo facoltativo. Al termine, salvare il file in locale.

  Per garantire un caricamento senza errori, osservare le procedure consigliate seguenti:

    - Verificare che nessuno dei campi modulo contenga virgole.
    - Rimuovere gli spazi prima e dopo i campi del modulo.
    - Assicurarsi che i nomi degli utenti non contengano spazi aggiuntivi nei nomi o cognomi composti da due parti (se il nome è composto da due parti, ad esempio "Maria Giovanna", digitare "MariaGiovanna" poiché il sistema non annulla lo spazio aggiuntivo).

1. Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio. Nella finestra di dialogo **Upload Multiple Subscribers** (Carica più sottoscrittori) fare clic su **Sfoglia**.
    > [!div class="mx-imgBorder"]
    > ![Passare al modello salvato per caricare più sottoscrittori](media\bulk-add-browse-saved-template.png)

1. Passare al file Excel salvato e quindi fare clic su **OK**.
    > [!div class="mx-imgBorder"]
    > ![Caricare il modello di Excel per caricare più sottoscrittori](media\bulk-upload-subscribers.png)

    Viene visualizzata una finestra di dialogo di avanzamento del caricamento.

    Se il modello contiene errori, il caricamento avrà esito negativo e verranno visualizzati gli errori per consentire di correggere il modello e tentare nuovamente il caricamento in blocco.
    > [!div class="mx-imgBorder"]
    > ![Messaggio di errore se il caricamento di più sottoscrittori ha esito negativo](media\bulk-add-template-failed.png)

    Quando il caricamento ha esito positivo, viene visualizzato l'elenco di sottoscrittori e un messaggio di conferma.
    > [!div class="mx-imgBorder"]
    > ![Messaggio di conferma se il caricamento di più sottoscrittori ha esito positivo](media\bulk-add-template-success.png)
