---
title: 'Procedura: Installare un plug-in del controllo del codice sorgente | Microsoft Docs'
description: Informazioni su come installare un plug-in del controllo del codice sorgente Visual Studio integrarlo con l'API plug-in di controllo del codice sorgente Visual Studio e registrarne la DLL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c1f491bdbf1b27c19f324c2cbee076cb8f9124f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042439"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Procedura: Installare un plug-in del controllo del codice sorgente
La creazione di un plug-in di controllo del codice sorgente prevede tre passaggi:

1. Creare una DLL con le funzioni definite nella sezione di riferimento dell'API plug-in del controllo del codice sorgente di questa documentazione.

2. Implementare le funzioni definite dall'API del plug-in del controllo del codice sorgente. Quando lo chiama, rendere disponibili interfacce e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestre di dialogo dal plug-in.

3. Registrare la DLL effettuando le voci appropriate del Registro di sistema.

## <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta plug-in di controllo del codice sorgente conformi all'API plug-in del controllo del codice sorgente.

### <a name="register-the-source-control-plug-in"></a>Registrare il plug-in del controllo del codice sorgente
 Prima che un ambiente di sviluppo integrato (IDE) in esecuzione possa chiamare nel sistema di controllo del codice sorgente, deve trovare la DLL del plug-in del controllo del codice sorgente che esporta l'API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Per registrare la DLL del plug-in del controllo del codice sorgente

1. Aggiungere due voci sotto la chiave **HKEY_LOCAL_MACHINE** chiave nella sottochiave **SOFTWARE** che specifica la sottochiave del nome della società seguita dalla sottochiave del nome del prodotto. Il modello è **HKEY_LOCAL_MACHINE\SOFTWARE\\ \<company name> \\ \<product name> \\ \<entry>**  =  *valore*. Le due voci sono sempre denominate **SCCServerName** e **SCCServerPath**. Ognuno è una stringa regolare.

    Ad esempio, se il nome della società è Microsoft e il prodotto del controllo del codice sorgente è denominato SourceSafe, il percorso del Registro di sistema sarà **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. In questa sottochiave la prima voce, **SCCServerName**, è una stringa leggibile dall'utente che assegna un nome al prodotto. La seconda voce, **SCCServerPath**, è il percorso completo della DLL del plug-in del controllo del codice sorgente a cui l'IDE deve connettersi. Di seguito sono riportate le voci del Registro di sistema di esempio:

   |Voce del Registro di sistema di esempio|Valore di esempio|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath è il percorso completo del plug-in di SourceSafe. Il plug-in di controllo del codice sorgente userà nomi di società e prodotti diversi, ma gli stessi percorsi di voce del Registro di sistema.

2. Le voci del Registro di sistema facoltative seguenti possono essere usate per modificare il comportamento del plug-in del controllo del codice sorgente. Queste voci si insedino nella stessa sottochiave **di SccServerName** e **SccServerPath**.

   - La **voce HideInVisualStudioregistry** può essere usata se non si vuole che il plug-in del controllo del codice sorgente venga visualizzato nell'elenco Selezione **plug-in** di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Questa voce influirà anche sul passaggio automatico al plug-in del controllo del codice sorgente. Un possibile uso di questa voce è se si specifica un pacchetto di controllo del codice sorgente che sostituisce il plug-in del controllo del codice sorgente, ma si vuole semplificare la migrazione dell'utente dall'uso del plug-in di controllo del codice sorgente al pacchetto di controllo del codice sorgente. Quando il pacchetto di controllo del codice sorgente viene installato, imposta questa voce del Registro di sistema, che nasconde il plug-in.

      **HideInVisualStudio è** un valore DWORD ed è impostato su *1* per nascondere il plug-in o *su 0* per visualizzare il plug-in. Se la voce del Registro di sistema non viene visualizzata, il comportamento predefinito è visualizzare il plug-in.

   - La **voce del Registro di sistema DisableSccManager**  **\<Source Control Server>** può essere usata per disabilitare o nascondere l'opzione di menu Avvia che in genere viene visualizzata nel sottomenu Controllo del codice  >  **sorgente** file. Selezionando questa opzione di menu viene chiamata [la funzione SccRunScc.](../../extensibility/sccrunscc-function.md) Il plug-in del controllo del codice sorgente potrebbe non supportare un programma esterno e pertanto potrebbe essere necessario disabilitare o nascondere **l'opzione di** menu Avvia.

      **DisableSccManager** è un valore DWORD ed è impostato su *0* **\<Source Control Server>** per abilitare l'opzione di menu Di avvio, su *1* per disabilitare l'opzione di menu e su *2* per nascondere l'opzione di menu. Se questa voce del Registro di sistema non viene visualizzata, il comportamento predefinito è visualizzare l'opzione di menu.

   | Voce del Registro di sistema di esempio | Valore di esempio |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Aggiungere la sottochiave **SourceCodeControlProvider** sotto la HKEY_LOCAL_MACHINE **chiave** nella **sottochiave SOFTWARE.**

    In questa sottochiave la voce del Registro di sistema **ProviderRegKey** è impostata su una stringa che rappresenta la sottochiave inserita nel Registro di sistema nel passaggio 1. Il modello **è** HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKeySOFTWARE<nome della società  =  *<nome del \\ \> \\ prodotto. \>*

    Di seguito è riportato il contenuto di esempio per questa sottochiave.

   |Voce del Registro di sistema|Valore di esempio|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Il plug-in del controllo del codice sorgente userà gli stessi nomi di sottochiave e voce, ma il valore sarà diverso.

4. Creare una sottochiave **denominata InstalledSCCProviders** nella sottochiave **SourceCodeControlProvider** e quindi inserire una voce sotto tale sottochiave.

    Il nome di questa voce è il nome leggibile dall'utente del provider (uguale al valore specificato per la voce SCCServerName) e il valore è, ancora una volta, la sottochiave creata nel passaggio 1. Il modello èHKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders **\\<nome \> visualizzato**  =  *SOFTWARE<nome della società \\<nome del \> \\ prodotto \>*.

    Esempio:

   |Voce del Registro di sistema di esempio|Valore di esempio|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > In questo modo possono essere registrati più plug-in di controllo del codice sorgente. In questo modo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono trovati tutti i plug-in basati su API di controllo del codice sorgente installati.

## <a name="how-an-ide-locates-the-dll"></a>Come un IDE individua la DLL
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'IDE ha due modi per trovare la DLL del plug-in del controllo del codice sorgente:

- Trovare il plug-in di controllo del codice sorgente predefinito e connettersi a esso in modo invisibile all'utente.

- Trovare tutti i plug-in del controllo del codice sorgente registrati, da cui l'utente ne sceglie uno.

  Per individuare la DLL nel primo modo, l'IDE cerca nella sottochiave **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** per la voce **ProviderRegKey**. Il valore di questa voce punta a un'altra sottochiave. L'IDE cerca quindi una voce denominata **SccServerPath** nella seconda sottochiave in **HKEY_LOCAL_MACHINE**. Il valore di questa voce punta all'IDE alla DLL.

> [!NOTE]
> L'IDE non carica le DLL dai percorsi relativi (ad esempio, *.\NewProvider.DLL*). È necessario specificare un percorso completo della DLL, ad esempio *c:\Providers\NewProvider.DLL*. Ciò consente di rafforzare la sicurezza dell'IDE impedendo il caricamento di DLL plug-in non autorizzate o rappresentate.

 Per individuare la DLL nel secondo modo, l'IDE cerca tutte le voci **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** sotto la sottochiave . Ogni voce ha un nome e un valore. L'IDE visualizza un elenco di questi nomi all'utente. Quando l'utente sceglie un nome, l'IDE trova il valore per il nome selezionato che punta a una sottochiave. L'IDE cerca una voce denominata **SccServerPath** in tale sottochiave **in HKEY_LOCAL_MACHINE**. Il valore di tale voce punta all'IDE alla DLL corretta.

 Un plug-in del controllo del codice sorgente deve supportare entrambi i modi di trovare la DLL e, di conseguenza, imposta **ProviderRegKey**, sovrascrivendo qualsiasi impostazione precedente. Ancora più importante, deve aggiungersi all'elenco **di InstalledSccProviders** in modo che l'utente possa scegliere quale plug-in del controllo del codice sorgente usare.

> [!NOTE]
> Poiché  viene usata la chiave HKEY_LOCAL_MACHINE, è possibile registrare un solo plug-in di controllo del codice sorgente come plug-in predefinito del controllo del codice sorgente in un determinato computer (tuttavia, consente agli utenti di determinare quale plug-in del controllo del codice sorgente vuole effettivamente usare per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] una determinata soluzione). Durante il processo di installazione, verificare se un plug-in del controllo del codice sorgente è già impostato. In tal caso, chiedere all'utente se impostare o meno il nuovo plug-in di controllo del codice sorgente installato come predefinito. Durante la disinstallazione, non rimuovere altre sottochiavi del Registro di sistema comuni a tutti i plug-in del controllo del codice sorgente in **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; rimuovere solo la sottochiave SCC specifica.

## <a name="how-the-ide-detects-version-1213-support"></a>Come l'IDE rileva il supporto della versione 1.2/1.3
 In che modo viene rilevato se un plug-in supporta le funzionalità dell'API plug-in di controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versione 1.2 e 1.3? Per dichiarare funzionalità avanzate, il plug-in del controllo del codice sorgente deve implementare la funzione corrispondente:

 Innanzitutto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controlla il valore restituito chiamando [SccGetVersion](../../extensibility/sccgetversion-function.md). Deve essere maggiore o uguale a 1,2.

 Determina quindi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se la nuova funzionalità specifica è supportata esaminando `lpSccCaps` l'argomento in [SccInitialize.](../../extensibility/sccinitialize-function.md)

 Se vengono soddisfatte entrambe queste condizioni, è possibile chiamare le nuove funzioni supportate nelle versioni 1.2 e 1.3.

## <a name="see-also"></a>Vedi anche
- [Introduzione ai plug-in del controllo del codice sorgente](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
