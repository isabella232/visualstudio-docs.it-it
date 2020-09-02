---
title: Usare gli account che richiedono l'autenticazione a più fattori
ms.date: 05/27/2020
ms.topic: conceptual
description: Informazioni su come usare Visual Studio con gli account che richiedono l'autenticazione a più fattori.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 699580689bcf00d00d2a6e07f814be4d1265bb1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283546"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Come usare Visual Studio con gli account che richiedono l'autenticazione a più fattori

Quando si collabora con utenti Guest esterni, è consigliabile proteggere le app e i dati con criteri di **accesso condizionale** , ad esempio **multi-factor authentication**.  

Una volta abilitata, gli utenti Guest dovranno avere più di un nome utente e una password per accedere alle risorse e devono soddisfare i requisiti di sicurezza aggiuntivi. I criteri MFA possono essere applicati a livello di tenant, di app o di singolo utente, così come vengono abilitati per i membri dell'organizzazione. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>In che modo l'esperienza di Visual Studio è interessata dai criteri di autenticazione a più fattori?
Le versioni di Visual Studio precedenti alla 16,6 possono avere una riduzione delle esperienze di autenticazione quando vengono usate con gli account che hanno abilitato criteri CA come l'autenticazione a più fattori e sono associati a due o più tenant.

Questi problemi possono causare l'istanza di Visual Studio per richiedere la riautenticazione più volte al giorno. Potrebbe essere necessario immettere nuovamente le credenziali per i tenant precedentemente autenticati, anche nel corso della stessa sessione di Visual Studio.

## <a name="using-visual-studio-with-mfa-policies"></a>Uso di Visual Studio con i criteri di autenticazione a più fattori
Nella versione 16,6 sono state aggiunte nuove funzionalità a Visual Studio 2019 che semplificano il modo in cui gli utenti possono accedere alle risorse protette tramite criteri di autorità di certificazione, ad esempio l'autenticazione a più fattori. Per usare questo flusso di lavoro migliorato, è necessario acconsentire esplicitamente a usare il Web browser predefinito del sistema come meccanismo per aggiungere e riautenticare gli account di Visual Studio.  

> [!WARNING]
> Il mancato utilizzo di questo flusso di lavoro potrebbe provocare un'esperienza ridotte, ottenendo più richieste di autenticazione aggiuntive durante l'aggiunta o la riautenticazione degli account di Visual Studio. 

### <a name="enabling-system-web-browser"></a>Abilitazione del Web browser di sistema

> [!NOTE] 
> Per un'esperienza ottimale, è consigliabile cancellare i dati del Web browser predefiniti del sistema prima di procedere con il flusso di lavoro. Inoltre, se si dispone di account aziendali o dell'Istituto di istruzione nelle impostazioni di Windows 10 in **Accedi all'ufficio o all'Istituto di istruzione**, verificare che siano autenticati correttamente.

Per abilitare questo flusso di lavoro, passare alla finestra di dialogo Opzioni di Visual Studio **(strumenti > opzioni...)**, selezionare la scheda **account** e selezionare **sistema Web browser** sotto l'elenco **a discesa Aggiungi e riautenticare gli account con:** . 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Dal menu selezionare System Web browser.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Accedere ad altri account con i criteri di autenticazione a più fattori 
Quando il flusso di lavoro del browser Web di sistema è abilitato, è possibile accedere o aggiungere account a Visual Studio normalmente, tramite la finestra di dialogo Impostazioni account **(File > impostazioni account...)**.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Aggiungere un nuovo account di personalizzazione a Visual Studio." border="false":::

Questa azione consente di aprire il Web browser predefinito del sistema, di richiedere l'accesso all'account e di convalidare i criteri di autenticazione a più fattori richiesti.

In base alle attività di sviluppo e alla configurazione delle risorse, è possibile che venga richiesto di immettere nuovamente le credenziali durante la sessione. Questo problema può verificarsi quando si aggiunge una nuova risorsa o si prova ad accedere a una risorsa senza che in precedenza siano stati soddisfatti i requisiti di autorizzazione CA/AMF.

> [!NOTE] 
> Per un'esperienza ottimale, è possibile lasciare il browser aperto fino a quando non vengono convalidati tutti i criteri CA/multi-factor authentication per le risorse. La chiusura del browser può comportare la perdita dello stato di autenticazione a più fattori compilato in precedenza e potrebbe richiedere richieste di autorizzazione aggiuntive.

## <a name="reauthenticating-an-account"></a>Riautenticazione di un account  
Se si verifica un problema con l'account, Visual Studio potrebbe richiedere di immettere nuovamente le credenziali dell'account.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Riautenticare l'account di Visual Studio.":::

Facendo clic su **reimmettere le credenziali** si aprirà il Web browser predefinito del sistema e si tenterà di aggiornare automaticamente le credenziali. In caso di esito negativo, verrà richiesto di accedere al proprio account e di convalidare i criteri di autorità di certificazione/autenticazione richiesti.

> [!NOTE] 
> Per un'esperienza ottimale, è possibile lasciare il browser aperto fino a quando non vengono convalidati tutti i criteri CA/multi-factor authentication per le risorse. La chiusura del browser può comportare la perdita dello stato di autenticazione a più fattori compilato in precedenza e potrebbe richiedere richieste di autorizzazione aggiuntive.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Come rifiutare esplicitamente l'uso di un tenant di Azure Active Directory specifico in Visual Studio

Visual Studio 2019 versione 16,6 offre la flessibilità necessaria per filtrare i tenant specifici, che li nasconde da Visual Studio. Il filtro elimina la necessità di eseguire l'autenticazione con tale tenant, ma significa anche che non sarà possibile accedere alle risorse associate. 

Questa funzionalità è utile quando si dispone di più tenant, ma si desidera ottimizzare l'ambiente di sviluppo selezionando come destinazione un subset specifico. Può anche essere utile nelle istanze quando non è possibile convalidare un particolare criterio di autorità di certificazione/autenticazione a più fattori, perché è possibile filtrare il tenant che ha causato il danneggiamento 

### <a name="how-to-filter-out-a-tenant"></a>Come filtrare un tenant
Per filtrare i tenant associati all'account di Visual Studio, aprire la finestra di dialogo Impostazioni account **(File > impostazioni account...)** e fare clic su **Applica filtro**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Applicare il filtro." border="false":::

Verrà visualizzata la finestra di dialogo **filtro account** , che consente di selezionare i tenant da usare con l'account. 

:::image type="content" source="media/select-filter-account.png" alt-text="Selezionare l'account da filtrare.":::

## <a name="see-also"></a>Vedere anche

- [Accedi a Visual Studio](signing-in-to-visual-studio.md)
- [Accesso a Visual Studio per Mac](/visualstudio/mac/signing-in)
- [Gestire più account utente](work-with-multiple-user-accounts.md)
