---
title: Assegnare licenze a gruppi di utenti per sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/21/2021
ms.topic: how-to
description: Informazioni su come gli amministratori possono assegnare licenze a più sottoscrittori usando la funzionalità di aggiunta in blocco o Microsoft Azure Active Directory gruppi
ms.openlocfilehash: 98740ba82f0641b310edc46e35a2e6a57fe10ea8
ms.sourcegitcommit: d5c038792da2c86436750380633ee80c39e4c4ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2021
ms.locfileid: "114597085"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Assegnare sottoscrizioni a più utenti
Il portale di amministrazione delle sottoscrizioni permette di aggiungere utenti uno per volta o in gruppi di grandi dimensioni.  Per aggiungere singoli utenti, vedere [Aggiungere singoli utenti](assign-license.md).

Per aggiungere gruppi di utenti di grandi dimensioni, è possibile usare la funzionalità di aggiunta in blocco oppure, se l'organizzazione usa Microsoft Azure Active Directory (Azure AD), è possibile usare Azure AD gruppi. Questo articolo illustra il processo per entrambe le opzioni.  Guardare questo video o leggere per altre informazioni sulla funzionalità di aggiunta in blocco. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Usare l'aggiunta in blocco per assegnare sottoscrizioni
1. Accedere al portale Sottoscrizioni di Visual Studio administration all'indirizzo <https://manage.visualstudio.com> .

1. Per aggiungere più sottoscrittori contemporaneamente, passare alla **scheda Gestisci sottoscrittori** . Scegliere la **scheda** Aggiungi, quindi scegliere **Aggiungi** in blocco nell'elenco a discesa.  

1. L'aggiunta in blocco usa un modello Microsoft Excel per caricare le informazioni del sottoscrittore. Nella finestra Upload più Sottoscrittori selezionare **Scarica** per scaricare il modello.
   > [!div class="mx-imgBorder"]
   > ![Scaricare il modello di Excel per caricare più sottoscrittori](media/download-template-upload-subscribers.png "Scaricare il modello di Excel vuoto per iniziare il processo di assegnazione in blocco.")
   >
   > [!NOTE]
   > Scaricare sempre la versione più recente del modello. Se si usa una versione precedente, il caricamento in blocco potrebbe non riuscire.

1. Nel foglio di calcolo Excel compilare i campi con le informazioni per gli utenti a cui si desidera assegnare le sottoscrizioni. Il *riferimento* è un campo facoltativo. Al termine, salvare il file in locale.

    > [!NOTE]
    > Uno dei campi nel modello consente agli amministratori di abilitare o disabilitare la capacità dei sottoscrittori di scaricare il software.  La disabilitazione dei download disabilita anche l'accesso ai codici Product Key.

   Per garantire un caricamento senza errori, osservare le procedure consigliate seguenti:

    - Verificare che nessuno dei campi modulo contenga virgole.
    - Rimuovere gli spazi prima e dopo i campi del modulo.
    - Assicurarsi che i nomi degli utenti non contengano spazi aggiuntivi nei nomi o cognomi composti da due parti (se il nome è composto da due parti, ad esempio "Maria Giovanna", digitare "MariaGiovanna" poiché il sistema non annulla lo spazio aggiuntivo).
    - Assicurarsi che tutti i campi obbligatori siano completati. 
    - Controllare la **colonna Messaggio di** errore.  Se sono elencati errori, risolverli prima di provare a caricare il file. 

1. Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio. Nella finestra **Upload più Sottoscrittori** selezionare **Sfoglia**.
   > [!div class="mx-imgBorder"]
   > ![Passare al modello salvato per caricare più sottoscrittori](media/bulk-add-browse-saved-template.png "È possibile passare al percorso del file o trascinarlo e rilasciarlo in questa finestra di dialogo.")

1. Passare al file Excel salvato e quindi selezionare **OK.**
   > [!div class="mx-imgBorder"]
   > ![Caricare il modello di Excel per caricare più sottoscrittori](media/bulk-upload-subscribers.png "Il modello con i dati verrà visualizzato qui.  Selezionare OK per iniziare il caricamento.")

    Viene visualizzata una finestra di dialogo di avanzamento del caricamento.

    Se il modello contiene errori, il caricamento avrà esito negativo e verranno visualizzati gli errori per consentire di correggere il modello e tentare nuovamente il caricamento in blocco.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di errore se il caricamento di più sottoscrittori ha esito negativo](_img/assign-license-bulk/bulk-add-upload-failure.png "Questo messaggio verrà visualizzato se il file caricato contiene errori.  Risolvere gli errori ed eseguire di nuovo il processo di aggiunta in blocco.")

   Se si verifica un errore, seguire questa procedura:
   1. Aprire il Excel file creato, correggere i problemi e salvare il file.
   0. Tornare al portale di amministrazione e ignorare il messaggio di errore.
   0. Scegliere **Aggiungi**.
   0. Selezionare **Aggiungi in blocco.**
   0. Poiché il file di Excel è già stato salvato, non è necessario scaricare il modello.  Selezionare **Sfoglia,** individuare il file appena salvato e selezionare **Apri.**
   0. Selezionare **OK**.


    Quando il caricamento ha esito positivo, viene visualizzato l'elenco di sottoscrittori e un messaggio di conferma.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di conferma se il caricamento di più sottoscrittori ha esito positivo](_img/assign-license-bulk/bulk-add-upload-success.png "Al termine del caricamento, si riceverà un messaggio di conferma.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Usare Azure Active Directory per assegnare sottoscrizioni 
L'uso di questa funzionalità semplifica il controllo delle assegnazioni delle sottoscrizioni. È possibile aggiungere Azure Active Directory di sicurezza nel portale di amministrazione delle sottoscrizioni per garantire che a tutti gli utenti del gruppo sia assegnata una sottoscrizione. E per semplificare, quando gli utenti lasciano l'organizzazione e vengono rimossi dal Azure Active Directory, viene rimosso anche l'accesso alle sottoscrizioni. 


> [!IMPORTANT]
>
> Le limitazioni seguenti si applicano all'uso di gruppi di Azure AD per l'aggiunta di sottoscrittori:
> - L'amministratore deve essere un membro del tenant di AAD quando inizialmente si aggiunge un gruppo al portale di amministrazione.  Dopo l'aggiunta del gruppo, le modifiche all'appartenenza dei gruppi non richiedono il coinvolgimento dell'amministratore. 
> - I gruppi devono contenere almeno un membro.  I gruppi vuoti non sono supportati.
> - Tutti gli utenti devono essere nel livello superiore del gruppo.  I gruppi annidati non sono supportati.
> - Sono supportati solo i contratti attendibili. Solo i contratti che possono "overallocate" sottoscrizioni sono attendibili.
> - Tutti i membri del gruppo devono avere un indirizzo di posta elettronica associato al Azure AD account.
> - Gli indirizzi di posta elettronica separati per le notifiche non sono supportati per le sottoscrizioni aggiunte Azure AD gruppi.  

Guardare questo video o leggere per altre informazioni sull'aggiunta di sottoscrittori usando la funzionalità Azure Active Directory gruppo di sottoscrizione. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Accedere al portale di Sottoscrizioni di Visual Studio all'indirizzo [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Per aggiungere più sottoscrittori contemporaneamente, passare alla **scheda Gestisci sottoscrittori.**

3. Scegliere la **scheda** Aggiungi, quindi **selezionare Azure Active Directory gruppo** nell'elenco a discesa.  

   > [!div class="mx-imgBorder"]
   > ![Scegliere l'aggiunta in blocco usando Azure AD](_img/assign-license-bulk/bulk-add-aad.png "Scegliere la funzionalità Aggiungi in blocco Azure AD per eseguire il pull dei sottoscrittori Azure Active Directory gruppo.")

4. Iniziare a immettere il nome del Azure AD che si desidera aggiungere nel campo del modulo. In questo modo verrà cercata la Azure AD gruppi all'interno dell'organizzazione. 

5. Quando si seleziona il gruppo, il campo verrà popolato automaticamente con il nome del gruppo. Sarà possibile visualizzare gli utenti in tale gruppo prima di aggiungerli. Successivamente, è possibile scegliere il livello di sottoscrizione, i diritti di download e le preferenze di comunicazione per il gruppo. Se si vuole, è possibile aggiungere dettagli nel campo di riferimento. 

   > [!div class="mx-imgBorder"]
   > ![Scegliere il gruppo Azure AD gruppo](_img/assign-license-bulk/bulk-add-aad-details.png "Scegliere il nome del gruppo Azure AD per aggiungere sottoscrittori da tale gruppo.")

6. Selezionare **Aggiungi** e quindi **Conferma.** 

7. Per visualizzare il gruppo aggiunto, scorrere fino alla fine dell'elenco di utenti.  

8. Selezionare **Visualizza sottoscrittori** per visualizzare i membri del gruppo. È possibile visualizzare i dettagli sui sottoscrittori nel gruppo, ma non è possibile apportare modifiche ai sottoscrittori o alle sottoscrizioni a cui sono assegnati.    

> [!NOTE]
> Se sono già state assegnate sottoscrizioni singolarmente agli utenti aggiunti successivamente come parte di un gruppo di Azure AD, queste verranno aggiunte come parte del gruppo e non verranno più elencate singolarmente. Tuttavia, se la singola sottoscrizione è per un livello di sottoscrizione diverso, avrà due sottoscrizioni.  Esempio: se un utente ha una singola sottoscrizione Visual Studio Professional e è membro di un gruppo a cui si assegnano sottoscrizioni Visual Studio Enterprise, avrà entrambe le opzioni.  
>
> Se si rimuove un sottoscrittore da un gruppo di Azure Active Directory a cui sono state assegnate sottoscrizioni, potrebbero essere necessario fino a 24 ore prima che l'aggiornamento venga visualizzato nel portale di amministrazione. 


## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>D: È possibile scegliere più livelli di sottoscrizione da assegnare all'interno di Azure AD gruppo? 
A: No: tutti gli utenti del gruppo ricevono la stessa sottoscrizione. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>D: È possibile modificare i dettagli dei sottoscrittori delle persone aggiunte in un gruppo Azure AD sottoscrizione?  
A: No : per modificare le informazioni per un singolo sottoscrittore, è necessario rimuoverle dal gruppo di sicurezza Azure AD e assegnare loro una sottoscrizione singolarmente.  

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>D: Perché non è possibile visualizzare l'opzione per usare Azure Active Directory per aggiungere sottoscrittori?
A: La funzionalità è attualmente disponibile solo per le organizzazioni con contratti attendibili.  Selezionare il **pulsante Dettagli** per visualizzare le informazioni sul contratto.

   > [!div class="mx-imgBorder"]
   > ![Fare clic sul pulsante Dettagli](_img/assign-license-bulk/bulk-add-agreement.png "Fare clic sul pulsante Dettagli per visualizzare il tipo di contratto")

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>D: È stato aggiunto un utente al gruppo di sicurezza Azure AD, ma non viene visualizzato come aggiunto nel portale di amministrazione delle sottoscrizioni e non ha una sottoscrizione. Perché no?  
A: A seconda di come l'organizzazione ha configurato Azure AD, potrebbero verificarsi ritardi fino a 24 ore prima dell'aggiunta dell'utente. Se sono state più di 24 ore, visitare la pagina Visual Studio [supporto per l'amministrazione e le sottoscrizioni.](https://my.visualstudio.com/gethelp)  

## <a name="resources"></a>Risorse
- [Visual Studio di amministrazione e sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere solo uno o due sottoscrittori,  vedere [Aggiungere singoli utenti](assign-license.md)
