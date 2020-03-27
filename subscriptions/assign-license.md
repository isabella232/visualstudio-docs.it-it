---
title: Assegnare licenze a sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: Informazioni su come gli amministratori possono assegnare licenze ai sottoscrittori
ms.openlocfilehash: 87334251532dbaa127d4def8c33a9814c28d42e1
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232714"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Assegnare licenze nel portale di amministrazione delle sottoscrizioni di Visual Studio
In qualità di amministratore delle sottoscrizioni di Visual Studio, è possibile usare il portale di amministrazione per assegnare sottoscrizioni a singoli utenti e gruppi di utenti.

Per gruppi di utenti, è possibile scegliere la modalità di assegnazione delle sottoscrizioni.  
- È possibile assegnare le sottoscrizioni una alla volta.
- È inoltre possibile caricare rapidamente e facilmente elenchi di abbonati e le relative informazioni di sottoscrizione utilizzando la funzionalità [di aggiunta in blocco.](assign-license-bulk.md)
- Se l'organizzazione usa Microsoft Azure Active Directory (Azure AD), è possibile usare i gruppi di Azure AD per assegnare sottoscrizioni a gruppi di utenti.  Questa funzionalità viene distribuita in fasi e potrebbe non essere immediatamente disponibile per l'organizzazione.


## <a name="add-a-single-subscriber"></a>Aggiungere un singolo sottoscrittore
Ecco come assegnare una sottoscrizione di Visual Studio a un nuovo utente in modo che possa accedere ai vantaggi della sottoscrizione.

1. Accedere al [portale di amministrazione](https://manage.visualstudio.com).
2. Per assegnare una licenza a un singolo sottoscrittore di Visual Studio, nella parte superiore della tabella selezionare **Aggiungi**, quindi **Sottoscrittore singolo**.
   > [!div class="mx-imgBorder"]
   > ![Aggiungere un singolo sottoscrittore](_img/assign-license-add/add-subscriber-individual.png)
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

## <a name="resend-assignment-emails"></a>Inviare di nuovo i messaggi di posta elettronica di assegnazione
Dopo aver aggiunto un sottoscrittore, un messaggio di posta elettronica di assegnazione verrà inviato automaticamente al nuovo sottoscrittore con ulteriori istruzioni. È possibile inviare nuovamente l'e-mail di assegnazione in qualsiasi momento selezionando l'abbonato e facendo clic sul pulsante **Invia di nuovo** nel menu in alto.  Per inviare di nuovo i messaggi di posta elettronica a più utenti, tenere premuto **CTRL** mentre si selezionano gli iscritti.  Quando fai clic sul pulsante **Invia di nuovo,** vedrai una finestra di dialogo che ti chiede di confermare che desideri inviare di nuovo a tali sottoscrittori.  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere molti utenti,  vedere le informazioni su come assegnare sottoscrizioni a [più sottoscrittori](assign-license-bulk.md).
- Richiesta di assistenza  Contattare il [supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).


