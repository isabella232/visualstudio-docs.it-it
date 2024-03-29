---
title: Possibili errori di accesso alle sottoscrizioni di Visual Studio con alias | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/19/2021
ms.topic: conceptual
description: Si possono verificare errori di accesso se si usano alias o nomi descrittivi
ms.openlocfilehash: 967c1091d26c99cb5ad4d8fea972e8a500b82ef8
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428116"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>L'accesso Visual Studio sottoscrizioni potrebbe non riuscire quando si usano alias
A seconda del tipo di account usato per l'accesso, le sottoscrizioni disponibili potrebbero non essere visualizzate correttamente quando si accede a [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) . Una delle possibili cause è l'uso di "alias" o "nomi descrittivi" al posto dell'identità di accesso a cui è assegnata la sottoscrizione. Questa situazione viene chiamata "aliasing".

## <a name="what-is-aliasing"></a>Il termine "aliasing"
indica utenti che usano identità diverse per accedere a Windows (o al servizio Active Directory) e per accedere alla posta elettronica.

Si riscontra l'uso dell'aliasing quando una società usa un servizio Microsoft Online per l'accesso alla directory, ad esempio 'JohnD@contoso.com', ma gli utenti accedono ai propri account di posta elettronica tramite alias o nomi descrittivi, ad esempio 'John.Doe@contoso.com'. Assicurarsi che gli utenti utilizzino "Indirizzo di posta elettronica di accesso" come elencato nel portale di amministrazione in https://manage.visualstudio.com per accedere alle sottoscrizioni. 

## <a name="what-are-the-potential-issues"></a>Quali sono i potenziali problemi?

A seconda del tipo di account del sottoscrittore, possono verificarsi due problemi. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problema di mancata corrispondenza dell'UPN dell'account aziendale o dell'istituto di istruzione 
Una mancata corrispondenza UPN può essere rilevata quando un'azienda ha un'istanza di Active Directory in cui UserPrincipalName (UPN) non corrisponde all'indirizzo SMTP primario. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Come rilevare se l'indirizzo di accesso è inciso da una mancata corrispondenza upn 

1. Accedere usando l'indirizzo di accesso indicato nel messaggio di posta https://my.visualstudio.com/subscriptions elettronica di assegnazione della sottoscrizione.

2. Fare clic sul proprio nome nell'angolo superiore destro della pagina.  Verrà aperto il profilo.  Verificare che l'indirizzo di posta elettronica di accesso elencato nel profilo corrisponda all'indirizzo usato per l'accesso.  In caso contrario, l'UPN non corrisponde e non sarà possibile visualizzare la sottoscrizione. 

> [!div class="mx-imgBorder"]
> ![Indirizzo di posta elettronica di accesso](_img//aliasing/sign-in-email.png "Assicurarsi che l'indirizzo di posta elettronica visualizzato nel profilo corrisponda a quello utilizzato per l'accesso.")

#### <a name="how-to-fix-a-upn-mismatch"></a>Come correggere una mancata corrispondenza upn

1. Accedere al portale Visual Studio Administration Management[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Individuare il sottoscrittore con il problema di mancata corrispondenza upn. La [funzionalità Filtro](search-license.md) consente di trovare facilmente un sottoscrittore.

3. Modificare l'indirizzo di posta elettronica di accesso con l'UPN del sottoscrittore 

0. Salvare le modifiche 

0. Informare il sottoscrittore di disconnettersi dal portale sottoscrittore e accedere di nuovo usando l'UPN 

### <a name="personal-account-aliasing-issue"></a>Problema di aliasing dell'account personale

Gli account di sottoscrizione personali possono inoltre verificarsi problemi se l'indirizzo di posta elettronica usato per accedere al portale Sottoscrizioni di Visual Studio non corrisponde all'indirizzo di posta elettronica associato alla sottoscrizione. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Come rilevare se l'account di sottoscrizione personale è stato intasato da un problema di aliasing

1. Accedere a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Verificare che l'indirizzo di posta elettronica di accesso elencato in alto a destra nella pagina corrisponda all'indirizzo usato per l'accesso.  Se l'indirizzo di posta elettronica connesso non corrisponde all'indirizzo di posta elettronica usato per accedere al sito Web, si verifica un conflitto tra l'account e l'alias.

#### <a name="how-to-fix-an-alias-issue"></a>Come risolvere un problema di alias

La Visual Studio assegna la priorità all'alias primario per visualizzare i dettagli della sottoscrizione. 

1. Passare a **Gestire la modalità di accesso a Microsoft.** Accedere al proprio account Microsoft se richiesto. 

2. In Alias account selezionare Rendi **primario** accanto all'indirizzo di posta elettronica usato per assegnare la sottoscrizione. 

> [!div class="mx-imgBorder"]
> ![Impostare l'indirizzo di posta elettronica primario](_img//aliasing/account-aliases.png "Usare il collegamento Crea database primario per scegliere l'alias primario per le sottoscrizioni.")

3. Disconnettersi dal portale Sottoscrizioni di Visual Studio (https://my.visualstudio.com) 

4. Accedere di nuovo usando l'account usato per assegnare la sottoscrizione che ora deve essere configurata come alias primario. 

## <a name="preventing-aliasing-issues"></a>Prevenzione dei problemi di aliasing

Gli amministratori hanno due opzioni per garantire che i sottoscrittori hanno un'esperienza di accesso corretta in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) .
- La prima opzione (scelta consigliata) è sfruttare l'account della directory come accesso per il portale Sottoscrizioni di Visual Studio all'indirizzo https://my.visualstudio.com .  
- La seconda opzione (meno sicura) è consentire ai sottoscrittori di accedere usando un indirizzo di posta elettronica diverso rispetto all'indirizzo di posta elettronica della directory.

Entrambe queste opzioni vengono configurate nel portale di amministrazione completando i passaggi seguenti:  
1. Accedere [https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Se si modifica un singolo utente, selezionarlo nella tabella e fare clic con il pulsante destro del mouse per modificarlo. Verrà aperto un pannello in cui è possibile modificare l'indirizzo di posta elettronica di accesso. Apportare gli aggiornamenti necessari nel campo indirizzo di posta elettronica di accesso. Fare clic su Salva e le modifiche avranno effetto.  

0. Se è necessario apportare queste modifiche a una grande quantità di utenti, è possibile usare la funzionalità di modifica in blocco. Per altre [informazioni, vedere l'articolo](./edit-license.md#edit-multiple-subscribers-using-bulk-edit) Modificare più sottoscrittori usando la modifica in blocco.

> [!NOTE]
> Per le modifiche sia singole che bulk, i sottoscrittori riceveranno un messaggio di posta elettronica con le istruzioni che l'indirizzo di posta elettronica di accesso è stato modificato e dovranno accedere usando l'indirizzo di posta elettronica aggiornato. È anche importante notare che se il sottoscrittore ha attivato in precedenza i vantaggi con l'altro indirizzo di accesso, dovrà continuare a usare l'altro indirizzo di accesso per accedervi.  

## <a name="support-resources"></a>Risorse di supporto
- Per assistenza per l'amministrazione di Sottoscrizioni di Visual Studio, contattare [il supporto Visual Studio sottoscrizioni](https://aka.ms/vsadminhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione Visual Studio sottoscrizioni.
- [Assegnare singole sottoscrizioni](assign-license.md)
- [Assegnare più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)