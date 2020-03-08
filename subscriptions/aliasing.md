---
title: Possibili errori di accesso alle sottoscrizioni di Visual Studio con alias | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Si possono verificare errori di accesso se si usano alias o nomi descrittivi
ms.openlocfilehash: 53b277296e6923bb78717bb76a0c20d2861c29ce
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865388"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>L'accesso alle sottoscrizioni di Visual Studio potrebbe non riuscire quando si usano gli alias
A seconda del tipo di account usato per l'accesso, le sottoscrizioni disponibili potrebbero non essere visualizzate correttamente quando si accede a [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Una delle possibili cause è l'uso di "alias" o "nomi descrittivi" al posto dell'identità di accesso a cui è assegnata la sottoscrizione. Questa situazione viene chiamata "aliasing".

## <a name="what-is-aliasing"></a>Il termine "aliasing"
indica utenti che usano identità diverse per accedere a Windows (o al servizio Active Directory) e per accedere alla posta elettronica.

Si riscontra l'uso dell'aliasing quando una società usa un servizio Microsoft Online per l'accesso alla directory, ad esempio 'JohnD@contoso.com', ma gli utenti accedono ai propri account di posta elettronica tramite alias o nomi descrittivi, ad esempio 'John.Doe@contoso.com'. Per molti clienti che gestiscono le sottoscrizioni tramite Volume Licensing Service Center (VLSC), questo può causare errori durante l'esperienza di accesso perché l'indirizzo di posta elettronica specificato (John.Doe@contoso.com) non corrisponde all'indirizzo della directory (JohnD@contoso.com) richiesto per completare l'autenticazione tramite l'opzione "Account aziendale o dell'istituto di istruzione".  Assicurarsi che gli utenti utilizzino l'indirizzo di posta elettronica di accesso come elencato nel portale di amministrazione all'https://manage.visualstudio.com per accedere alle sottoscrizioni. 

## <a name="what-are-the-potential-issues"></a>Quali sono i potenziali problemi?

A seconda del tipo di account del Sottoscrittore, è possibile che si verifichino due problemi. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problema di mancata corrispondenza UPN dell'account aziendale o dell'Istituto di istruzione 
Una mancata corrispondenza UPN può essere rilevata quando una società dispone di un Active Directory impostato in cui UserPrincipalName (UPN) non è uguale all'indirizzo SMTP primario. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Come rilevare se l'indirizzo di accesso è influenzato da un UPN non corrispondente 

1. Accedere https://my.visualstudio.com/subscriptions usando l'indirizzo di accesso indicato nel messaggio di posta elettronica di assegnazione della sottoscrizione.

2. Verificare che l'indirizzo di posta elettronica di accesso elencato nella parte superiore destra della pagina corrisponda all'indirizzo usato per l'accesso.  In caso contrario, il nome UPN non corrisponde e non sarà possibile visualizzare la sottoscrizione. 

> [!div class="mx-imgBorder"]
> ![l'indirizzo di posta elettronica di accesso](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>Come correggere un UPN non corrispondente

1. Accedere al portale di gestione dell'amministrazione di Visual Studio [https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Individuare il Sottoscrittore con il problema di mancata corrispondenza UPN. La funzionalità [filtro](search-license.md) può semplificare la ricerca di un Sottoscrittore.

3. Modificare l'indirizzo di posta elettronica di accesso all'UPN del Sottoscrittore 

0. Salva le modifiche 

0. Informare il Sottoscrittore di disconnettersi dal portale Sottoscrittore e accedere di nuovo usando il nome UPN 

### <a name="personal-account-aliasing-issue"></a>Problema di alias dell'account personale

Gli account di sottoscrizione personali possono anche riscontrare problemi se l'indirizzo di posta elettronica usato per accedere al portale delle sottoscrizioni di Visual Studio non corrisponde all'indirizzo di posta elettronica associato alla sottoscrizione. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Come rilevare se il proprio account di sottoscrizione personale è influenzato da un problema di aliasing

1. Accedere a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions).

0. Verificare che l'indirizzo di posta elettronica di accesso elencato nella parte superiore destra della pagina corrisponda all'indirizzo usato per l'accesso.  Se l'indirizzo di posta elettronica connesso non corrisponde a quello usato per accedere al sito Web, si verifica un conflitto tra l'account e l'alias.

#### <a name="how-to-fix-an-alias-issue"></a>Come risolvere un problema di alias

La piattaforma Visual Studio assegna la priorità all'alias primario per visualizzare i dettagli della sottoscrizione. 

1. Passare a **gestire la modalità di accesso a Microsoft**. Accedere alla account Microsoft, se richiesto. 

2. In alias account selezionare **Rendi primario** accanto all'indirizzo di posta elettronica usato per assegnare la sottoscrizione. 

> [!div class="mx-imgBorder"]
> ![impostare l'indirizzo di posta elettronica primario](_img//aliasing/account-aliases.png)

3. Disconnettersi dal portale delle sottoscrizioni di Visual Studio (https://my.visualstudio.com) 

4. Eseguire di nuovo l'accesso con l'account usato per assegnare la sottoscrizione che ora deve essere configurata come alias primario. 

## <a name="preventing-aliasing-issues"></a>Prevenzione di problemi di aliasing

Come amministratore esistono due opzioni per assicurarsi che l'esperienza di accesso dei sottoscrittori a [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) sia positiva.
- La prima opzione (scelta consigliata) consiste nell'usare l'account di directory come accesso per il portale delle sottoscrizioni di Visual Studio all'https://my.visualstudio.com.  
- La seconda opzione (meno sicura) consiste nel consentire ai sottoscrittori di accedere con un indirizzo di posta elettronica diverso da quello dell'indirizzo di posta elettronica della directory.

Entrambe le opzioni sono configurate nel portale di amministrazione completando i passaggi seguenti:  
1. Accedi [https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Se si modifica un singolo utente, selezionare l'utente nella tabella e fare clic con il pulsante destro del mouse per modificare. Verrà aperto un pannello in cui è possibile modificare l'indirizzo di posta elettronica di accesso. Apportare gli aggiornamenti necessari nel campo indirizzo di posta elettronica di accesso. Fare clic su Save (Salva) per rendere effettive le modifiche.  

0. Se è necessario apportare queste modifiche a una grande quantità di utenti, è possibile utilizzare la funzionalità di modifica in blocco. Per ulteriori informazioni, vedere l'articolo su come [modificare più Sottoscrittori utilizzando la modifica bulk](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) .

> [!NOTE]
> Per le modifiche sia singole che bulk, i sottoscrittori riceveranno un messaggio di posta elettronica con le istruzioni per la modifica dell'indirizzo di posta elettronica di accesso e dovranno eseguire l'accesso con l'indirizzo di posta elettronica aggiornato. È anche importante notare che se il Sottoscrittore ha attivato in precedenza i vantaggi con l'altro indirizzo di accesso, sarà necessario continuare a usare l'altro indirizzo di accesso per accedervi.  

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


