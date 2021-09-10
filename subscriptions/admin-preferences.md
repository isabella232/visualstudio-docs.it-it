---
title: Impostare le preferenze nel portale di amministrazione Visual Studio sottoscrizioni
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 05/18/2021
ms.topic: conceptual
description: Informazioni su come impostare le preferenze per la lingua, i contatti, il livello di sottoscrizione e altre opzioni nel portale di amministrazione
ms.openlocfilehash: 348febd6b964feec54053cff4a3d50cc02eba3d0
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123965487"
---
# <a name="set-preferences-for-your-agreements-in-the-admin-portal"></a>Impostare le preferenze per i contratti nel portale di amministrazione
Gli amministratori con privilegi super possono impostare determinate preferenze nel portale di amministrazione (portale di amministrazione) che verranno applicate a livello globale per ogni contratto.  Queste preferenze popolano automaticamente i dettagli della sottoscrizione per gli amministratori quando aggiungono sottoscrittori e possono essere modificate solo a livello globale dagli amministratori con privilegi più importanti.  

## <a name="access-preferences"></a>Preferenze di accesso
Per visualizzare o modificare le preferenze, è necessario aver eseguito l'accesso al [portale di amministrazione](https://manage.visualstudio.com) con un ID di accesso con diritti di amministratore con privilegi avanzati per il contratto.  

Per impostare le preferenze:
1. Accedere al portale di amministrazione con un ID con privilegi di amministratore con privilegi avanzati.
2. Fare clic sull'icona dell'impostazione nel riquadro sinistro.
   > [!div class="mx-imgBorder"]
   > ![Pulsante Admin Preferences (Preferenze amministratore)](_img/admin-preferences/admin-preferences-button.png "Fare clic su Manage Administrators (Gestisci amministratori) e quindi su Agreement Preferences (Preferenze contratto) per visualizzare le preferenze")

3. Fare clic su **Agreement Preferences** (Preferenze per i contratti).
Verrà aperto un pannello a sinistra e verranno visualizzate le preferenze disponibili. 

   > [!div class="mx-imgBorder"]
   > ![Finestra di dialogo a comparsa Admin Preferences (Preferenze amministratore)](_img/admin-preferences/admin-preferences-flyout-2.png "Impostare le preferenze e fare clic su Salva")

## <a name="set-your-preferences"></a>Impostare le preferenze
Verranno illustrate di eseguito tutte le preferenze disponibili e i relativi effetti. 

### <a name="agreement"></a>Contratto
Se si dispone di più contratti per i quali si è un amministratore con privilegi super, sarà possibile scegliere il contratto desiderato nell'elenco a discesa a destra del pannello delle impostazioni espanso.  Le preferenze impostate verranno applicate solo al contratto selezionato.  I singoli amministratori possono sostituire alcune di queste preferenze caso per caso durante l'assegnazione delle sottoscrizioni. 

Se è presente un solo contratto associato all'indirizzo di posta elettronica usato per accedere, verrà visualizzato a destra del pannello delle impostazioni espanso e l'elenco a discesa verrà disabilitato. 

### <a name="contact-email-address"></a>Contact email address (Indirizzo di posta elettronica del contatto)
Questa preferenza consente ai sottoscrittori di contattare gli amministratori tramite  il pulsante Contatta [](https://my.visualstudio.com/subscriptions) l'amministratore nella pagina delle sottoscrizioni del portale per i sottoscrittori.  Se questa preferenza viene lasciata vuota, i messaggi del sottoscrittore verranno inoltrati a tutti gli amministratori e agli amministratori con privilegi super per il contratto.  È consigliabile usare un alias di posta elettronica di gruppo o un gruppo di sicurezza per personalizzare i destinatari per questo indirizzo di posta elettronica di contatto. Se lo si preferisce, è anche possibile scegliere di immettere l'indirizzo di posta elettronica di un singolo utente.

> [!NOTE]
> L'indirizzo di posta elettronica qui indicato NON verrà fornito ai sottoscrittori.  Quando un sottoscrittore invia una richiesta **Contatta** l'amministratore nel portale per i sottoscrittori, il messaggio verrà inoltrato all'alias senza esporlo al sottoscrittore. 

### <a name="default-subscription-level"></a>Default subscription level (Livello di sottoscrizione predefinito)
È possibile usare questa impostazione per determinare quali livelli di sottoscrizione inclusi nel contratto vengono selezionati per impostazione predefinita quando una sottoscrizione viene assegnata a un utente.  Gli amministratori possono modificare l'impostazione a qualsiasi livello di sottoscrizione nel contratto, in modo da evitare di dover effettuare ripetutamente la scelta più comune. 

### <a name="default-communication-preferences"></a>Default communication preferences (Preferenze predefinite per le comunicazioni)
L'impostazione di una lingua e di impostazioni locali predefinite per le comunicazioni può semplificare il processo di assegnazione delle sottoscrizioni.  Ad esempio, se il team di sviluppo si trova in un paese diverso da quello del team di amministrazione, è possibile impostare le preferenze più adatte alla località dei sottoscrittori. Queste impostazioni possono comunque essere modificate da tutti gli amministratori per i singoli sottoscrittori. 

### <a name="default-external-subscribers-setting"></a>Default external subscribers setting (Impostazione predefinita per i sottoscrittori esterni)
Questa preferenza consente di decidere se gli amministratori possono aggiungere sottoscrittori dall'esterno del tenant o della directory dell'organizzazione.  Se si disattiva questa opzione, non sarà consentito alcun sottoscrittore esterno.  Se viene abilitata e un amministratore tenta di aggiungere un sottoscrittore esterno, verrà chiesto di confermare la scelta e sarà consentita l'assegnazione della sottoscrizione. Gli amministratori non possono sostituire questa impostazione. 

### <a name="default-downloads-setting"></a>Default downloads setting (Impostazione predefinita per i download)
L'abilitazione di questa impostazione, attivata per impostazione predefinita, consentirà ai sottoscrittori di accedere ai download quando gli amministratori creano nuove sottoscrizioni.  Gli amministratori possono comunque disabilitare i download per singole sottoscrizioni.  La disabilitazione dell'accesso ai download disabilita anche l'accesso ai codici Product Key.  

### <a name="overallocation-notification"></a>Notifica di sovrallocazione 
Acconsentire esplicitamente a ricevere un messaggio di posta elettronica quando le assegnazioni nel contratto vengono sovrassegnate. Questa notifica di posta [](admin-preferences.md#contact-email-address)elettronica verrà inviata all'indirizzo di posta elettronica del contatto o a tutti gli amministratori del contratto se non è presente un indirizzo di posta elettronica di contatto. Usare il menu a discesa per configurare la soglia a cui si desidera ricevere una notifica. 

 
## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>D: È possibile disabilitare **l'indirizzo di posta elettronica di contatto in** modo che i sottoscrittori non possano contattare gli amministratori?
A: No: anche se è possibile determinare quali amministratori vengono contattati usando un gruppo di sicurezza, un alias di posta elettronica del gruppo o un singolo indirizzo di posta elettronica, la funzionalità non può essere disabilitata.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>D: Se si risponde al messaggio di posta elettronica di un sottoscrittore, l'utente avrà l'indirizzo di posta elettronica?
A: Poiché la risposta verrà inviata da qualsiasi client di posta elettronica in uso, la risposta ricevuta dal sottoscrittore mostrerà l'indirizzo di posta elettronica in uso.  Se si risponde da un alias di gruppo, il sottoscrittore vedrà l'alias del gruppo  e se si risponde con il proprio indirizzo di posta elettronica, il destinatario vedrà questo indirizzo.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>D: Dove è possibile trovare altre informazioni sulla funzionalità Contatta l'amministratore **nel** portale per i sottoscrittori?
A: Vedere [l'articolo Contattare l'amministratore.](contact-my-admin.md) 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>D: Se non si completa l'indirizzo di posta elettronica di **contatto** e un sottoscrittore usa la funzionalità **Contatta** l'amministratore, chi riceve la richiesta?
A: Se nella preferenza Indirizzo  di posta elettronica di contatto non è impostato alcun indirizzo di posta elettronica specifico, tutti gli amministratori del contratto riceveranno la richiesta. 

## <a name="resources"></a>Risorse
- [Visual Studio di amministrazione e sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione Visual Studio sottoscrizioni.
- [Assegnare sottoscrizioni singole](assign-license.md)
- [Assegnare più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)