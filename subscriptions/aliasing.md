---
title: Possibili errori di accesso alle sottoscrizioni di Visual Studio con alias | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: Si possono verificare errori di accesso se si usano alias o nomi descrittivi
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276628"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Possibili errori di accesso alle sottoscrizioni di Visual Studio con alias
A seconda del tipo di account usato per l'accesso, le sottoscrizioni disponibili potrebbero non essere visualizzate correttamente quando si accede a [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Una delle possibili cause è l'uso di "alias" o "nomi descrittivi" al posto dell'identità di accesso a cui è assegnata la sottoscrizione. Questa situazione viene chiamata "aliasing".

## <a name="what-is-aliasing"></a>Il termine "aliasing"
indica utenti che usano identità diverse per accedere a Windows (o al servizio Active Directory) e per accedere alla posta elettronica.

Si riscontra l'uso dell'aliasing quando una società usa un servizio Microsoft Online per l'accesso alla directory, ad esempio 'olivia@contoso.com', ma gli utenti accedono ai propri account di posta elettronica tramite alias o nomi descrittivi, ad esempio 'OliviaG@contoso.com'. Verificare che gli utenti accedano usando il "indirizzo di posta elettronica di accesso" come elencato nel portale di amministrazione delle sottoscrizioni di Visual Studio all'https://manage.visualstudio.com per accedere alle sottoscrizioni

## <a name="as-an-administrator-what-options-do-i-have"></a>Opzioni per l'amministratore

A seconda del tipo di account del Sottoscrittore, trovare la soluzione applicabile di seguito:

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problema di mancata corrispondenza UPN dell'account aziendale o dell'Istituto di istruzione

Una mancata corrispondenza del nome dell'entità utente (UPN) può essere rilevata quando in un compnay è configurata una posizione attiva in cui l'UPN non è uguale all'indirizzo SMTP primario. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>Come rilevare se l'indirizzo di accesso di un utente presenta un UPN non corrispondente

Chiedere all'utente di completare i passaggi seguenti:

1. Accedere a https://my.visualstudio.com usando l'indirizzo di accesso indicato nel messaggio di posta elettronica di assegnazione della sottoscrizione.  

    > [!NOTE]
    > Se non dispongono di un messaggio di posta elettronica di assegnazione della sottoscrizione, è possibile inviarlo di nuovo all'interno del portale di dell'amministrazione.  

2. Fare clic sulla scheda **Sottoscrizioni**.
3. Verificare che l'indirizzo di posta elettronica visualizzato in alto a destra indichi che l'utente ha eseguito l'accesso come... corrisponde all'indirizzo di posta elettronica di accesso nel messaggio di posta elettronica di assegnazione della sottoscrizione.  In caso contrario, non saranno in grado di accedere ai vantaggi della sottoscrizione. 

   > [!div class="mx-imgBorder"]
   > pagina Sottoscrizioni ![](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>Come correggere la mancata corrispondenza dell'UPN

1. Accedere al portale di gestione dell'amministrazione di Visual Studio all'https://manage.visualstudio.com 

2. Individuare l'utente che presenta il problema di mancata corrispondenza dell'UPN.  La funzionalità di [filtro](search-license.md) può semplificare questa operazione se si dispone di numerose sottoscrizioni. 

3. Modificare l'indirizzo di posta elettronica di accesso all'UPN dell'utente.

4. Salva le modifiche 

5. Richiedere all'utente di disconnettersi dal portale per gli abbonati e accedere di nuovo usando l'UPN.   

### <a name="personal-account-aliasing-issue"></a>Problema di alias dell'account personale

I problemi di aliasing possono anche influito sugli account personali. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>Come rilevare se un account personale presenta un problema di aliasing

1. Accedere https://my.visualstudio.com.

2. Fare clic sulla scheda **sottoscrizioni** e controllare l'indirizzo con cui si è effettuato l'accesso. 

3. Se l'indirizzo di posta elettronica connesso non corrisponde a quello usato per accedere al sito Web, si verifica un conflitto tra l'account e l'alias. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>Come risolvere un problema di aliasing di un account personale

La piattaforma delle sottoscrizioni di Visual Studio assegna la priorità all'alias primario per visualizzare i dettagli della sottoscrizione.  Per risolvere il problema, è necessario creare un alias di posta elettronica diverso per l'alias principale per l'accesso. 

1. Passare a [gestire la modalità di accesso a Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842796).
2. Accedere alla account Microsoft, se richiesto. 
3. In alias account selezionare **Rendi primario** accanto all'indirizzo di posta elettronica usato per assegnare la sottoscrizione. 
4. In alias account selezionare Rendi primario accanto all'indirizzo di posta elettronica usato per assegnare la sottoscrizione. 
5. Disconnettersi dal portale per i sottoscrittori di Visual Studio (https://my.visualstudio.com) 
6. Accedere di nuovo al portale usando il nuovo alias primario. 

### <a name="ensure-a-successful-experience-for-your-users"></a>Garantire una corretta esperienza per gli utenti

In qualità di amministratore, sono disponibili due opzioni per assicurarsi che i Sottoscrittori dispongano di un'esperienza di accesso efficace in https://my.visualstudio.com. 

- La prima opzione (scelta consigliata) consiste nell'utilizzare l'account di directory come indirizzo di accesso in https://manage.visualstudio.com.
- La seconda opzione, che è meno sicura, la seconda opzione (meno sicura) consiste nel consentire ai sottoscrittori di accedere con un indirizzo di posta elettronica diverso da quello dell'indirizzo di posta elettronica della directory.

Entrambe le opzioni sono configurate nel portale di amministrazione completando i passaggi seguenti:

1. Accedi https://manage.visualstudio.com 

2. Se si modifica un singolo utente, selezionare l'utente nella tabella e fare clic con il pulsante destro del mouse per modificare. Verrà aperto un pannello in cui è possibile modificare l'indirizzo di posta elettronica di accesso.  

3. Apportare gli aggiornamenti necessari nel campo indirizzo di posta elettronica di accesso. 

4. Fare clic su Save (Salva) per rendere effettive le modifiche.  
Se è necessario apportare queste modifiche a una grande quantità di utenti, è possibile utilizzare la funzionalità di modifica in blocco. Per altre informazioni su questo processo, vedere la sezione **modificare più sottoscrittori usando la modifica bulk** dell'articolo [modificare le sottoscrizioni]] (edit-License.MD).  

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione delle sottoscrizioni di Visual Studio.
- [Assegna singole sottoscrizioni](assign-license.md)
- [Assegna più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)
