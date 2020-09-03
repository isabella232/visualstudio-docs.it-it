---
title: Impostare le preferenze per il contratto nel portale di amministrazione
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 03/17/2020
ms.topic: conceptual
description: Informazioni su come impostare le preferenze per la lingua, i contatti, il livello di sottoscrizione e altre opzioni nel portale di amministrazione
ms.openlocfilehash: e34b9cf1ed32abc81b9c2ebb3ef7c370818c9089
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "87234614"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Impostare le preferenze per i contratti nel portale di amministrazione
Gli amministratori con privilegi avanzati possono impostare determinate preferenze nel portale di amministrazione (portale di amministrazione) che verrà applicato globalmente per ogni contratto.  Queste preferenze compileranno automaticamente i dettagli della sottoscrizione per gli amministratori durante l'aggiunta di sottoscrittori e potranno essere modificati solo a livello globale dagli amministratori con privilegi avanzati.  

## <a name="access-preferences"></a>Preferenze di accesso
Per visualizzare o modificare le preferenze, è necessario aver eseguito l'accesso al [portale di amministrazione](https://manage.visualstudio.com) con un ID di accesso con diritti di amministratore con privilegi avanzati per il contratto.  

Per impostare le preferenze:
1. Accedere al portale di amministrazione con un ID con privilegi di amministratore con privilegi avanzati.
2. Fare clic sulla scheda **Manage Administrators** (Gestisci amministratori).
   > [!div class="mx-imgBorder"]
   > ![Pulsante Admin Preferences (Preferenze amministratore)](_img/admin-prefs/admin-prefs-button.png "Fare clic su Gestisci amministratori e quindi su Preferenze accordo per visualizzare le preferenze")

3. Fare clic su **Agreement Preferences** (Preferenze per i contratti).
Verrà aperto un pannello a destra e verranno visualizzate le preferenze disponibili. 

   > [!div class="mx-imgBorder"]
   > ![Finestra di dialogo a comparsa Admin Preferences (Preferenze amministratore)](_img/admin-prefs/admin-prefs-flyout.png "Imposta le preferenze e fai clic su Salva")

## <a name="set-your-preferences"></a>Impostare le preferenze
Verranno illustrate di eseguito tutte le preferenze disponibili e i relativi effetti. 

### <a name="agreement"></a>Contratto
Gli amministratori con privilegi avanzati di più contratti potranno scegliere il contratto desiderato nell'elenco a discesa.  Le preferenze impostate verranno applicate solo al contratto selezionato.  I singoli amministratori possono sostituire alcune di queste preferenze caso per caso durante l'assegnazione delle sottoscrizioni. 

Se esiste un solo contratto associato all'indirizzo di posta elettronica usato per l'accesso, verrà visualizzato tale contratto e l'elenco a discesa sarà disabilitato. 

### <a name="contact-email-address"></a>Contact email address (Indirizzo di posta elettronica del contatto)
Questa preferenza consente ai sottoscrittori di contattare gli amministratori tramite il pulsante **Contatta l'amministratore** della [pagina Sottoscrizioni](https://my.visualstudio.com/subscriptions) del portale Sottoscrittore.  Se questa preferenza viene lasciata vuota, i messaggi del sottoscrittore verranno inoltrati a tutti gli amministratori e agli amministratori con privilegi avanzati per il contratto.  È consigliabile usare un alias di posta elettronica di gruppo o un gruppo di sicurezza per personalizzare i destinatari per questo indirizzo di posta elettronica di contatto. Se lo si preferisce, è anche possibile scegliere di immettere l'indirizzo di posta elettronica di un singolo utente.

> [!NOTE]
> L'indirizzo di posta elettronica qui indicato NON verrà fornito ai sottoscrittori.  Quando un Sottoscrittore invia una richiesta **Contatta l'amministratore** nel portale per i sottoscrittori, il messaggio verrà inoltrato all'alias senza esporlo al Sottoscrittore. 

### <a name="default-external-subscribers-setting"></a>Default external subscribers setting (Impostazione predefinita per i sottoscrittori esterni)
Questa preferenza consente di decidere se gli amministratori possono aggiungere sottoscrittori dall'esterno del tenant o della directory dell'organizzazione.  Se si disattiva questa opzione, non sarà consentito alcun sottoscrittore esterno.  Se viene abilitata e un amministratore tenta di aggiungere un sottoscrittore esterno, verrà chiesto di confermare la scelta e sarà consentita l'assegnazione della sottoscrizione. Gli amministratori non possono eseguire l'override di questa impostazione. 

### <a name="default-downloads-setting"></a>Default downloads setting (Impostazione predefinita per i download)
L'abilitazione di questa impostazione, attivata per impostazione predefinita, consentirà ai sottoscrittori di accedere ai download quando gli amministratori creano nuove sottoscrizioni.  Gli amministratori possono comunque disabilitare i download per singole sottoscrizioni.  Disabilitando l'accesso ai download viene disabilitato anche l'accesso ai codici Product Key.  

### <a name="default-subscription-level"></a>Default subscription level (Livello di sottoscrizione predefinito)
È possibile usare questa impostazione per determinare quali livelli di sottoscrizione inclusi nel contratto vengono selezionati per impostazione predefinita quando una sottoscrizione viene assegnata a un utente.  Gli amministratori possono modificare l'impostazione per qualsiasi livello di sottoscrizione nel contratto, evitando così di dover effettuare ripetutamente la scelta più comune. 

### <a name="default-communication-preferences"></a>Default communication preferences (Preferenze predefinite per le comunicazioni)
L'impostazione di una lingua e di impostazioni locali predefinite per le comunicazioni può semplificare il processo di assegnazione delle sottoscrizioni.  Ad esempio, se il team di sviluppo si trova in un paese diverso da quello del team di amministrazione, è possibile impostare le preferenze più adatte alla località dei sottoscrittori. Queste impostazioni possono comunque essere modificate da tutti gli amministratori per i singoli sottoscrittori. 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>D: è possibile disabilitare l' **indirizzo di posta elettronica di contatto** per consentire ai sottoscrittori di contattare gli amministratori?
R: No. è possibile determinare gli amministratori contattati usando un gruppo di sicurezza, un alias di posta elettronica di gruppo o un indirizzo di posta elettronica singolo. la funzionalità non può essere disabilitata.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>D: se si risponde a un messaggio di posta elettronica di un Sottoscrittore, avrà l'indirizzo di posta elettronica?
R: dal momento che la risposta proverrà dal client di posta elettronica in uso, la risposta ricevuta dal Sottoscrittore visualizzerà l'indirizzo di posta elettronica in uso.  Se si risponde da un alias di gruppo, il sottoscrittore vedrà l'alias del gruppo  e se si risponde con il proprio indirizzo di posta elettronica, il destinatario vedrà questo indirizzo.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>D: dove è possibile reperire altre informazioni sulla funzionalità **Contatta l'amministratore** nel portale per gli abbonati?
R: consultare l'articolo [contattare l'amministratore](contact-my-admin.md) . 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>D: se non si completa l' **indirizzo di posta elettronica di contatto** e un Sottoscrittore usa la funzionalità **Contatta l'amministratore** , che riceve la richiesta?
R: se non è stato impostato alcun indirizzo di posta elettronica specifico nella preferenza dell' **indirizzo di posta elettronica di contatto** , tutti gli amministratori del contratto riceveranno la richiesta. 

## <a name="resources"></a>Risorse
- [Supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione delle sottoscrizioni di Visual Studio.
- [Assegna singole sottoscrizioni](assign-license.md)
- [Assegna più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)
