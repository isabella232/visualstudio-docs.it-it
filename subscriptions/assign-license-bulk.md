---
title: Assegnare licenze a gruppi di utenti per sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/02/2020
ms.topic: conceptual
description: Informazioni su come gli amministratori possono assegnare licenze a più sottoscrittori usando la funzionalità di aggiunta in blocco o i gruppi di Microsoft Azure Active Directory
ms.openlocfilehash: eb641d86733ef794f1d53ae6eee45e0bdf4fde18
ms.sourcegitcommit: deab74e8f41b30b28c041b048d67b3fff2cceab9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2020
ms.locfileid: "80994443"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Assegnare sottoscrizioni a più utenti
Il portale di amministrazione delle sottoscrizioni permette di aggiungere utenti uno per volta o in gruppi di grandi dimensioni.  Per aggiungere singoli utenti, vedere [Aggiungere singoli utenti](assign-license.md).

Per aggiungere grandi gruppi di utenti, è possibile usare la funzionalità di aggiunta in blocco oppure, se l'organizzazione usa Microsoft Azure Active Directory (Azure AD), è possibile usare i gruppi di Azure AD. Questo articolo spiegherà il processo per entrambe le opzioni. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>Usare l'aggiunta in blocco per assegnare sottoscrizioniUse Bulk add to assign subscriptions
1. Accedere al portale di amministrazione https://manage.visualstudio.comdelle sottoscrizioni di Visual Studio all'indirizzo .

2. Per aggiungere più sottoscrittori contemporaneamente, passare alla scheda **Add** **Gestisci sottoscrittori.** **Bulk add**  

2. Aggiunta in blocco utilizza un modello di Microsoft Excel per caricare le informazioni sul sottoscrittore. Nella finestra di dialogo Upload Multiple Subscriber (Carica più sottoscrittori), fare clic su **Download** per scaricare il modello.
   > [!div class="mx-imgBorder"]
   > ![Scaricare il modello di Excel per caricare più sottoscrittori](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Scaricare sempre la versione più recente del modello. Se si usa una versione precedente, il caricamento in blocco potrebbe non riuscire.

3. Nel foglio di calcolo Excel compilare i campi con le informazioni per gli utenti a cui si desidera assegnare le sottoscrizioni. *(Riferimento* è un campo facoltativo.) Al termine, salvare il file in locale.

   Per garantire un caricamento senza errori, osservare le procedure consigliate seguenti:

    - Verificare che nessuno dei campi modulo contenga virgole.
    - Rimuovere gli spazi prima e dopo i campi del modulo.
    - Assicurarsi che i nomi degli utenti non contengano spazi aggiuntivi nei nomi o cognomi composti da due parti (se il nome è composto da due parti, ad esempio "Maria Giovanna", digitare "MariaGiovanna" poiché il sistema non annulla lo spazio aggiuntivo).
    - Assicurarsi che tutti i campi obbligatori siano completi. 
    - Controllare la colonna **Messaggio di errore.**  Se sono elencati errori, risolverli prima di tentare di caricare il file. 

4. Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio. Nella finestra di dialogo **Upload Multiple Subscribers** (Carica più sottoscrittori) fare clic su **Sfoglia**.
   > [!div class="mx-imgBorder"]
   > ![Passare al modello salvato per caricare più sottoscrittori](media/bulk-add-browse-saved-template.png)

5. Passare al file Excel salvato e quindi fare clic su **OK**.
   > [!div class="mx-imgBorder"]
   > ![Caricare il modello di Excel per caricare più sottoscrittori](media/bulk-upload-subscribers.png)

    Viene visualizzata una finestra di dialogo di avanzamento del caricamento.

    Se il modello contiene errori, il caricamento avrà esito negativo e verranno visualizzati gli errori per consentire di correggere il modello e tentare nuovamente il caricamento in blocco.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di errore se il caricamento di più sottoscrittori ha esito negativo](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Se si verifica un errore, attenersi alla seguente procedura:
   1. Aprire il file di Excel creato, correggere i problemi e salvare il file.
   0. Tornare al portale di amministrazione e scegliere **Aggiungi**.
   0. Selezionare **Aggiunta in blocco**.
   0. Poiché il file Excel è già stato salvato, non è necessario scaricare il modello.  Fare clic su **Sfoglia**, individuare il file appena salvato e fare clic su **Apri**.
   0. Fare clic su **OK**.


    Quando il caricamento ha esito positivo, viene visualizzato l'elenco di sottoscrittori e un messaggio di conferma.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di conferma se il caricamento di più sottoscrittori ha esito positivo](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Usare i gruppi di Azure Active Directory per assegnare sottoscrizioniUse Azure Active Directory groups to assign subscriptions 
L'utilizzo di questa funzionalità semplifica il mantenersi in primo piano sulle assegnazioni delle sottoscrizioni. È possibile aggiungere gruppi di sicurezza di Azure Active Directory nel portale di amministrazione delle sottoscrizioni per garantire che a tutti i utenti del gruppo venga assegnata una sottoscrizione. E per semplificare, quando gli utenti lasciano l'organizzazione e vengono rimossi da Azure Active Directory, viene rimosso anche l'accesso alle sottoscrizioni. 


> [!IMPORTANT]
>
> Le limitazioni seguenti si applicano all'uso dei gruppi di Azure AD per l'aggiunta di sottoscrittori:The following limitations apply to the use of Azure AD groups for adding subscribers:
> - I gruppi devono contenere almeno un membro.  I gruppi vuoti non sono supportati.
> - I gruppi devono avere meno di 1.000 utenti 
> - Tutti gli utenti devono essere nel livello superiore del gruppo.  I gruppi nidificati non sono supportati
> - Sono supportati solo gli accordi attendibili
> - Tutti i membri del gruppo devono avere un indirizzo di posta elettronica associato all'account Azure ADAll members of the group must have an email address associated with their Azure AD account
> - Indirizzi di posta elettronica separati per le notifiche non sono supportati per le sottoscrizioni aggiunte usando i gruppi di Azure AD.  

1. Accedere al portale di amministrazione [https://manage.visualstudio.com](https://manage.visualstudio.com)delle sottoscrizioni di Visual Studio all'indirizzo .

2. Per aggiungere più sottoscrittori contemporaneamente, passare alla scheda **Gestisci sottoscrittori.**

3. Scegliere la scheda **Aggiungi,** quindi selezionare il **gruppo Azure Active Directory** nell'elenco a discesa.  

   > [!div class="mx-imgBorder"]
   > ![Scegliere l'aggiunta in blocco con Azure ADChoose bulk add using Azure AD](_img/assign-license-bulk/bulk-add-aad.png)

4. Iniziare a immettere il nome del gruppo di Azure AD che si vuole aggiungere nel campo modulo. Verrà eseguita la ricerca dei gruppi di Azure AD disponibili all'interno dell'organizzazione. 

5. Quando si seleziona il gruppo, il campo verrà popolato automaticamente con il nome del gruppo. È possibile visualizzare gli utenti di tale gruppo prima di aggiungerli. Successivamente, è possibile scegliere il livello di abbonamento, i diritti di download e le preferenze di comunicazione per il gruppo. Se lo si desidera, è possibile aggiungere dettagli nel campo di riferimento. 

   > [!div class="mx-imgBorder"]
   > ![Scegliere l'aggiunta in blocco con Azure ADChoose bulk add using Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Fare clic su **Aggiungi** e quindi **su Conferma**. 

7. Per visualizzare il gruppo aggiunto, scorrere fino alla fine dell'elenco di utenti.  

8. Selezionare **Visualizza sottoscrittori** per visualizzare i membri del gruppo. È possibile visualizzare i dettagli sui sottoscrittori del gruppo, ma non è possibile apportare modifiche ai sottoscrittori o alle sottoscrizioni a cui sono assegnati.    

> [!NOTE]
> Se le sottoscrizioni sono già state assegnate singolarmente agli utenti aggiunti successivamente come parte di un gruppo di Azure AD, verranno aggiunti come parte del gruppo e non verranno più elencati singolarmente. Tuttavia, se la singola sottoscrizione è per un livello di sottoscrizione diverso, avranno due sottoscrizioni.  Esempio: se un utente ha una singola sottoscrizione di Visual Studio Professional e sono membri di un gruppo a cui si assegnano le sottoscrizioni di Visual Studio Enterprise, entrambi avranno.  


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>D: È possibile scegliere più livelli di sottoscrizione da assegnare all'interno di un gruppo di Azure AD? 
R: No, tutti i membri del gruppo ricevono la stessa sottoscrizione. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>D: È possibile modificare i dettagli del sottoscrittore delle persone aggiunte in un gruppo di Azure AD?  
R: No: Per modificare le informazioni per un singolo sottoscrittore, è necessario rimuoverle dal gruppo di sicurezza di Azure AD e assegnare loro una sottoscrizione singolarmente.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>D: Ho aggiunto qualcuno al gruppo di sicurezza di Azure AD, ma non li vedo aggiunti nel portale di amministrazione delle sottoscrizioni e non dispone di una sottoscrizione. relativa ricerca  
R: A seconda di come l'organizzazione ha configurato Azure AD, è possibile che si verifichino ritardi fino a 24 ore prima dell'aggiunta dell'utente. Se sono passate più di 24 ore, [contattare il supporto](https://visualstudio.microsoft.com/support/support-overview-vs)tecnico .  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere solo uno o due sottoscrittori,  vedere [Aggiungere singoli utenti](assign-license.md)
- Richiesta di assistenza Contattare il [supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).
