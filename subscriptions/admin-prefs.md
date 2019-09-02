---
title: Impostare le preferenze per il contratto nel portale di amministrazione
author: evanwindom
ms.author: lank
manager: lank
ms.date: 08/21/2019
ms.topic: conceptual
description: Informazioni su come impostare le preferenze per la lingua, i contatti, il livello di sottoscrizione e altre opzioni nel portale di amministrazione
ms.openlocfilehash: 24e9ddfa92ee63e4d15eea086224e1069d4bcbc8
ms.sourcegitcommit: c90a998716b3dfa614dedc61a1bea515364efbec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000981"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Impostare le preferenze per i contratti nel portale di amministrazione
Gli amministratori con privilegi avanzati possono ora impostare determinate preferenze nel portale di amministrazione, che verranno applicate globalmente per ogni contratto.  Queste preferenze determineranno ciò che gli amministratori dei contratti possono impostare quando aggiungono sottoscrittori e possono essere modificate solo a livello globale dagli amministratori con privilegi avanzati.  

## <a name="access-preferences"></a>Preferenze di accesso
Per visualizzare o modificare le preferenze, è necessario aver eseguito l'accesso al [portale di amministrazione](https://manage.visualstudio.com) con un ID di accesso con diritti di amministratore con privilegi avanzati per il contratto.  

Per impostare le preferenze:
1. Accedere al portale di amministrazione con un ID con privilegi di amministratore con privilegi avanzati.
2. Fare clic sulla scheda **Manage Administrators** (Gestisci amministratori).
   > [!div class="mx-imgBorder"]
   > ![Pulsante Admin Preferences (Preferenze amministratore)](_img/admin-prefs/admin-prefs-button.png)

3. Fare clic su **Agreement Preferences** (Preferenze per i contratti).
Verrà aperto un pannello a destra e verranno visualizzate le preferenze disponibili. 

   > [!div class="mx-imgBorder"]
   > ![Finestra di dialogo a comparsa Admin Preferences (Preferenze amministratore)](_img/admin-prefs/admin-prefs-flyout.png)

## <a name="set-your-preferences"></a>Impostare le preferenze
Verranno illustrate di eseguito tutte le preferenze disponibili e i relativi effetti. 

### <a name="agreement"></a>Contratto
Gli amministratori con privilegi avanzati di più contratti potranno scegliere il contratto desiderato nell'elenco a discesa.  Le preferenze impostate verranno applicate solo al contratto selezionato.  I singoli amministratori possono sostituire alcune di queste preferenze caso per caso durante l'assegnazione delle sottoscrizioni. 

Se esiste un solo contratto associato all'indirizzo di posta elettronica usato per l'accesso, verrà visualizzato tale contratto e l'elenco a discesa sarà disabilitato. 

### <a name="contact-email-address"></a>Contact email address (Indirizzo di posta elettronica del contatto)
Questa preferenza consente ai sottoscrittori di contattare gli amministratori tramite il pulsante **Contact my Admin** (Contatta amministratore) nella [pagina delle sottoscrizioni](https://my.visualstudio.com/subscriptions) del portale dei sottoscrittori.  Se questa preferenza viene lasciata vuota, i messaggi del sottoscrittore verranno inoltrati a tutti gli amministratori e agli amministratori con privilegi avanzati per il contratto.  È consigliabile usare un alias di posta elettronica di gruppo o un gruppo di sicurezza per personalizzare i destinatari per questo indirizzo di posta elettronica di contatto. Se lo si preferisce, è anche possibile scegliere di immettere l'indirizzo di posta elettronica di un singolo utente.

> [!NOTE]
> L'indirizzo di posta elettronica qui indicato NON verrà fornito ai sottoscrittori.  Quando un sottoscrittore invia una richiesta **Contact my Admin** (Contatta amministratore) nel portale dei sottoscrittori, il messaggio verrà inoltrato all'alias senza esporlo ai sottoscrittori. 

### <a name="default-external-subscribers-setting"></a>Default external subscribers setting (Impostazione predefinita per i sottoscrittori esterni)
Questa preferenza consente di decidere se gli amministratori possono aggiungere sottoscrittori dall'esterno del tenant o della directory dell'organizzazione.  Se si disattiva questa opzione, non sarà consentito alcun sottoscrittore esterno.  Se viene abilitata e un amministratore tenta di aggiungere un sottoscrittore esterno, verrà chiesto di confermare la scelta e sarà consentita l'assegnazione della sottoscrizione. Gli amministratori non possono sostituire questa impostazione. 

### <a name="default-downloads-setting"></a>Default downloads setting (Impostazione predefinita per i download)
L'abilitazione di questa impostazione, attivata per impostazione predefinita, consentirà ai sottoscrittori di accedere ai download quando gli amministratori creano nuove sottoscrizioni.  Gli amministratori possono comunque disabilitare i download per singole sottoscrizioni.  

### <a name="default-subscription-level"></a>Default subscription level (Livello di sottoscrizione predefinito)
È possibile usare questa impostazione per determinare quali livelli di sottoscrizione inclusi nel contratto vengono selezionati per impostazione predefinita quando una sottoscrizione viene assegnata a un utente.  Gli amministratori possono modificare l'impostazione per qualsiasi livello di sottoscrizione nel contratto, evitando così di dover effettuare ripetutamente la scelta più comune. 

### <a name="default-communication-preferences"></a>Default communication preferences (Preferenze predefinite per le comunicazioni)
L'impostazione di una lingua e di impostazioni locali predefinite per le comunicazioni può semplificare il processo di assegnazione delle sottoscrizioni.  Ad esempio, se il team di sviluppo si trova in un paese diverso da quello del team di amministrazione, è possibile impostare le preferenze più adatte alla località dei sottoscrittori. Queste impostazioni possono comunque essere modificate da tutti gli amministratori per i singoli sottoscrittori. 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>D:  È possibile disabilitare **Contact email address** (Indirizzo di posta elettronica del contatto) in modo che i sottoscrittori non possano contattare gli amministratori?
R:  No. Anche se è possibile determinare quali amministratori vengono contattati usando un gruppo di sicurezza, un alias di posta elettronica di gruppo o un singolo indirizzo di posta elettronica, la funzionalità non può essere disabilitata.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>D: Se si risponde a un messaggio di posta elettronica di un sottoscrittore, l'indirizzo di posta elettronica del mittente sarà visibile?
R:  Dato che la risposta proverrà dal client di posta elettronica usato, nella risposta ricevuta dal sottoscrittore sarà visualizzato l'indirizzo di posta elettronica usato.  Se si risponde da un alias di gruppo, il sottoscrittore vedrà l'alias del gruppo  e se si risponde con il proprio indirizzo di posta elettronica, il destinatario vedrà questo indirizzo.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>D: Dove è possibile reperire altre informazioni sulla funzionalità **Contact my Admin** (Contatta amministratore) nel portale dei sottoscrittori?
R:  Vedere l'articolo [Ottenere assistenza dall'amministratore delle sottoscrizioni](contact-my-admin.md). 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>D: Se non si completa il campo **Contact email address** (Indirizzo di posta elettronica del contatto) e un sottoscrittore usa la funzionalità **Contact my Admin** (Contatta amministratore), chi riceve la richiesta?
R:  Se nella preferenza **Contact email address** (Indirizzo di posta elettronica del contatto) non viene impostato alcun indirizzo di posta elettronica specifico, tutti gli amministratori del contratto riceveranno la richiesta. 

## <a name="resources"></a>Risorse
- [Supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="next-steps"></a>Passaggi successivi
- Vedere come [assegnare le sottoscrizioni](assign-license.md)
- Vedere altre informazioni su tutti i [vantaggi della sottoscrizione](https://visualstudio.microsoft.com/vs/benefits/)

