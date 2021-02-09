---
title: 'Procedura: installare un plug-in del controllo del codice sorgente | Microsoft Docs'
description: Informazioni su come installare un plug-in del controllo del codice sorgente in Visual Studio mediante l'integrazione con l'API del plug-in del controllo del codice sorgente di Visual Studio e la registrazione della DLL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad5b77176d05c28b3ba938a1255de6e10fcd7094
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912748"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Procedura: installare un plug-in del controllo del codice sorgente
La creazione di un plug-in del controllo del codice sorgente prevede tre passaggi:

1. Creare una DLL con le funzioni definite nella sezione di riferimento dell'API del plug-in del controllo del codice sorgente di questa documentazione.

2. Implementare le funzioni definite dall'API del plug-in del controllo del codice sorgente. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene chiamato, le interfacce e le finestre di dialogo sono disponibili dal plug-in.

3. Registrare la DLL rendendo le voci del registro di sistema appropriate.

## <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta i plug-in del controllo del codice sorgente conformi all'API del plug-in del controllo del codice sorgente.

### <a name="register-the-source-control-plug-in"></a>Registrare il plug-in del controllo del codice sorgente
 Prima che un Integrated Development Environment di esecuzione (IDE) possa chiamare nel sistema di controllo del codice sorgente, deve innanzitutto trovare la DLL del plug-in del controllo del codice sorgente che esporta l'API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Per registrare la DLL del plug-in del controllo del codice sorgente

1. Aggiungere due voci sotto la chiave **HKEY_LOCAL_MACHINE** della sottochiave **software** che specifica la sottochiave del nome della società seguita dalla sottochiave del nome del prodotto. Il modello è **\\ \<company name> \\ \<product name>HKEY_LOCAL_MACHINE\SOFTWARE\\ valore \<entry>**  =  . Le due voci sono sempre denominate **SCCServerName** e **SCCServerPath**. Ogni è una stringa normale.

    Se, ad esempio, il nome della società è Microsoft e il prodotto del controllo del codice sorgente è denominato SourceSafe, il percorso del registro di sistema sarà **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. In questa sottochiave, la prima voce, **SCCServerName**, è una stringa leggibile dall'utente che assegna un nome al prodotto. La seconda voce, **SCCServerPath**, è il percorso completo della dll del plug-in del controllo del codice sorgente a cui l'IDE deve connettersi. Di seguito sono disponibili voci del registro di sistema di esempio:

   |Voce del registro di sistema di esempio|Valore di esempio|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath è il percorso completo del plug-in di SourceSafe. Il plug-in del controllo del codice sorgente utilizzerà nomi di società e prodotti diversi, ma gli stessi percorsi di immissione del registro di sistema.

2. Per modificare il comportamento del plug-in del controllo del codice sorgente, è possibile utilizzare le seguenti voci del registro di sistema facoltative. Queste voci vengono inserite nella stessa sottochiave di **SccServerName** e **SccServerPath**.

   - La voce **HideInVisualStudioregistry** può essere utilizzata se non si desidera che il plug-in del controllo del codice sorgente venga visualizzato nell'elenco di **selezione dei plug-in** di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Questa voce influirà anche sul cambio automatico al plug-in del controllo del codice sorgente. Un possibile utilizzo di questa voce è se si fornisce un pacchetto di controllo del codice sorgente che sostituisce il plug-in del controllo del codice sorgente, ma si desidera rendere più semplice per l'utente eseguire la migrazione dall'utilizzo del plug-in del controllo del codice sorgente al pacchetto del controllo del codice sorgente. Quando il pacchetto del controllo del codice sorgente è installato, imposta questa voce del registro di sistema, che nasconde il plug-in.

      **HideInVisualStudio** è un valore DWORD ed è impostato su *1* per nascondere il plug-in o *0* per visualizzare il plug-in. Se la voce del registro di sistema non viene visualizzata, il comportamento predefinito consiste nel visualizzare il plug-in.

   - La voce del registro di sistema **DisableSccManager** può essere usata per disabilitare o nascondere l'opzione di menu **Launch \<Source Control Server>** che in genere viene visualizzata sotto il   >  sottomenu **controllo del codice sorgente** file. Se si seleziona questa opzione di menu, viene chiamata la funzione [SccRunScc](../../extensibility/sccrunscc-function.md) . Il plug-in del controllo del codice sorgente potrebbe non supportare un programma esterno e, pertanto, potrebbe essere necessario disabilitare o nascondere l'opzione del menu **Launch** .

      **DisableSccManager** è un valore DWORD ed è impostato su *0* per abilitare l'opzione di menu **Launch \<Source Control Server>** , impostata su *1* per disabilitare l'opzione di menu e su *2* per nascondere l'opzione di menu. Se questa voce del registro di sistema non viene visualizzata, il comportamento predefinito consiste nel visualizzare l'opzione di menu.

   | Voce del registro di sistema di esempio | Valore di esempio |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Aggiungere la sottochiave **SourceCodeControlProvider** nella chiave **HKEY_LOCAL_MACHINE** della sottochiave **software** .

    In questa sottochiave la voce del registro di sistema **ProviderRegKey** è impostata su una stringa che rappresenta la sottochiave inserita nel registro di sistema nel passaggio 1. Il modello è **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey**  =  *software \\<nome della società \> \\<nome \> del prodotto*.

    Di seguito è riportato un esempio di contenuto per questa sottochiave.

   |Voce del Registro di sistema|Valore di esempio|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Il plug-in del controllo del codice sorgente utilizzerà la stessa sottochiave e i nomi di voce, ma il valore sarà diverso.

4. Creare una sottochiave denominata **InstalledSCCProviders** nella sottochiave **SourceCodeControlProvider** e quindi inserire una voce sotto tale sottochiave.

    Il nome di questa voce è il nome leggibile dall'utente del provider (uguale al valore specificato per la voce SCCServerName) e il valore è ancora una volta, la sottochiave creata nel passaggio 1. Il modello è **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<nome visualizzato \>**  =  *software<nome della \\ società \> \\<nome \> del prodotto*.

    Ad esempio:

   |Voce del registro di sistema di esempio|Valore di esempio|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > In questo modo è possibile registrare più plug-in del controllo del codice sorgente. Questo è il modo in cui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Trova tutti i plug-in basati su API del plug-in del controllo del codice sorgente installati.

## <a name="how-an-ide-locates-the-dll"></a>Come un IDE individua la DLL
 L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ha due modi per trovare la dll del plug-in del controllo del codice sorgente:

- Trovare il plug-in del controllo del codice sorgente predefinito e connettersi in modo invisibile all'utente.

- Trova tutti i plug-in del controllo del codice sorgente registrati, da cui l'utente ne sceglie uno.

  Per individuare la DLL nel primo modo, l'IDE cerca sotto la sottochiave **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** per la voce **ProviderRegKey**. Il valore di questa voce punta a un'altra sottochiave. L'IDE cerca quindi una voce denominata **SccServerPath** nella seconda sottochiave in **HKEY_LOCAL_MACHINE**. Il valore di questa voce indica l'IDE alla DLL.

> [!NOTE]
> L'IDE non carica le dll dai percorsi relativi, ad esempio *.\NewProvider.DLL*. È necessario specificare un percorso completo della DLL, ad esempio *c:\Providers\NewProvider.DLL*. Ciò consente di migliorare la sicurezza dell'IDE impedendo il caricamento di DLL plug-in non autorizzate o rappresentate.

 Per individuare la DLL nel secondo modo, l'IDE cerca sotto la sottochiave **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** per tutte le voci. Ogni voce ha un nome e un valore. L'IDE Visualizza un elenco di questi nomi per l'utente. Quando l'utente sceglie un nome, l'IDE trova il valore per il nome selezionato che punta a una sottochiave. L'IDE cerca una voce denominata **SccServerPath** nella sottochiave in **HKEY_LOCAL_MACHINE**. Il valore di tale voce indica l'IDE alla DLL corretta.

 Un plug-in del controllo del codice sorgente deve supportare entrambe le modalità di ricerca della DLL e, di conseguenza, imposta **ProviderRegKey**, sovrascrivendo qualsiasi impostazione precedente. In particolare, è necessario aggiungersi all'elenco di **InstalledSccProviders** in modo che l'utente possa scegliere il plug-in del controllo del codice sorgente da usare.

> [!NOTE]
> Poiché viene utilizzata la chiave di **HKEY_LOCAL_MACHINE** , è possibile registrare un solo plug-in del controllo del codice sorgente come plug-in del controllo del codice sorgente predefinito in un determinato computer. Tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente agli utenti di determinare il plug-in del controllo del codice sorgente che si desidera utilizzare effettivamente per una particolare soluzione. Durante il processo di installazione, verificare se un plug-in del controllo del codice sorgente è già impostato. in tal caso, richiedere all'utente se impostare il nuovo plug-in del controllo del codice sorgente installato come predefinito. Durante la disinstallazione, non rimuovere altre sottochiavi del registro di sistema comuni a tutti i plug-in del controllo del codice sorgente in **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; rimuovere solo la sottochiave SCC specifica.

## <a name="how-the-ide-detects-version-1213-support"></a>Come l'IDE rileva il supporto della versione 1.2/1.3
 Come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rileva se un plug-in supporta la funzionalità di plug-in del controllo del codice sorgente versione 1,2 e 1,3? Per dichiarare la funzionalità avanzata, il plug-in del controllo del codice sorgente deve implementare la funzione corrispondente:

 Prima di tutto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Controlla il valore restituito chiamando [SccGetVersion](../../extensibility/sccgetversion-function.md). Deve essere maggiore o uguale a 1,2.

 Quindi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina se la nuova funzionalità specifica è supportata esaminando l' `lpSccCaps` argomento in [SccInitialize](../../extensibility/sccinitialize-function.md).

 Se vengono soddisfatte entrambe le condizioni, è possibile chiamare le nuove funzioni supportate nelle versioni 1,2 e 1,3.

## <a name="see-also"></a>Vedi anche
- [Introduzione ai plug-in del controllo del codice sorgente](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
