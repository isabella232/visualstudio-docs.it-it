---
title: Assegnare licenze a gruppi di utenti per sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/26/2020
ms.topic: conceptual
description: Informazioni su come gli amministratori possono assegnare licenze a più sottoscrittori usando la funzionalità di aggiunta in blocco o i gruppi di Microsoft Azure Active Directory
ms.openlocfilehash: ae16c64f90f90b820332e0ee7f1753a8dd6e5c32
ms.sourcegitcommit: a80489d216c4316fde2579a0a2d7fdb54478abdf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652820"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Assegnare sottoscrizioni a più utenti
Il portale di amministrazione delle sottoscrizioni permette di aggiungere utenti uno per volta o in gruppi di grandi dimensioni.  Per aggiungere singoli utenti, vedere [Aggiungere singoli utenti](assign-license.md).

Per aggiungere gruppi di utenti di grandi dimensioni, è possibile utilizzare la funzionalità di aggiunta in blocco o, se l'organizzazione utilizza Microsoft Azure Active Directory (Azure AD), è possibile utilizzare Azure AD gruppi. In questo articolo viene illustrato il processo per entrambe le opzioni. 


## <a name="use-bulk-add-to-assign-subscriptions"></a>Utilizzare Aggiunta bulk per assegnare sottoscrizioni
1. Accedere al portale di amministrazione delle sottoscrizioni di Visual Studio all'https://manage.visualstudio.com.

2. Per aggiungere più sottoscrittori contemporaneamente, passare alla scheda **Gestisci sottoscrittori** . scegliere la scheda **Aggiungi** , quindi scegliere **Aggiungi in blocco** nell'elenco a discesa.  

2. L'aggiunta bulk utilizza un modello di Microsoft Excel per caricare informazioni sul Sottoscrittore. Nella finestra di dialogo Upload Multiple Subscriber (Carica più sottoscrittori), fare clic su **Download** per scaricare il modello.
   > [!div class="mx-imgBorder"]
   > ![Scaricare il modello di Excel per caricare più sottoscrittori](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Scaricare sempre la versione più recente del modello. Se si usa una versione precedente, il caricamento in blocco potrebbe non riuscire.

3. Nel foglio di calcolo Excel compilare i campi con le informazioni per gli utenti a cui si desidera assegnare le sottoscrizioni. (*Reference* è un campo facoltativo). Al termine, salvare il file localmente.

   Per garantire un caricamento senza errori, osservare le procedure consigliate seguenti:

    - Verificare che nessuno dei campi modulo contenga virgole.
    - Rimuovere gli spazi prima e dopo i campi del modulo.
    - Assicurarsi che i nomi degli utenti non contengano spazi aggiuntivi nei nomi o cognomi composti da due parti (se il nome è composto da due parti, ad esempio "Maria Giovanna", digitare "MariaGiovanna" poiché il sistema non annulla lo spazio aggiuntivo).
    - Verificare che tutti i campi obbligatori siano completati. 
    - Controllare la colonna del **messaggio di errore** .  Se vengono elencati errori, risolverli prima di provare a caricare il file. 

4. Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio. Nella finestra di dialogo **Upload Multiple Subscribers** (Carica più sottoscrittori) fare clic su **Sfoglia**.
   > [!div class="mx-imgBorder"]
   > ![Passare al modello salvato per caricare più sottoscrittori](media/bulk-add-browse-saved-template.png)

5. Passare al file Excel salvato e quindi fare clic su **OK**.
   > [!div class="mx-imgBorder"]
   > ![Caricare il modello di Excel per caricare più sottoscrittori](media/bulk-upload-subscribers.png)

    Viene visualizzata una finestra di dialogo di avanzamento del caricamento.

    Se il modello contiene errori, il caricamento avrà esito negativo e verranno visualizzati gli errori per consentire di correggere il modello e tentare nuovamente il caricamento in blocco.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di errore se il caricamento di più sottoscrittori ha esito negativo](media/bulk-add-template-failed.png)

    Quando il caricamento ha esito positivo, viene visualizzato l'elenco di sottoscrittori e un messaggio di conferma.
   > [!div class="mx-imgBorder"]
   > ![Messaggio di conferma se il caricamento di più sottoscrittori ha esito positivo](media/bulk-add-template-success.png)

## <a name="use-azure-ad-groups-to-assign-subscriptions"></a>Usare gruppi di Azure AD per assegnare sottoscrizioni 
L'uso di questa funzionalità consente di mantenere più facilmente le assegnazioni di sottoscrizione. È possibile aggiungere Azure AD gruppi di sicurezza nel portale di amministrazione delle sottoscrizioni, in modo da garantire che a tutti gli utenti del gruppo venga assegnata una sottoscrizione. Per semplificare, quando gli utenti lasciano l'organizzazione e vengono rimossi dalla Azure AD, viene rimosso anche l'accesso alle sottoscrizioni.

> [!NOTE]
> Questa funzionalità viene distribuita in fasi, quindi potrebbe non essere disponibile immediatamente per l'organizzazione.   

> [!IMPORTANT]
> Per l'utilizzo di gruppi di Azure AD per l'aggiunta di sottoscrittori, si applicano le limitazioni seguenti:
> - I gruppi devono contenere almeno un membro.  I gruppi vuoti non sono supportati.
> - I gruppi devono avere meno di 1.000 utenti.
> - Tutti gli utenti devono trovarsi nel primo livello del gruppo.  I gruppi annidati non sono supportati.
> - Sono supportati solo i contratti attendibili.
> - Tutti i membri del gruppo devono avere un indirizzo di posta elettronica associato all'account Azure AD.


1. Accedere al portale di amministrazione delle sottoscrizioni di Visual Studio all' [https://manage.visualstudio.com](https://manage.visualstudio.com).

2. Per aggiungere più sottoscrittori contemporaneamente, passare alla scheda **Gestisci sottoscrittori** .

3. Scegliere la scheda **Aggiungi** , quindi selezionare **Azure Active Directory gruppo** nell'elenco a discesa.  

   > [!div class="mx-imgBorder"]
   > ![scegliere Aggiungi in blocco utilizzando Azure AD](_img/assign-license-bulk/bulk-add-aad.png)


4. Iniziare a immettere il nome del gruppo di Azure AD che si desidera aggiungere nel campo del modulo. Verrà cercata nei gruppi di Azure AD disponibili all'interno dell'organizzazione. 

5. Quando si seleziona il gruppo, il campo viene popolato automaticamente con il nome del gruppo. Sarà possibile visualizzare gli utenti del gruppo prima di aggiungerli. Successivamente, è possibile scegliere il livello di sottoscrizione, i diritti di download e le preferenze di comunicazione per il gruppo. Se lo si desidera, è possibile aggiungere dettagli nel campo di riferimento. 

   > [!div class="mx-imgBorder"]
   > ![scegliere Aggiungi in blocco utilizzando Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Fare clic su **Aggiungi** e quindi su **conferma**. 

7. Per visualizzare il gruppo aggiunto, scorrere fino alla fine dell'elenco di utenti.  

8. Selezionare **Visualizza sottoscrittori** per visualizzare i membri del gruppo. È possibile visualizzare i dettagli relativi ai sottoscrittori nel gruppo, ma non è possibile apportare modifiche ai sottoscrittori o alle sottoscrizioni a cui sono assegnati.    

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>D: è possibile scegliere più livelli di abbonamento da assegnare all'interno di un gruppo di Azure AD? 
R: No, tutti gli utenti del gruppo ricevono la stessa sottoscrizione. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>D: è possibile modificare i dettagli del Sottoscrittore dei singoli utenti aggiunti in un gruppo di Azure AD?  
R: No. per modificare le informazioni per un singolo Sottoscrittore, è necessario rimuoverle dal gruppo di sicurezza Azure AD e assegnare loro una sottoscrizione singolarmente.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>D: è stato aggiunto un utente al gruppo di sicurezza Azure AD, ma non è stato aggiunto nel portale di amministrazione delle sottoscrizioni e non è presente una sottoscrizione. non vengono visualizzati?  
R: a seconda del modo in cui l'organizzazione ha configurato Azure AD, è possibile che vengano visualizzati ritardi fino a 24 ore prima che l'utente venga aggiunto. Se la durata è superiore a 24 ore, [contattare il supporto tecnico](https://visualstudio.microsoft.com/support/support-overview-vs).  


## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere solo uno o due sottoscrittori,  vedere [Aggiungere singoli utenti](assign-license.md)
- Per ulteriori informazioni, vedere contattare il [supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).



