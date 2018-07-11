---
title: Assegnare licenze alle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Informazioni su come gli amministratori possono assegnare licenze ai sottoscrittori
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: d0dbd509d60ed3528186e41c98f374ab6db60fa3
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "36327024"
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Assegnazione di licenze nel portale di amministrazione delle sottoscrizioni di Visual Studio

Come amministratore di sottoscrizioni di Visual Studio, è possibile usare il portale per gli amministratori delle sottoscrizioni di Visual Studio per assegnare le sottoscrizioni a singoli utenti.  
È possibile assegnare le sottoscrizioni una alla volta oppure usare la funzionalità di aggiunta in blocco per caricare elenchi di sottoscrittori con le relative informazioni di sottoscrizione in modo semplice e rapido. 

## <a name="assigning-a-single-user"></a>Assegnazione di un singolo utente
Se sono disponibili licenze per le sottoscrizioni di Visual Studio, è possibile assegnare queste licenze a nuovi utenti per consentire loro di accedere ai vantaggi delle sottoscrizioni. 
1.  Accedere al [portale per gli amministratori](https://manage.visualstudio.com)

2.  Per assegnare un singolo sottoscrittore di Visual Studio, nella parte superiore della tabella, fare clic su **Aggiungi**.
   
3.  Immettere le informazioni nei campi del modulo per il nuovo sottoscrittore. Se l'organizzazione usa Azure Active Directory, questo campo funge da funzione di ricerca per trovare i contatti nella directory corrente per poter selezionare l'utente corretto nei risultati della ricerca. Una volta selezionata la persona, vengono compilati automaticamente i campi relativi a nome, indirizzo di posta elettronica di accesso e per le notifiche, come visualizzato di seguito. 

    Se l'organizzazione non usa Azure Active Directory (Azure AD) ma ha un indirizzo di posta elettronica diverso per ricevere gli email rispetto a quello da utilizzare per l'accesso, l'utente ha la possibilità di indicarlo qui. Selezionare il collegamento ipertestuale "Add a different notification email for receiving communication" (Aggiungi un indirizzo di posta elettronica di notifica diverso per la ricezione delle comunicazioni). 

    **Accesso ai download:**  
    Se si vuole che il sottoscrittore possa accedere ai download software quando accede al [portale delle sottoscrizioni di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), assicurarsi di lasciare selezionata la casella di attivazione/disattivazione dei download. Se si sceglie di disattivare i download, l'utente non avrà accesso ai download del software, ma potrà comunque accedere a tutti gli altri vantaggi inclusi nella sottoscrizione. 
    
    Dopo aver scelto le opzioni per il sottoscrittore, fare clic su **Aggiungi**.

    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-1.png" style="border: 1px solid #CCCCCC" />
    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-2.png" style="border: 1px solid #CCCCCC" />

4.  Dopo aver aggiunto il sottoscrittore, viene inviato automaticamente al nuovo sottoscrittore un messaggio di posta elettronica di assegnazione, con altre istruzioni. È possibile inviare nuovamente il messaggio di posta elettronica di assegnazione in qualunque momento selezionando il sottoscrittore e facendo clic sul pulsante **Invia di nuovo** nel menu superiore.


## <a name="bulk-assignments"></a>Assegnazioni in blocco
1.  Per aggiungere contemporaneamente più sottoscrittori, passare alla scheda **Manage Subscribers** (Gestione sottoscrittori). Nella barra multifunzione in alto, fare clic su **Aggiungi in blocco**. 

2. L'assegnazione in blocco usa un modello di Microsoft Excel per caricare i sottoscrittori. Nella finestra di dialogo Upload Multiple Subscriber (Carica più sottoscrittori), fare clic su **Download** per scaricare il modello. Scaricare sempre la versione più recente del modello. Se si usa una versione precedente, il caricamento in blocco potrebbe non riuscire.

3.  Nel foglio di calcolo Excel, compilare i campi con le informazioni per gli utenti a cui si desidera assegnare le sottoscrizioni. Il riferimento è un campo facoltativo. Se una parte del modello è stata compilata in modo errato, si dovrebbe visualizzare un messaggio di errore che descrive il problema. Al termine, salvare il file in locale.
**Per garantire un caricamento senza errori, osservare le procedure consigliate seguenti:**
    - Verificare che nessuno dei campi modulo contenga virgole.
    - Rimuovere gli spazi prima e dopo i campi del modulo, ad esempio i nomi degli utenti.
    - Assicurarsi che i nomi degli utenti non contengano spazi aggiuntivi tra i nomi e cognomi composti da due parti (ad esempio il nome composto "Maria Giovanna" non deve essere digitato come "Maria  Giovanna" perché il sistema non annullerà lo spazio aggiuntivo).

4.  Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio e nella finestra di dialogo Upload Multiple Subscribers (Carica più sottoscrittori), fare clic su **Sfoglia**. Andare al file di Excel salvato e fare clic su **OK**. Lo stato di avanzamento del caricamento verrà visualizzato sullo schermo. 

    <img alt="Bulk add upload" src="_img\assign-license-add\bulk-assign-upload-2.png" style="border: 1px solid #CCCCCC" />

Se il modello contiene errori, il caricamento avrà esito negativo e verranno visualizzati gli errori in modo da poter correggere il modello e tentare nuovamente il caricamento in blocco.
    <img alt="Upload fail" src="_img\assign-license-add\bulk-assign-upload-fail.png" style="border: 1px solid #CCCCCC" />

Quando il caricamento ha esito positivo, viene visualizzato l'elenco di sottoscrittori e un messaggio di conferma.

