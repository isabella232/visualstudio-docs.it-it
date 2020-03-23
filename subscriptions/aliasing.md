---
title: Possibili errori di accesso alle sottoscrizioni di Visual Studio con alias | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: Si possono verificare errori di accesso se si usano alias o nomi descrittivi
ms.openlocfilehash: 0f5ed4fe67dbd863a7ba4c22f10946cbeb1c36b0
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509057"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>L'accesso alle sottoscrizioni di Visual Studio potrebbe non riuscire quando si usano alias
A seconda del tipo di account utilizzato per l'accesso, le [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)sottoscrizioni disponibili potrebbero non essere visualizzate correttamente quando si accede a . Una delle possibili cause è l'uso di "alias" o "nomi descrittivi" al posto dell'identità di accesso a cui è assegnata la sottoscrizione. Questa situazione viene chiamata "aliasing".

## <a name="what-is-aliasing"></a>Il termine "aliasing"
indica utenti che usano identità diverse per accedere a Windows (o al servizio Active Directory) e per accedere alla posta elettronica.

Si riscontra l'uso dell'aliasing quando una società usa un servizio Microsoft Online per l'accesso alla directory, ad esempio 'JohnD@contoso.com', ma gli utenti accedono ai propri account di posta elettronica tramite alias o nomi descrittivi, ad esempio 'John.Doe@contoso.com'. Assicurarsi che gli utenti utilizzino l'"Indirizzo di posta https://manage.visualstudio.com elettronica di accesso" come indicato nel portale di amministrazione in cui accedere alle sottoscrizioni. 

## <a name="what-are-the-potential-issues"></a>Quali sono i potenziali problemi?

A seconda del tipo di account dell'abbonato, potrebbero riscontrare uno dei due problemi. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problema di mancata corrispondenza UPN dell'account aziendale o dell'istituto di istruzione 
Una mancata corrispondenza UPN può essere rilevata quando una società dispone di un Active Directory impostato in cui il UserPrincipalName (UPN) non corrisponde all'indirizzo SMTP primario. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Come rilevare se l'indirizzo di accesso è interessato da una mancata corrispondenza UPN 

1. Accedere https://my.visualstudio.com/subscriptions utilizzando l'indirizzo di accesso indicato nell'e-mail di assegnazione della sottoscrizione.

2. Verificare che l'indirizzo di posta elettronica di accesso elencato nella parte superiore destra della pagina corrisponda all'indirizzo utilizzato per l'accesso.  In caso contrario, l'UPN non corrisponde e non sarà possibile visualizzare l'abbonamento. 

> [!div class="mx-imgBorder"]
> ![Indirizzo di posta elettronica di accesso](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>Come correggere una mancata corrispondenza UPN

1. Accedere al portale di gestione dell'amministrazione di Visual StudioAccess the Visual Studio Administration Management portal[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Individuare il sottoscrittore con il problema di mancata corrispondenza UPN. La funzione [Filtro](search-license.md) può semplificare la ricerca di un sottoscrittore.

3. Modificare l'indirizzo di posta elettronica di accesso in UPN del sottoscrittore 

0. Salvare le modifiche 

0. Informare l'abbonato di disconnettersi dal portale per gli abbonati e accedere nuovamente tramite l'UPN 

### <a name="personal-account-aliasing-issue"></a>Problema di aliasing dell'account personale

Gli account di sottoscrizione personali possono verificarsi problemi anche se l'indirizzo di posta elettronica usato per accedere al portale delle sottoscrizioni di Visual Studio non corrisponde all'indirizzo di posta elettronica associato alla sottoscrizione. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Come rilevare se l'account dell'abbonamento personale è interessato da un problema di aliasing

1. Accedi a[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Verificare che l'indirizzo di posta elettronica di accesso elencato nella parte superiore destra della pagina corrisponda all'indirizzo utilizzato per l'accesso.  Se l'indirizzo e-mail di accesso non corrisponde all'indirizzo e-mail utilizzato per accedere al sito Web, si verifica un conflitto tra l'account e l'alias.

#### <a name="how-to-fix-an-alias-issue"></a>Come risolvere un problema relativo all'alias

La piattaforma di Visual Studio assegna la priorità all'alias principale per visualizzare i dettagli della sottoscrizione. 

1. Passare a **Gestire la modalità**di accesso a Microsoft . Se richiesto, accedi al tuo account Microsoft. 

2. In Alias account selezionare **Rendi principale** accanto all'indirizzo di posta elettronica utilizzato per assegnare la sottoscrizione. 

> [!div class="mx-imgBorder"]
> ![Impostare l'indirizzo di posta elettronica principale](_img//aliasing/account-aliases.png)

3. Disconnettersi dal portale delle sottoscrizioni di Visual Studio (https://my.visualstudio.com) 

4. Accedere di nuovo utilizzando l'account utilizzato per assegnare la sottoscrizione che deve ora essere configurata come alias primario. 

## <a name="preventing-aliasing-issues"></a>Prevenzione dei problemi di aliasing

In qualità di amministratore, sono disponibili due opzioni per garantire [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)che gli abbonati abbiano un'esperienza di accesso corretta su .
- La prima opzione (scelta consigliata) consiste nell'utilizzare l'account di https://my.visualstudio.comdirectory come accesso per il portale delle sottoscrizioni di Visual Studio in .  
- La seconda opzione (meno sicura), consiste nel consentire ai sottoscrittori di accedere utilizzando un indirizzo di posta elettronica diverso da quello dell'indirizzo di posta elettronica della directory.

Entrambe queste opzioni vengono configurate nel portale di amministrazione completando i passaggi seguenti:  
1. Accedi[https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Se si modifica un singolo utente, selezionarlo nella tabella e fare clic con il pulsante destro del mouse per modificare. Si aprirà un pannello in cui è possibile modificare l'indirizzo di posta elettronica di accesso. Apportare gli aggiornamenti necessari nel campo dell'indirizzo di posta elettronica di accesso. Fare clic su Salva per rendere effettive le modifiche.  

0. Se è necessario apportare queste modifiche a una grande quantità di utenti, è possibile utilizzare la funzionalità di modifica in blocco. Per altre informazioni, leggi l'articolo [Modificare più sottoscrittori utilizzando la modifica in blocco.](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit)

> [!NOTE]
> Per le modifiche individuali e collettive, gli abbonati riceveranno un'e-mail con le istruzioni che l'indirizzo di posta elettronica di accesso è stato modificato e dovranno accedere utilizzando l'indirizzo di posta elettronica aggiornato. È inoltre importante notare che se il sottoscrittore ha attivato in precedenza i vantaggi con l'altro indirizzo di accesso, dovrà continuare a utilizzare l'altro indirizzo di accesso per accedervi.  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione delle sottoscrizioni di Visual Studio.Learn more about managing Visual Studio subscriptions.
- [Assegnare singole sottoscrizioniAssign individual subscriptions](assign-license.md)
- [Assegnare più sottoscrizioniAssign multiple subscriptions](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Determinare l'utilizzo massimoDetermine maximum usage](maximum-usage.md)


