---
title: 'Procedura: installare un plug-in per il controllo del codice sorgente Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707999"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Procedura: installare un plug-in del controllo del codice sorgenteHow to: Install a source control plug-in
La creazione di un plug-in del controllo del codice sorgente prevede tre passaggi:Creating a source-control plug-in involves three steps:

1. Creare una DLL con le funzioni definite nella sezione di riferimento dell'API del plug-in del controllo del codice sorgente di questa documentazione.

2. Implementare le funzioni definite dall'API plug-in del controllo del codice sorgente. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene chiamato, rendere le interfacce e le finestre di dialogo disponibili dal plug-in.

3. Registrare la DLL creando le voci del Registro di sistema appropriate.

## <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta i plug-in del controllo del codice sorgente conformi all'API del plug-in del controllo del codice sorgente.

### <a name="register-the-source-control-plug-in"></a>Registrare il plug-in del controllo del codice sorgenteRegister the source control plug-in
 Prima che un ambiente di sviluppo integrato (IDE) in esecuzione possa chiamare nel sistema di controllo del codice sorgente, è necessario trovare la DLL del plug-in del controllo del codice sorgente che esporta l'API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Per registrare la DLL del plug-in del controllo del codice sorgente

1. Aggiungere due voci nella **chiave HKEY_LOCAL_MACHINE** della sottochiave **SOFTWARE** che specifica la sottochiave del nome della società seguita dalla sottochiave del nome del prodotto. Il modello è **HKEY_LOCAL_MACHINE:\\\< \\ \<il nome \\ \<della società>il nome del prodotto>la voce>**  =  *valore*. Le due voci sono sempre denominate **SCCServerName** e **SCCServerPath**. Ognuna è una stringa normale.

    Se, ad esempio, il nome della società è Microsoft e il prodotto del controllo del codice sorgente è denominato SourceSafe, il percorso del Registro di sistema sarà **HKEY_LOCAL_MACHINE SOFTWARE**. In questa sottochiave, la prima voce, **SCCServerName**, è una stringa leggibile dall'utente che denomina il prodotto. La seconda voce, **SCCServerPath**, è il percorso completo della DLL del plug-in del controllo del codice sorgente a cui l'IDE deve connettersi. Di seguito vengono fornite voci del Registro di sistema di esempio:The following provides sample registry entries:

   |Voce del Registro di sistema di esempio|Valore di esempio|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE SOFTWARE Microsoft SourceSafe NomeServer SCC|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE SOFTWARE Microsoft SourceSafe SCCServerPath|*c: vss win32 ssscc.dll*|

   > [!NOTE]
   > SCCServerPath è il percorso completo del plug-in di SourceSafe. Il plug-in del controllo del codice sorgente utilizzerà nomi di società e prodotti diversi, ma gli stessi percorsi delle voci del Registro di sistema.

2. Le seguenti voci facoltative del Registro di sistema possono essere utilizzate per modificare il comportamento del plug-in del controllo del codice sorgente. Queste voci si ripercano nella stessa sottochiave **di SccServerName** e **SccServerPath**.

   - La voce **HideInVisualStudioregistry** può essere utilizzata se non si desidera che il plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]del controllo del codice sorgente venga visualizzato nell'elenco **Selezione plug-in** di . Questa voce influirà anche sul passaggio automatico al plug-in del controllo del codice sorgente. Un possibile utilizzo di questa voce è se si fornisce un pacchetto di controllo del codice sorgente che sostituisce il plug-in del controllo del codice sorgente, ma si desidera semplificare la migrazione dell'utente dall'utilizzo del plug-in del controllo del codice sorgente al pacchetto del controllo del codice sorgente. Quando viene installato il pacchetto del controllo del codice sorgente, imposta questa voce del Registro di sistema, che nasconde il plug-in.

      **HideInVisualStudio** è un valore DWORD ed è impostato su *1* per nascondere il plug-in o *su 0* per visualizzare il plug-in. Se la voce del Registro di sistema non viene visualizzata, il comportamento predefinito prevede la visualizzazione del plug-in.

   - La voce del Registro di sistema **DisableSccManager** può essere utilizzata per disattivare o nascondere l'opzione di menu **Avvia \<** server controllo del codice sorgente>che normalmente viene visualizzata nel sottomenu**Controllo origine** **file.** >  La selezione di questa opzione di menu chiama la funzione [SccRunScc.](../../extensibility/sccrunscc-function.md) Il plug-in del controllo del codice sorgente potrebbe non supportare un programma esterno e pertanto è possibile disattivare o addirittura nascondere l'opzione di menu **di avvio.**

      **DisableSccManager** è un valore DWORD ed è impostato su *0* per abilitare l'opzione di menu *2* Avvia *1* ** \<** server del controllo del codice sorgente>, impostata su 1 per disabilitare l'opzione di menu e impostata su 2 per nascondere l'opzione di menu. Se questa voce del Registro di sistema non viene visualizzata, il comportamento predefinito prevede la visualizzazione dell'opzione di menu.

   | Voce del Registro di sistema di esempio | Valore di esempio |
   | - |--------------|
   | HKEY_LOCAL_MACHINE SOFTWARE Microsoft SourceSafe HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE SOFTWARE Microsoft SourceSafe DisableSccManager | 1 |

3. Aggiungere la sottochiave **SourceCodeControlProvider**, nella **chiave HKEY_LOCAL_MACHINE** della sottochiave **SOFTWARE.**

    In questa sottochiave, la voce del Registro di sistema **ProviderRegKey** è impostata su una stringa che rappresenta la sottochiave inserita nel Registro di sistema nel passaggio 1. Il modello è HKEY_LOCAL_MACHINE SOFTWARE HKEY_LOCAL_MACHINE SOFTWARE , **SOFTWARE , SourceCodeControlProvider , ProviderRegKey** = SOFTWARE*\\ \> \\<nome\>* della società<nome del prodotto .

    Di seguito è riportato il contenuto di esempio per questa sottochiave.

   |Voce del Registro di sistema|Valore di esempio|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE SOFTWARE SourceCodeControlProvider|SOFTWARE: Microsoft SourceSafe|

   > [!NOTE]
   > Il plug-in del controllo del codice sorgente utilizzerà gli stessi nomi di sottochiave e voce, ma il valore sarà diverso.

4. Creare una sottochiave denominata **InstalledSCCProviders** nella sottochiave **SourceCodeControlProvider,** quindi inserire una voce in tale sottochiave.

    Il nome di questa voce è il nome leggibile dall'utente del provider (uguale al valore specificato per la voce SCCServerName) e il valore è, ancora una volta, la sottochiave creata nel passaggio 1. Il modello è **HKEY_LOCAL_MACHINE SOFTWARE, SourceCodeControlProvider,\\ InstalledSCCProviders<\>nome** = visualizzato SOFTWARE*\\<nome\> \\ della società<nome\>del prodotto*.

    Ad esempio:

   |Voce del Registro di sistema di esempio|Valore di esempio|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE SOFTWARE SourceCodeControlProvider , InstalledSCCProviders , Microsoft Visual SourceSafe|SOFTWARE: Microsoft SourceSafe|

   > [!NOTE]
   > In questo modo possono essere registrati più plug-in del controllo del codice sorgente. Questo è [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il modo in cui trova tutti i plug-in basati su API del plug-in del controllo del codice sorgente installati.

## <a name="how-an-ide-locates-the-dll"></a>Modalità di individuazione della DLL da parte di un IDE
 L'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dispone di due modi per trovare la DLL del plug-in del controllo del codice sorgente:

- Trovare il plug-in del controllo del codice sorgente predefinito e connettersi ad esso in modo invisibile all'utente.

- Trovare tutti i plug-in del controllo del codice sorgente registrati, da cui l'utente sceglie uno.

  Per individuare la DLL nel primo modo, l'IDE cerca la voce **ProviderRegKey**nella sottochiave di HKEY_LOCAL_MACHINE , **Software, SourceCodeControlProvider** . Il valore di questa voce punta a un'altra sottochiave. L'IDE cerca quindi una voce denominata **SccServerPath** nella seconda sottochiave **in HKEY_LOCAL_MACHINE**. Il valore di questa voce punta l'IDE alla DLL.

> [!NOTE]
> L'IDE non carica le DLL da percorsi relativi (ad esempio, *.* È necessario specificare un percorso completo per la DLL (ad esempio, *c:* In questo modo viene rafforzata la sicurezza dell'IDE impedendo il caricamento di DLL di plug-in non autorizzate o rappresentate.

 Per individuare la DLL nel secondo modo, l'IDE cerca tutte le voci nella sottochiave **HKEY_LOCAL_MACHINE** . Ogni voce ha un nome e un valore. L'IDE visualizza un elenco di questi nomi per l'utente. Quando l'utente sceglie un nome, l'IDE trova il valore per il nome selezionato che punta a una sottochiave. L'IDE cerca una voce denominata **SccServerPath** in tale sottochiave in **HKEY_LOCAL_MACHINE**. Il valore di tale voce punta l'IDE alla DLL corretta.

 Un plug-in del controllo del codice sorgente deve supportare entrambe le modalità di individuazione della DLL e, di conseguenza, imposta **ProviderRegKey**, sovrascrivendo qualsiasi impostazione precedente. Ancora più importante, è necessario aggiungere se stesso all'elenco di **InstalledSccProviders** in modo che l'utente può avere una scelta di quale plug-in controllo del codice sorgente da utilizzare.

> [!NOTE]
> Poiché viene utilizzato il **HKEY_LOCAL_MACHINE** chiave, solo un plug-in del controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può essere registrato come plug-in del controllo del codice sorgente predefinito in un determinato computer (tuttavia, consente agli utenti di determinare quale plug-in del controllo del codice sorgente che desiderano utilizzare effettivamente per una determinata soluzione). Durante il processo di installazione, verificare se un plug-in del controllo del codice sorgente è già impostato; in caso affermativo, chiedere all'utente se impostare o meno il nuovo plug-in del controllo del codice sorgente da installare come predefinito. Durante la disinstallazione, non rimuovere altre sottochiavi del Registro di sistema comuni a tutti i plug-in del controllo del codice sorgente in **HKEY_LOCAL_MACHINE SOFTWARE SourceCodeControlProvider**; rimuovere solo la sottochiave SCC specifica.

## <a name="how-the-ide-detects-version-1213-support"></a>Come l'IDE rileva il supporto della versione 1.2/1.3
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che modo rileva se un plug-in supporta la funzionalità dell'API del plug-in del controllo di codice sorgente versione 1.2 e 1.3? Per dichiarare funzionalità avanzate, il plug-in del controllo del codice sorgente deve implementare la funzione corrispondente:To declare advanced capability, the source control plug-in must implement the corresponding function:

 Innanzitutto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controlla il valore restituito chiamando il [SccGetVersion](../../extensibility/sccgetversion-function.md). Deve essere maggiore o uguale a 1,2.

 Successivamente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina se la nuova funzionalità specifica `lpSccCaps` è supportata esaminando l'argomento in [SccInitialize](../../extensibility/sccinitialize-function.md).

 Se entrambe queste condizioni vengono soddisfatte, è possibile chiamare le nuove funzioni supportate nelle versioni 1.2 e 1.3.

## <a name="see-also"></a>Vedere anche
- [Introduzione ai plug-in del controllo del codice sorgente](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
