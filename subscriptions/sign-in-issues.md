---
title: Problemi di accesso alle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 03/11/2020
ms.topic: conceptual
description: Informazioni sui problemi che potrebbero verificarsi durante l'accesso alle sottoscrizioni di Visual Studio
ms.openlocfilehash: de27f64f1d5c83ed01a1e561f4921dbed53c479c
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233238"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problemi di accesso alle sottoscrizioni di Visual Studio
Per usare la sottoscrizione di Visual Studio, è necessario eseguire prima l'accesso.  A seconda della sottoscrizione, è possibile che la configurazione sia stata eseguita con un account Microsoft (MSA) o un'identità di Azure Active Directory (AAD).  Questo articolo descrive alcuni dei problemi che potrebbero verificarsi durante l'accesso alla sottoscrizione.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Non è possibile creare gli account Microsoft (MSA) usando indirizzi di posta elettronica aziendali o dell'istituto di istruzione
Quando il dominio di posta elettronica è configurato in Azure AD, non è più possibile creare un nuovo account personale Microsoft (MSA) usando un indirizzo di posta elettronica aziendale o dell'istituto di istruzione. Che cosa significa? Se l'organizzazione usa Office 365 o altri servizi aziendali Microsoft basati su Azure AD ed è stato aggiunto un nome di dominio al tenant di Azure AD, gli utenti non potranno più creare un nuovo account personale Microsoft usando un indirizzo di posta elettronica del dominio.

### <a name="why-was-this-change-made"></a>Perché è stata effettuata questa modifica?
Un account personale Microsoft con indirizzo aziendale come nome utente presenta problemi per gli utenti finali e i reparti IT. Ad esempio:
- È possibile che gli utenti considerino il loro account personale Microsoft conforme all'azienda e pensino di rispettare i criteri di conformità quando salvano un documento aziendale in OneDrive
- Gli utenti che lasciano un'azienda solitamente perdono l'accesso all'indirizzo di posta elettronica aziendale. In questo caso, potrebbero non essere in grado di accedere all'account personale Microsoft se dimenticano la password. Tuttavia, il reparto IT potrebbe reimpostare la password e accedere all'account personale degli ex-dipendenti.
- I reparti IT credono erroneamente di essere proprietari dell'account e della relativa sicurezza. Ma gli utenti possono avere la necessità di eseguire il roundtrip di un codice nel loro indirizzo di posta elettronica aziendale una sola volta e possono rinominare l'account in qualsiasi momento successivo.

La situazione è particolarmente complicata per gli utenti che hanno due account con lo stesso indirizzo di posta elettronica (uno in Azure AD e un account Microsoft).

### <a name="what-does-this-experience-look-like"></a>Com'è questa esperienza?
Se si tenta di registrarsi in un'app consumer Microsoft con un indirizzo di posta elettronica aziendale o dell'istituto di istruzione, verrà visualizzato il messaggio seguente.

   > [!div class="mx-imgBorder"]
   > ![Impossibile creare un account con la posta elettronica aziendale](_img/sign-in-issues/cannot-use-work-email.png)

Tuttavia, se si tenta di registrarsi in un'app Microsoft che supporta gli account personali e aziendali o dell'istituto di istruzione, verrà visualizzato il messaggio seguente:

   > [!div class="mx-imgBorder"]
   > ![Account aziendali o dell'istituto di istruzione supportati](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Gli account esistenti sono interessati?
Il blocco della registrazione descritto di seguito impedisce solo la creazione di nuovi account. Non ha alcun impatto sugli utenti che hanno già un account Microsoft con un indirizzo di posta elettronica aziendale o dell'istituto di istruzione. In questo caso, è ora più semplice rinominare un account Microsoft personale. Questo [articolo del supporto](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) offre semplici istruzioni dettagliate. Rinominare il proprio account personale Microsoft significa modificarne il nome utente senza alcun impatto sulla posta elettronica aziendale o sulla modalità di accesso ai servizi aziendali, ad esempio Office 365. Non ha alcun impatto neanche sui contenuti personali ma ne modifica soltanto la modalità di accesso. È possibile usare un altro indirizzo di posta elettronica (personale), ottenere un nuovo indirizzo di posta elettronica @outlook.com da Microsoft oppure usare un numero di telefono come nuovo nome utente.

> [!NOTE]
> Se il proprio reparto IT ha richiesto di creare un account personale Microsoft con la posta elettronica aziendale o dell'istituto di istruzione, ad esempio per accedere a servizi aziendali Microsoft come Premier Support, rivolgersi al team di amministratori prima di rinominare l'account.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>L'eliminazione di un indirizzo di accesso può impedire l'accesso a una sottoscrizione
Se si elimina una o più identità (MSA o AAD) associate alla sottoscrizione, è possibile che il rendering dei dati del sottoscrittore, inclusi nome utente e ID di accesso, venga eseguito in modo anonimo causando la perdita dell'accesso alla sottoscrizione.

Per evitare effetti sull'accesso alla sottoscrizione, usare una delle tecniche seguenti.
- Distribuire un solo sistema di gestione delle identità, MSA o AAD, ma non entrambi.
- Associare le identità AAD e MSA tramite il tenant.

## <a name="signing-in-may-fail-when-using-aliases"></a>L'accesso potrebbe non riuscire quando si usano gli alias
A seconda del tipo di account utilizzato per l'accesso, le [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)sottoscrizioni disponibili potrebbero non essere visualizzate correttamente quando si accede a . Una delle possibili cause è l'uso di "alias" o "nomi descrittivi" al posto dell'identità di accesso a cui è assegnata la sottoscrizione. Questa situazione viene chiamata "aliasing".

### <a name="what-is-aliasing"></a>Il termine "aliasing"
indica utenti che usano identità diverse per accedere a Windows (o al servizio Active Directory) e per accedere alla posta elettronica.

L'aliasing può esistere quando un'azienda usa un servizio Microsoft Online per l'accesso alla directory, ad esempio JohnD@contoso.com, ma gli utenti accedono agli account di posta elettronica tramite alias o nomi descrittivi, ad esempio John.Doe@contoso.com. Per molti clienti che gestiscono le sottoscrizioni tramite Volume Licensing Service Center (VLSC), questo può causare errori durante l'esperienza di accesso perché l'indirizzo di posta elettronica fornito (John.Doe@contoso.com) non corrisponde all'indirizzo della directory (JohnD@contoso.com) richiesto per completare l'autenticazione tramite l'opzione "Account aziendale o dell'istituto di istruzione".

### <a name="what-options-do-i-have"></a>Quali sono le opzioni a disposizione?
Dal punto di vista dei sottoscrittori, è prima di tutto importante collaborare con l'amministratore per comprendere la configurazione delle identità della società. Se necessario, l'amministratore potrebbe dover aggiornare le impostazioni dell'account dal portale di amministrazione o potrebbe essere necessario creare un account Microsoft (MSA) usando l'indirizzo di posta elettronica aziendale. Prima di eseguire i passaggi per creare un account Microsoft, contattare l'amministratore per verificare se esistono criteri o problemi per questa azione. 

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Scoprire come [collegare gli account MSA e AAD](/azure/active-directory/b2b/add-users-administrator) all'interno di AAD.
- Ottenere altre informazioni sull'[anonimizzazione](anonymization.md).
