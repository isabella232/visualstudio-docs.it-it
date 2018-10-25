---
title: 'Procedura: installare un plug-in del controllo del codice sorgente | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f8c442aec21042faa4aa992dcdefc4f9d2ad335
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812985"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Procedura: installare un plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Creazione di un controllo del codice sorgente del plug-in include tre passaggi:  
  
1.  Creare una DLL con le funzioni definite nella sezione riferimenti API dei plug-in del controllo origine di questa documentazione.  
  
2.  Implementare le funzioni definite dall'API dei plug-in del controllo origine. Quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] chiamate, rendere le interfacce e le finestre di dialogo disponibili dal plug-in.  
  
3.  Registrare la DLL, rendendo le voci del Registro di sistema appropriate.  
  
## <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta plug-in di controllo di origine che è conforme all'API di plug-in controllo di origine.  
  
### <a name="registering-the-source-control-plug-in"></a>Registrare il plug-in del controllo del codice sorgente  
 Prima di chiama un ambiente di sviluppo integrato (IDE) in esecuzione nel sistema di controllo di origine, è necessario innanzitutto trovare l'origine DLL plug-in che consente di esportare l'API di controllo.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Per registrare l'origine controllare DLL plug-in  
  
1.  Aggiungere due voci nella chiave HKEY_LOCAL_MACHINE nella sottochiave del SOFTWARE che specifica la sottochiave nome società aggiungendo la sottochiave del nome di prodotto. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\\ *[nome azienda]*\\ *[nome del prodotto]*\\ *[entry]* = valore. Le due voci vengono sempre chiamate SCCServerName e SCCServerPath. Ognuno è una stringa normale.  
  
     Ad esempio, se il nome della società è Microsoft e il controllo del codice sorgente è denominato SourceSafe, questo percorso del Registro di sistema sarebbe HKEY_LOCAL_MACHINE\Software\Microsoft\SourceSafe. Questa sottochiave, la prima voce, SCCServerName, è una stringa leggibile dall'utente di denominazione del prodotto. La seconda voce, SCCServerPath, è il percorso completo all'origine controllare DLL plug-in cui deve connettersi l'IDE. Di seguito sono riportate le voci del Registro di sistema di esempio:  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  Il SCCServerPath è il percorso completo per il plug-in SourceSafe. Controllo del codice sorgente del plug-in userà i nomi di società e prodotti diversi ma gli stessi percorsi di voce del Registro di sistema.  
  
2.  Le seguenti voci del Registro di sistema facoltativo sono utilizzabile per modificare il comportamento del controllo del codice sorgente del plug-in. Queste voci passare nella sottochiave stessa come SccServerName e SccServerPath.  
  
    -   La voce HideInVisualStudioregistry può essere usata se non si desidera l'origine-plug-in controllo venga visualizzato nell'elenco di selezione dei plug-in di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Questa voce influirà anche su un passaggio automatico per il plug-in del controllo del codice sorgente. Un possibile utilizzo di questa voce è se è fornire un pacchetto del controllo codice sorgente che sostituisce i plug-in del controllo del codice sorgente ma si vuole semplificare per l'utente di eseguire la migrazione tramite il controllo del codice sorgente del plug-in per il pacchetto del controllo codice sorgente. Quando viene installato il pacchetto del controllo codice sorgente, imposta questa voce del Registro di sistema, che nasconde il plug-in.  
  
         HideInVisualStudio è un valore DWORD e viene impostato su 1 per nascondere il plug-in o 0 per mostrare il plug-in. Se non viene visualizzata la voce del Registro di sistema, il comportamento predefinito è per mostrare il plug-in.  
  
    -   La voce del Registro di sistema DisableSccManager consente di disabilitare o nascondere il **avviare \<Server di controllo di origine >** opzione di menu che in genere viene visualizzato sotto il **File**  ->   **Controllo del codice sorgente** sottomenu. Selezionare questo menu opzione chiama il [SccRunScc](../../extensibility/sccrunscc-function.md) (funzione). Plug-in del controllo del codice sorgente potrebbe non supportare un programma esterno e pertanto è possibile disabilitare o nascondere anche le **avviare** opzione di menu.  
  
         DisableSccManager è un valore DWORD è impostato su 0 per abilitare la **avvio veloce \<Server di controllo di origine >** opzione di menu, impostare su 1 per disabilitare l'opzione di menu e impostato su 2 per nascondere l'opzione di menu. Se questa voce del Registro di sistema non viene visualizzato, il comportamento predefinito è visualizzare l'opzione di menu.  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Aggiungere la sottochiave SourceCodeControlProvider, sotto la chiave HKEY_LOCAL_MACHINE nella sottochiave del SOFTWARE.  
  
     Sotto questa sottochiave è impostata la voce del Registro di sistema ProviderRegKey a una stringa che rappresenta la sottochiave che è stato inserito nel Registro di sistema nel passaggio 1. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = SOFTWARE\\ *[nome azienda]*\\ *[nome del prodotto]*.  
  
     Di seguito è riportato il contenuto di esempio per questa sottochiave.  
  
    |Voce del Registro di sistema|Valore di esempio|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Controllo del codice sorgente del plug-in userà la stessa sottochiave e i nomi delle voci, ma il valore sarà diverso.  
  
4.  Creare una sottochiave denominata InstalledSCCProviders sottochiave SourceCodeControlProvider e quindi inserire una voce sotto tale sottochiave.  
  
     Il nome di questa voce è il nome leggibile dall'utente del provider (lo stesso come il valore specificato per la voce SCCServerName) e il valore è, ancora una volta, la sottochiave creata nel passaggio 1. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\ *[DisplayName]* = SOFTWARE\\ *[nome azienda]* \\ *[nome del prodotto]*.  
  
     Ad esempio:  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Possono esistere più origine plug-in del controllo registrato in questo modo. Si tratta di come [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Trova tutti installati plug-in basato su API dei plug-in del controllo origine.  
  
## <a name="how-an-ide-locates-the-dll"></a>Modalità di individuazione della DLL di un IDE  
 Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE offre due modi per trovare l'origine controllano DLL plug-in:  
  
- Trovare il controllo del codice sorgente predefinito plug-in e connettersi ad esso in modo invisibile.  
  
- Trova origine registrata tutti i plug-in del controllo, da cui l'utente sceglie una.  
  
  Per individuare la DLL il primo modo, l'IDE cerca nella sottochiave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider per la voce ProviderRegKey. Il valore di questa voce punta a un'altra sottochiave. L'IDE cerca quindi una voce denominata SccServerPath nella seconda sottochiave in HKEY_LOCAL_MACHINE. Il valore di questa voce punta IDE alla DLL.  
  
> [!NOTE]
>  L'IDE non caricare le DLL da percorsi relativi (ad esempio,.\NewProvider.DLL). Specificare un percorso completo alla DLL (ad esempio, c:\Providers\NewProvider.DLL). Ciò aumenta la protezione dell'IDE, impedendo il caricamento delle DLL del plug-in non autorizzati o rappresentato.  
  
 Per individuare la DLL il secondo modo, l'IDE è simile per tutte le voci nella sottochiave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders<em>.</em> Ogni voce ha un nome e un valore. L'IDE visualizza un elenco di questi nomi per l'utente<em>.</em> Quando l'utente sceglie un nome, l'IDE rileva che il valore per il nome selezionato che punta a una sottochiave. L'IDE cerca una voce denominata SccServerPath in tale sottochiave in HKEY_LOCAL_MACHINE. Il valore di tale voce punta IDE alla DLL corretta.  
  
 Un plug-in del controllo del codice sorgente deve supportare entrambi i metodi di individuazione della DLL e, di conseguenza, impostare ProviderRegKey, sovrascrivendo qualsiasi impostazione precedente. Ancora più importante, è necessario aggiungere se stesso all'elenco di InstalledSccProviders in modo che l'utente può avere una scelta di quale plug-in del controllo del codice sorgente da utilizzare.  
  
> [!NOTE]
>  Poiché viene usata la chiave HKEY_LOCAL_MACHINE, controllo del codice sorgente di un solo plug-in può essere registrato come controllo del codice sorgente l'impostazione predefinita del plug-in un determinato computer (tuttavia, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] consente agli utenti di determinare quale controllo del codice sorgente del plug-in si intende utilizzare per un soluzione specifica). Durante il processo di installazione, verificare se è già impostato un plug-in del controllo del codice sorgente; In questo caso, chiedere all'utente di impostare il controllo del codice sorgente nuovo plug-in viene installato come valore predefinito o meno. Durante la disinstallazione, non rimuovere altri sottochiavi del Registro di sistema che sono comuni a tutte le origine plug-in del controllo in HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; rimuovere solo la sottochiave SCC particolare.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Come l'IDE rileva versione 1.2 o 1.3 supporto  
 Come viene [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rilevare la presenza di una funzionalità di versione 1.2 e 1.3 plug-in supporta API dei plug-in del controllo origine? Per dichiarare funzionalità avanzata, il plug-in del controllo del codice sorgente deve implementare la funzione corrispondente.  
  
 Prima di tutto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] controlla il valore restituito dalla chiamata di [SccGetVersion](../../extensibility/sccgetversion-function.md). Deve essere maggiore o uguale a 1.2.  
  
 Successivamente, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] determina se la nuova funzionalità specifica è supportata esaminando il `lpSccCaps` argomento per il [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Se entrambe queste condizioni vengono soddisfatte, le nuove funzioni supportate nelle versioni 1.2 e 1.3 possono essere chiamate.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

