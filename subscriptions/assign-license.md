---
title: Assegnare Visual Studio sottoscrizioni agli utenti | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/21/2021
ms.topic: conceptual
description: Informazioni su come gli amministratori possono assegnare licenze ai sottoscrittori
ms.openlocfilehash: 91bb0a4c288915b14d0bd9354ef325d0c0b259be
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427597"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Assegnare licenze nel portale di amministrazione delle sottoscrizioni di Visual Studio
Come amministratore Visual Studio sottoscrizioni, è possibile usare il portale di amministrazione per assegnare sottoscrizioni a singoli utenti e gruppi di utenti.

Per i gruppi di utenti, è possibile scegliere come assegnare le sottoscrizioni.  
- È possibile assegnare le sottoscrizioni una alla volta.
- È anche possibile caricare in modo rapido e semplice elenchi di sottoscrittori e le relative informazioni di sottoscrizione usando la [funzionalità di aggiunta in](assign-license-bulk.md) blocco.
- Se l'organizzazione usa Microsoft Azure Active Directory (Azure AD), è possibile usare i gruppi Azure AD per [assegnare](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) sottoscrizioni a gruppi di utenti.  


## <a name="add-a-single-subscriber"></a>Aggiungere un singolo sottoscrittore
Guardare il video o leggere per informazioni su come assegnare una sottoscrizione Visual Studio a un nuovo utente in modo che possa accedere ai vantaggi della sottoscrizione.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Accedere al portale [di amministrazione.](https://manage.visualstudio.com)
2. Per assegnare una licenza a un singolo sottoscrittore Visual Studio, nella parte superiore della tabella selezionare **Aggiungi** e quindi scegliere **Sottoscrittore singolo.**
   > [!div class="mx-imgBorder"]
   > ![Aggiungere un singolo sottoscrittore](_img/assign-license-add/add-subscriber-individual.png "Selezionare Aggiungi e quindi scegliere Singolo sottoscrittore per assegnare una singola sottoscrizione.")
3. Immettere le informazioni nei campi del modulo per il nuovo sottoscrittore. Se l'organizzazione usa Azure Active Directory, il campo **Nome** funge da funzione di ricerca per trovare le persone nella directory corrente, in modo da selezionare l'utente corretto nei risultati della ricerca. Dopo aver selezionato la persona, vengono inseriti automaticamente il nome, l'indirizzo di posta elettronica di accesso e l'indirizzo di posta elettronica di notifica.  Se il sottoscrittore non viene trovato nell'organizzazione, il messaggio di posta elettronica di notifica non verrà popolato automaticamente, ma sarà disponibile per aggiungere manualmente un indirizzo di posta elettronica diverso a cui verranno inviati i messaggi di posta elettronica correlati alla sottoscrizione.  Se il servizio di posta elettronica blocca i messaggi di posta elettronica in arrivo agli indirizzi di posta elettronica di accesso, è importante specificare un indirizzo di posta elettronica di notifica diverso in modo che i sottoscrittori e gli amministratori ricevano importanti messaggi di posta elettronica relativi alla sottoscrizione da Microsoft.
   > [!div class="mx-imgBorder"]
   > ![Dettagli sul sottoscrittore](_img/assign-license-add/subscriber-details.png "Immettere il nome del sottoscrittore e altri dettagli oppure scegliere tra i membri del tenant.")

    > [!NOTE]
    > Perché i membri di un tenant Azure Active Directory siano visibili quando si immette il nome di un sottoscrittore, l'amministratore deve essere un membro del tenant. 


    Se si vuole che il sottoscrittore possa accedere ai download software quando accede al [portale delle sottoscrizioni di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), assicurarsi di lasciare selezionata la casella di attivazione/disattivazione dei download nella sezione delle **impostazioni di download**. Se si sceglie di disabilitare i download, l'utente non avrà accesso ai download del software.  Anche l'accesso ai codici Product Key verrà disabilitato.  Il sottoscrittore avrà comunque accesso a tutti gli altri vantaggi inclusi nella sottoscrizione.
   > [!div class="mx-imgBorder"]
   > ![Accedere ai download](media/access-to-downloads.png "Scegliere &quot;Consenti&quot; per fornire al sottoscrittore l'accesso ai download del software.")

    Se si vuole aggiungere le proprie note di riferimento alla sottoscrizione, è possibile aggiungerle nella sezione **Aggiungi riferimento**.
   > [!div class="mx-imgBorder"]
   > ![Aggiungere le proprie note di riferimento a ogni sottoscrizione](media/add-subscriber-reference-notes.png "Usare il campo Riferimento per registrare eventuali note sulla sottoscrizione.")

    Dopo aver selezionato le opzioni e aver immesso i dati per il sottoscrittore, scegliere **Aggiungi** nella parte inferiore di **Aggiungi sottoscrittore**.
   > [!div class="mx-imgBorder"]
   > ![Scegliere il pulsante Aggiungi](media/add-button.png "Selezionare Aggiungi per salvare le informazioni e assegnare la sottoscrizione al sottoscrittore.")

## <a name="why-use-a-different-notification-email-address"></a>Perché usare un indirizzo di posta elettronica di notifica diverso?
Alcune organizzazioni configurano i propri servizi di posta elettronica per bloccare i messaggi di posta elettronica in arrivo da altri domini.  Bloccando i messaggi di posta elettronica in arrivo, i sottoscrittori e gli amministratori non riceveranno comunicazioni importanti:
- I Sottoscrittori non riceveranno una notifica che indica che è stata loro assegnata una sottoscrizione.  Ciò impedirà anche l'attivazione di alcuni dei vantaggi inclusi.  
- I sottoscrittori a cui sono state assegnate sottoscrizioni Visual Studio con GitHub Enterprise non riceveranno l'invito a partecipare all'organizzazione GitHub, ovvero non potranno accettare l'invito. Devono **accettare l'invito inviato tramite posta** elettronica per ottenere l'accesso all'GitHub organizzazione. 
- Gli amministratori non riceveranno notifiche quando vengono aggiunti a un contratto, riceveranno istruzioni di amministrazione mensili o notifiche delle modifiche delle funzionalità che influiscono sul modo in cui gestiscono le sottoscrizioni.

L'uso di un indirizzo di posta elettronica di notifica offre la possibilità di consentire ai sottoscrittori di ricevere comunicazioni importanti sulle sottoscrizioni senza modificare la funzionalità degli indirizzi di posta elettronica di accesso.  

## <a name="resend-assignment-emails"></a>Inviare di nuovo i messaggi di posta elettronica di assegnazione
Dopo aver aggiunto un sottoscrittore, verrà inviato automaticamente un messaggio di posta elettronica di assegnazione al nuovo sottoscrittore con altre istruzioni. È possibile inviare di nuovo il messaggio di posta elettronica di assegnazione in qualsiasi momento selezionando il sottoscrittore e quindi il pulsante **Invia** di nuovo nel menu in alto.  Per inviare di nuovo messaggi di posta elettronica a più utenti, tenere premuto **CTRL** mentre si selezionano i sottoscrittori.  Quando si seleziona il **pulsante Invia di** nuovo, viene visualizzata una finestra di dialogo in cui viene chiesto di confermare che si vuole inviare di nuovo i sottoscrittori.  


## <a name="resources"></a>Risorse
- Serve aiuto?  Contattare il [supporto per le sottoscrizioni.](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere molti utenti,  vedere le informazioni su come assegnare sottoscrizioni a [più sottoscrittori](assign-license-bulk.md).
