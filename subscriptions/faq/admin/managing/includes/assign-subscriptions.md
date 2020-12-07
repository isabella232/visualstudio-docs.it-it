---
title: Qual è la procedura per assegnare le sottoscrizioni di Visual Studio?
description: È possibile assegnare le sottoscrizioni agli utenti finali una alla volta oppure usare la funzionalità di aggiunta in blocco per caricare in modo rapido e semplice...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 12/03/2020
ms.openlocfilehash: 5a12d59f90ee2a09002efcb99c78cfd563060006
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96584545"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Qual è la procedura per assegnare le sottoscrizioni di Visual Studio?

È possibile assegnare le sottoscrizioni agli utenti finali una alla volta oppure usare la funzionalità di aggiunta in blocco per caricare in modo rapido e semplice un numero maggiore di sottoscrittori alla volta.

Per assegnare le sottoscrizioni singolarmente:

1. Selezionare la scheda [Gestisci sottoscrittori](https://manage.visualstudio.com/subscribers) nella parte superiore della pagina in [manage.visualstudio.com](https://manage.visualstudio.com)
2. Selezionare Aggiungi e digitare il nome e l'indirizzo di posta elettronica dell'utente a cui si vuole assegnare una sottoscrizione.
    1. Se l'organizzazione usa Azure Active Directory, nel campo del nome verrà eseguita una ricerca per trovare gli utenti nella directory corrente. È possibile effettuare una selezione dai risultati della ricerca o aggiungere manualmente un utente.
3. Se si vuole che il sottoscrittore possa accedere ai download software quando accede al [portale delle sottoscrizioni di Visual Studio](https://my.visualstudio.com/), assicurarsi di lasciare selezionata la casella di attivazione/disattivazione dei download nella sezione delle impostazioni di download.
4. Completare la sezione Preferenze di comunicazione in modo che Microsoft sappia quale lingua usare per inviare il messaggio di posta elettronica di assegnazione dei sottoscrittori.
5. Per aggiungere note associate all'assegnazione, usare la selezione Riferimento.
6. Selezionare Aggiungi nella parte inferiore del pannello a comparsa per completare l'assegnazione della sottoscrizione. Il sottoscrittore riceverà un messaggio di posta elettronica e potrà iniziare a usare immediatamente la sottoscrizione di Visual Studio (non è richiesta alcuna attivazione da parte del sottoscrittore).

Per assegnare le sottoscrizioni in blocco:

1. Selezionare la scheda [Gestisci sottoscrittori](https://manage.visualstudio.com/subscribers) nella parte superiore della pagina in [manage.visualstudio.com](https://manage.visualstudio.com).
2. Selezionare Aggiungi in blocco, scaricare il modello di Excel e salvare una copia locale.
3. Tutti i campi sono obbligatori, ad eccezione del campo Riferimento.
    1. Verificare che nessuno dei campi modulo contenga virgole.
    2. Rimuovere gli spazi prima e dopo i campi del modulo.
    3. Assicurarsi che i nomi in due parti non contengano spazi aggiuntivi tra il nome e il secondo nome (se il nome è composto da due parti, ad esempio 'Maria Giovanna', digitare 'MariaGiovanna').
4. Tornare a [manage.visualstudio.com](https://manage.visualstudio.com), selezionare Aggiungi in blocco e caricare la copia salvata del modello di Excel.
5. Quando il caricamento ha esito positivo verrà visualizzata una pagina di conferma e l'elenco dei sottoscrittori sarà aggiornato con i nuovi. I sottoscrittori riceveranno un messaggio di posta elettronica e potranno iniziare a usare immediatamente la sottoscrizione di Visual Studio (non è richiesta alcuna attivazione da parte del sottoscrittore).

Per scoprire come assegnare le sottoscrizioni in modo rapido e semplice, [vedere altre informazioni](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) sull'assegnazione delle sottoscrizioni nel portale di amministrazione di Sottoscrizioni di Visual Studio.  [Altre informazioni](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) sulla gestione delle sottoscrizioni di Visual Studio con GitHub Enterprise. 

## <a name="what-is-the-github-enterprise-setup-process"></a>Come funziona il processo di configurazione di GitHub Enterprise? 

GitHub Enterprise viene configurato e gestito separatamente dalle sottoscrizioni di Visual Studio. Dopo l'acquisto di una sottoscrizione di Visual Studio con GitHub Enterprise viene avviato il processo di configurazione dell'account di GitHub Enterprise parallelamente (ma separatamente) alla sottoscrizione di un contratto in manage.visualstudio.com. La creazione di questo account di GitHub Enterprise può richiedere del tempo.  

Dopo che l'azienda ha configurato un account di GitHub Enterprise, i sottoscrittori a cui sono state assegnate sottoscrizioni di Visual Studio con GitHub Enterprise riceveranno un messaggio di posta elettronica da GitHub che informa che le sottoscrizioni di Visual Studio sono state collegate. Quando i sottoscrittori ricevono questo messaggio di posta elettronica, possono rivolgersi all'amministratore dell'organizzazione di GitHub per ricevere un invito all'organizzazione appropriata. 

[Vedere altre informazioni](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) sulla gestione delle sottoscrizioni di Visual Studio con GitHub Enterprise. Per altri dettagli sul processo di configurazione di GitHub Enterprise, fare riferimento alla [documentazione per i sottoscrittori](https://docs.microsoft.com/visualstudio/subscriptions/access-github). 