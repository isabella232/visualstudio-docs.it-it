---
title: Assegnare Visual Studio sottoscrizioni a più utenti | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.date: 03/19/2021
ms.topic: conceptual
description: Informazioni su come gli amministratori possono assegnare più sottoscrizioni contemporaneamente.
ms.openlocfilehash: 813c2caecb5e54ba0ed0a4f4196be84105aa3722
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709980"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Assegnare sottoscrizioni a più utenti
Il portale di amministrazione delle sottoscrizioni permette di aggiungere utenti uno per volta o in gruppi di grandi dimensioni.  Per aggiungere singoli utenti, vedere [Aggiungere singoli utenti](assign-license.md).

Per aggiungere gruppi di utenti di grandi dimensioni, è possibile usare la funzionalità di aggiunta in blocco oppure, se l'organizzazione usa Microsoft Azure Active Directory (Azure AD), è possibile usare Azure AD gruppi. Questo articolo illustra il processo per entrambe le opzioni.  Guardare questo video o leggere per altre informazioni sulla funzionalità di aggiunta in blocco. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Usare l'aggiunta in blocco per assegnare sottoscrizioni
1. Accedere al portale Sottoscrizioni di Visual Studio administration all'indirizzo <https://manage.visualstudio.com> .

1. Per aggiungere più sottoscrittori contemporaneamente, passare alla **scheda Gestisci sottoscrittori.** Scegliere la **scheda** Aggiungi, quindi **scegliere Aggiungi** in blocco nell'elenco a discesa.  

1. L'aggiunta in blocco usa un modello Microsoft Excel per caricare le informazioni del Sottoscrittore. Nella finestra Upload più Sottoscrittori selezionare **Scarica** per scaricare il modello.
   > [!div class="mx-imgBorder"]
   > ![Scaricare il modello di Excel per caricare più sottoscrittori](media/download-template-upload-subscribers.png "Scaricare il modello di Excel vuoto per avviare il processo di assegnazione in blocco.")
   >
   > [!NOTE]
   > Scaricare sempre la versione più recente del modello. Se si usa una versione precedente, il caricamento in blocco potrebbe non riuscire.

1. Nel foglio di calcolo Excel compilare i campi con le informazioni per gli utenti a cui si desidera assegnare le sottoscrizioni. Il *riferimento* è un campo facoltativo. Al termine, salvare il file in locale.

    > [!NOTE]
    > Uno dei campi del modello consente agli amministratori di abilitare o disabilitare la capacità dei sottoscrittori di scaricare il software.  La disabilitazione dei download disabilita anche l'accesso ai codici Product Key.

   Per garantire un caricamento senza errori, osservare le procedure consigliate seguenti:

    - Verificare che nessuno dei campi modulo contenga virgole.
    - Rimuovere gli spazi prima e dopo i campi del modulo.
    - Assicurarsi che i nomi degli utenti non contengano spazi aggiuntivi nei nomi o cognomi composti da due parti (se il nome è composto da due parti, ad esempio "Maria Giovanna", digitare "MariaGiovanna" poiché il sistema non annulla lo spazio aggiuntivo).
    - Assicurarsi che tutti i campi obbligatori siano completati. 
    - Controllare la **colonna Messaggio di** errore.  Se sono elencati errori, risolverli prima di tentare di caricare il file. 

1. Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio. Nella finestra **Upload più Sottoscrittori** selezionare **Sfoglia**.
   > [!div class="mx-imgBorder"]
   > ![Passare al modello salvato per caricare più sottoscrittori](media/bulk-add-browse-saved-template.png "È possibile passare al percorso del file o trascinarlo in questa finestra di dialogo.")

1. Passare al file Excel salvato e quindi selezionare **OK.**
   > [!div class="mx-imgBorder"]
   > ![Caricare il modello di Excel per caricare più sottoscrittori](media/bulk-upload-subscribers.png "Il modello con i dati verrà visualizzato qui.  Selezionare OK per avviare il caricamento.")

    Viene visualizzata una finestra di dialogo di avanzamento del caricamento.

    Se il modello contiene errori, il caricamento avrà esito negativo e verranno visualizzati gli errori per consentire di correggere il modello e tentare nuovamente il caricamento in blocco.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di errore se il caricamento di più sottoscrittori ha esito negativo](_img/assign-license-bulk/bulk-add-upload-failure.png "Questo messaggio viene visualizzato se il file caricato contiene errori.  Risolvere gli errori ed eseguire di nuovo il processo di aggiunta in blocco.")

   Se si verifica un errore, seguire questa procedura:
   1. Aprire il Excel creato, correggere i problemi e salvare il file.
   0. Tornare al portale di amministrazione e chiudere il messaggio di errore.
   0. Scegliere **Aggiungi**.
   0. Selezionare **Aggiungi in blocco**.
   0. Poiché il file di Excel è già stato salvato, non è necessario scaricare il modello.  Selezionare **Sfoglia,** individuare il file appena salvato e selezionare **Apri.**
   0. Selezionare **OK**.


    Quando il caricamento ha esito positivo, viene visualizzato l'elenco di sottoscrittori e un messaggio di conferma.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di conferma se il caricamento di più sottoscrittori ha esito positivo](_img/assign-license-bulk/bulk-add-upload-success.png "Al termine del caricamento, si riceverà un messaggio di conferma.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Usare Azure Active Directory gruppi per assegnare sottoscrizioni 
L'uso di questa funzionalità semplifica la gestione delle assegnazioni di sottoscrizione. È possibile aggiungere Azure Active Directory di sicurezza nel portale di amministrazione delle sottoscrizioni per garantire che a tutti i singoli utenti del gruppo sia assegnata una sottoscrizione. Per semplificare, quando gli utenti lasciano l'organizzazione e vengono rimossi dal Azure Active Directory, viene rimosso anche l'accesso alle sottoscrizioni. 


> [!IMPORTANT]
>
> Le limitazioni seguenti si applicano all'uso di gruppi Azure AD per l'aggiunta di sottoscrittori:
> - L'amministratore deve essere un membro del tenant di AAD quando inizialmente si aggiunge un gruppo al portale di amministrazione.  Dopo l'aggiunta del gruppo, le modifiche all'appartenenza ai gruppi non richiedono il coinvolgimento dell'amministratore. 
> - I gruppi devono contenere almeno un membro.  I gruppi vuoti non sono supportati.
> - Tutti gli utenti devono essere nel livello superiore del gruppo.  I gruppi annidati non sono supportati.
> - Sono supportati solo i contratti attendibili. (Solo i contratti che possono "classificare complessivamente" le sottoscrizioni sono attendibili).
> - Tutti i membri del gruppo devono avere un indirizzo di posta elettronica associato al Azure AD account.
> - Gli indirizzi di posta elettronica separati per le notifiche non sono supportati per le sottoscrizioni aggiunte Azure AD gruppi.  

Guardare questo video o leggere per altre informazioni sull'aggiunta di sottoscrittori usando la funzionalità Azure Active Directory gruppo. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Accedere al portale di amministrazione Sottoscrizioni di Visual Studio all'indirizzo [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Per aggiungere più sottoscrittori contemporaneamente, passare alla **scheda Gestisci sottoscrittori.**

3. Scegliere la **scheda** Aggiungi, quindi selezionare **Azure Active Directory gruppo nell'elenco** a discesa.  

   > [!div class="mx-imgBorder"]
   > ![Scegliere l'aggiunta in blocco usando Azure AD](_img/assign-license-bulk/bulk-add-aad.png "Scegliere l'aggiunta in blocco usando Azure AD per eseguire il pull dei sottoscrittori dal Azure Active Directory gruppo.")

4. Iniziare a immettere il nome del Azure AD che si desidera aggiungere nel campo del modulo. In questo modo verranno cercati i gruppi Azure AD all'interno dell'organizzazione. 

5. Quando si seleziona il gruppo, il campo verrà popolato automaticamente con il nome del gruppo. Sarà possibile visualizzare gli utenti in tale gruppo prima di aggiungerli. È quindi possibile scegliere il livello di sottoscrizione, i diritti di download e le preferenze di comunicazione per il gruppo. Se si desidera, è possibile aggiungere dettagli nel campo di riferimento. 

   > [!div class="mx-imgBorder"]
   > ![Scegliere il gruppo Azure AD locale](_img/assign-license-bulk/bulk-add-aad-details.png "Scegliere il nome del gruppo Azure AD per aggiungere sottoscrittori da tale gruppo.")

6. Selezionare **Aggiungi** e quindi **Conferma.** 

7. Per visualizzare il gruppo aggiunto, scorrere fino alla fine dell'elenco di utenti.  

8. Selezionare **Visualizza sottoscrittori** per visualizzare i membri del gruppo. È possibile visualizzare i dettagli sui sottoscrittori nel gruppo, ma non è possibile apportare modifiche ai sottoscrittori o alle sottoscrizioni assegnate.    

> [!NOTE]
> Se sono già state assegnate sottoscrizioni singolarmente agli utenti aggiunti successivamente come parte di un gruppo Azure AD, verranno aggiunte come parte del gruppo e non verranno più elencate singolarmente. Tuttavia, se la singola sottoscrizione è per un livello di sottoscrizione diverso, avrà due sottoscrizioni.  Esempio: se un utente ha una singola sottoscrizione Visual Studio Professional e è membro di un gruppo a cui si assegnano Visual Studio Enterprise sottoscrizioni, avrà entrambe le opzioni.  
>
> Se si rimuove un sottoscrittore da un gruppo Azure Active Directory a cui sono state assegnate sottoscrizioni, l'aggiornamento potrebbe richiedere fino a 24 ore prima che l'aggiornamento venga visualizzato nel portale di amministrazione. 


## <a name="frequently-asked-questions"></a>Domande frequenti

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>D: Perché non è possibile visualizzare l'opzione per usare Azure Active Directory gruppi per aggiungere sottoscrittori?
A: La funzionalità è attualmente disponibile solo per le organizzazioni con contratti attendibili.  Selezionare il **pulsante Dettagli** per visualizzare le informazioni sull'accordo.

   > [!div class="mx-imgBorder"]
   > ![Fare clic sul pulsante Dettagli](_img/assign-license-bulk/bulk-add-agreement.png "Fare clic sul pulsante Dettagli per visualizzare il tipo di contratto")

### <a name="q-i-added-users-to-my-azure-active-directory-group-but-they-dont-have-subscriptions-yet-why"></a>D: Gli utenti sono stati aggiunti al gruppo Azure Active Directory, ma non hanno ancora sottoscrizioni. Perché? 
A: Se le modifiche sono state apportate direttamente Azure Active Directory le sottoscrizioni devono essere assegnate molto rapidamente, tuttavia se le modifiche sono state apportate in un'istanza locale di Active Directory, sarà prima necessario sincronizzarla con Azure Active Directory. A seconda della configurazione di Active Directory locale, le modifiche potrebbero richiedere fino a 24 ore. Se sono più di 24 ore, il team di [supporto può risolvere eventuali problemi.](https://aka.ms/vsadminhelp) 

### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-active-directory-group"></a>D: È possibile scegliere più livelli di sottoscrizione da assegnare all'interno di Azure Active Directory gruppo?
A: No: tutti gli utenti del gruppo ricevono lo stesso livello di sottoscrizione.

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-active-directory-group"></a>D: È possibile modificare i dettagli dei sottoscrittori delle persone aggiunte in un Azure Active Directory gruppo?
A: No: per modificare le informazioni per un singolo sottoscrittore, è necessario rimuoverle dal gruppo di sicurezza Azure Active Directory e assegnarle una sottoscrizione singolarmente.

### <a name="q-can-i-add-separate-notification-email-addresses-for-members-of-an-azure-active-directory-group"></a>D: È possibile aggiungere indirizzi di posta elettronica di notifica separati per i membri di un Azure Active Directory gruppo?
A: No: gli indirizzi di posta elettronica separati per le notifiche non sono attualmente supportati per le sottoscrizioni aggiunte Azure Active Directory gruppi. Tutti i messaggi di posta elettronica verranno inviati al messaggio di posta elettronica primario (nome del principio utente)

## <a name="resources"></a>Risorse
- [Visual Studio di amministrazione e sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere solo uno o due sottoscrittori, vedere [Aggiungere singoli utenti](assign-license.md)
