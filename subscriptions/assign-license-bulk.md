---
title: Assegnare licenze a gruppi di utenti per sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 09/21/2020
ms.topic: how-to
description: Informazioni su come gli amministratori possono assegnare licenze a più sottoscrittori usando la funzionalità di aggiunta in blocco o i gruppi di Microsoft Azure Active Directory
ms.openlocfilehash: 6154e9796e1ba021eedf86bcee7d508e285b6645
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "91022422"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Assegnare sottoscrizioni a più utenti
Il portale di amministrazione delle sottoscrizioni permette di aggiungere utenti uno per volta o in gruppi di grandi dimensioni.  Per aggiungere singoli utenti, vedere [Aggiungere singoli utenti](assign-license.md).

Per aggiungere gruppi di utenti di grandi dimensioni, è possibile utilizzare la funzionalità di aggiunta in blocco o, se l'organizzazione utilizza Microsoft Azure Active Directory (Azure AD), è possibile utilizzare Azure AD gruppi. In questo articolo viene illustrato il processo per entrambe le opzioni.  Guardare questo video o leggere per ulteriori informazioni sulla funzionalità di aggiunta in blocco. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Utilizzare Aggiunta bulk per assegnare sottoscrizioni
1. Accedere al portale di amministrazione delle sottoscrizioni di Visual Studio all'indirizzo <https://manage.visualstudio.com> .

1. Per aggiungere più sottoscrittori contemporaneamente, passare alla scheda **Gestisci sottoscrittori** . Scegliere la scheda **Aggiungi** , quindi scegliere **Aggiungi in blocco** nell'elenco a discesa.  

1. L'aggiunta bulk utilizza un modello di Microsoft Excel per caricare informazioni sul Sottoscrittore. Nella finestra di dialogo Carica più Sottoscrittori selezionare **download** per scaricare il modello.
   > [!div class="mx-imgBorder"]
   > ![Scaricare il modello di Excel per caricare più sottoscrittori](media/download-template-upload-subscribers.png "Scaricare il modello di Excel vuoto per iniziare il processo di assegnazione in blocco.")
   >
   > [!NOTE]
   > Scaricare sempre la versione più recente del modello. Se si usa una versione precedente, il caricamento in blocco potrebbe non riuscire.

1. Nel foglio di calcolo Excel compilare i campi con le informazioni per gli utenti a cui si desidera assegnare le sottoscrizioni. (*Reference* è un campo facoltativo). Al termine, salvare il file localmente.

    > [!NOTE]
    > Uno dei campi del modello consente agli amministratori di abilitare o disabilitare la possibilità per i sottoscrittori di scaricare il software.  La disabilitazione dei download Disabilita anche l'accesso ai codici Product Key.

   Per garantire un caricamento senza errori, osservare le procedure consigliate seguenti:

    - Verificare che nessuno dei campi modulo contenga virgole.
    - Rimuovere gli spazi prima e dopo i campi del modulo.
    - Assicurarsi che i nomi degli utenti non contengano spazi aggiuntivi nei nomi o cognomi composti da due parti (se il nome è composto da due parti, ad esempio "Maria Giovanna", digitare "MariaGiovanna" poiché il sistema non annulla lo spazio aggiuntivo).
    - Verificare che tutti i campi obbligatori siano completati. 
    - Controllare la colonna del **messaggio di errore** .  Se vengono elencati errori, risolverli prima di provare a caricare il file. 

1. Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio. Nella finestra di dialogo **carica più sottoscrittori** selezionare **Sfoglia**.
   > [!div class="mx-imgBorder"]
   > ![Passare al modello salvato per caricare più sottoscrittori](media/bulk-add-browse-saved-template.png "È possibile passare al percorso del file oppure trascinarlo e rilasciarlo in questa finestra di dialogo.")

1. Passare al file di Excel salvato e quindi fare clic su **OK**.
   > [!div class="mx-imgBorder"]
   > ![Caricare il modello di Excel per caricare più sottoscrittori](media/bulk-upload-subscribers.png "Il modello con i dati verrà visualizzato qui.  Selezionare OK per avviare il caricamento.")

    Viene visualizzata una finestra di dialogo di avanzamento del caricamento.

    Se il modello contiene errori, il caricamento avrà esito negativo e verranno visualizzati gli errori per consentire di correggere il modello e tentare nuovamente il caricamento in blocco.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di errore se il caricamento di più sottoscrittori ha esito negativo](_img/assign-license-bulk/bulk-add-upload-failure.png "Questo messaggio verrà visualizzato se il file caricato conteneva errori.  Risolvere gli errori ed eseguire di nuovo il processo di aggiunta in blocco.")

   Se si verifica un errore, attenersi alla procedura seguente:
   1. Aprire il file di Excel creato, risolvere i problemi e salvare il file.
   0. Tornare al portale di amministrazione e chiudere il messaggio di errore.
   0. Scegliere **Aggiungi**.
   0. Selezionare **Aggiungi in blocco**.
   0. Poiché è già stato salvato il file di Excel, non è necessario scaricare il modello.  Selezionare **Sfoglia**, individuare il file appena salvato e selezionare **Apri**.
   0. Selezionare **OK**.


    Quando il caricamento ha esito positivo, viene visualizzato l'elenco di sottoscrittori e un messaggio di conferma.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di conferma se il caricamento di più sottoscrittori ha esito positivo](_img/assign-license-bulk/bulk-add-upload-success.png "Quando il caricamento viene completato correttamente, si riceverà un messaggio di conferma.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Usare gruppi di Azure Active Directory per assegnare sottoscrizioni 
L'uso di questa funzionalità consente di mantenere più facilmente le assegnazioni di sottoscrizione. È possibile aggiungere Azure Active Directory gruppi di sicurezza nel portale di amministrazione delle sottoscrizioni, in modo da garantire che a tutti gli utenti del gruppo venga assegnata una sottoscrizione. Per semplificare, quando gli utenti lasciano l'organizzazione e vengono rimossi dalla Azure Active Directory, viene rimosso anche l'accesso alle sottoscrizioni. 


> [!IMPORTANT]
>
> Per l'utilizzo di gruppi di Azure AD per l'aggiunta di sottoscrittori, si applicano le limitazioni seguenti:
> - L'amministratore deve essere un membro del tenant AAD quando inizialmente aggiunge un gruppo al portale di amministrazione.  Una volta aggiunto il gruppo, le modifiche apportate all'appartenenza dei gruppi non richiedono l'intervento dell'amministratore. 
> - I gruppi devono contenere almeno un membro.  I gruppi vuoti non sono supportati.
> - I gruppi devono avere meno di 1.000 utenti. 
> - Tutti gli utenti devono trovarsi nel primo livello del gruppo.  I gruppi annidati non sono supportati.
> - Sono supportati solo i contratti attendibili.
> - Tutti i membri del gruppo devono avere un indirizzo di posta elettronica associato all'account Azure AD.
> - Gli indirizzi di posta elettronica separati per le notifiche non sono supportati per le sottoscrizioni aggiunte con Azure AD gruppi.  

Guardare questo video o leggere per altre informazioni sull'aggiunta di sottoscrittori con la funzionalità gruppo di Azure Active Directory. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Accedere al portale di amministrazione delle sottoscrizioni di Visual Studio all'indirizzo [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Per aggiungere più sottoscrittori contemporaneamente, passare alla scheda **Gestisci sottoscrittori** .

3. Scegliere la scheda **Aggiungi** , quindi selezionare **Azure Active Directory gruppo** nell'elenco a discesa.  

   > [!div class="mx-imgBorder"]
   > ![Scegliere Aggiungi in blocco utilizzando Azure AD](_img/assign-license-bulk/bulk-add-aad.png "Scegliere la funzionalità Aggiungi in blocco utilizzando Azure AD per eseguire il pull dei sottoscrittori dal gruppo di Azure Active Directory.")

4. Iniziare a immettere il nome del gruppo di Azure AD che si desidera aggiungere nel campo del modulo. Verrà cercata nei gruppi di Azure AD disponibili all'interno dell'organizzazione. 

5. Quando si seleziona il gruppo, il campo viene popolato automaticamente con il nome del gruppo. Sarà possibile visualizzare gli utenti del gruppo prima di aggiungerli. Successivamente, è possibile scegliere il livello di sottoscrizione, i diritti di download e le preferenze di comunicazione per il gruppo. Se lo si desidera, è possibile aggiungere dettagli nel campo di riferimento. 

   > [!div class="mx-imgBorder"]
   > ![Scegliere il gruppo di Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png "Scegliere il nome del gruppo di Azure AD per aggiungere i sottoscrittori del gruppo.")

6. Selezionare **Aggiungi** e quindi **conferma**. 

7. Per visualizzare il gruppo aggiunto, scorrere fino alla fine dell'elenco di utenti.  

8. Selezionare **Visualizza sottoscrittori** per visualizzare i membri del gruppo. È possibile visualizzare i dettagli relativi ai sottoscrittori nel gruppo, ma non è possibile apportare modifiche ai sottoscrittori o alle sottoscrizioni a cui sono assegnati.    

> [!NOTE]
> Se sono già state assegnate sottoscrizioni individualmente agli utenti aggiunti successivamente come parte di un gruppo di Azure AD, verranno aggiunte come parte del gruppo e non verranno più elencate singolarmente. Tuttavia, se la sottoscrizione singola è per un livello di sottoscrizione diverso, avranno due sottoscrizioni.  Esempio: se un utente dispone di un singolo Visual Studio Professional sottoscrizione e è membro di un gruppo a cui si assegnano Visual Studio Enterprise sottoscrizioni, avranno entrambi.  


## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>D: è possibile scegliere più livelli di abbonamento da assegnare all'interno di un gruppo di Azure AD? 
R: No, tutti gli utenti del gruppo ricevono la stessa sottoscrizione. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>D: è possibile modificare i dettagli del Sottoscrittore dei singoli utenti aggiunti in un gruppo di Azure AD?  
R: No. per modificare le informazioni per un singolo Sottoscrittore, è necessario rimuoverle dal gruppo di sicurezza Azure AD e assegnare loro una sottoscrizione singolarmente.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>D: è stato aggiunto un utente al gruppo di sicurezza Azure AD, ma non è stato aggiunto nel portale di amministrazione delle sottoscrizioni e non è presente una sottoscrizione. Perché no?  
R: a seconda del modo in cui l'organizzazione ha configurato Azure AD, è possibile che vengano visualizzati ritardi fino a 24 ore prima che l'utente venga aggiunto. Se la durata è superiore a 24 ore, [contattare il supporto tecnico](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere solo uno o due sottoscrittori,  vedere [Aggiungere singoli utenti](assign-license.md)
- Serve aiuto? Contattare il [supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).