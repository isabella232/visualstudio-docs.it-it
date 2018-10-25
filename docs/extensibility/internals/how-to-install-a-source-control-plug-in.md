---
title: 'Procedura: installare un plug-in del controllo del codice sorgente | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3487c796661a8194b9c920f43bae9df87f1ba57d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950264"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Procedura: installare un plug-in del controllo del codice sorgente
Creazione di un controllo del codice sorgente del plug-in include tre passaggi:  

1. Creare una DLL con le funzioni definite nella sezione riferimenti API dei plug-in del controllo origine di questa documentazione.  

2. Implementare le funzioni definite dall'API dei plug-in del controllo origine. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiamate, rendere le interfacce e le finestre di dialogo disponibili dal plug-in.  

3. Registrare la DLL, rendendo le voci del Registro di sistema appropriate.  

## <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta plug-in di controllo di origine che è conforme all'API di plug-in controllo di origine.  

### <a name="register-the-source-control-plug-in"></a>Registrare il plug-in del controllo del codice sorgente  
 Prima di chiama un ambiente di sviluppo integrato (IDE) in esecuzione nel sistema di controllo di origine, è necessario innanzitutto trovare l'origine DLL plug-in che consente di esportare l'API di controllo.  

#### <a name="to-register-the-source-control-plug-in-dll"></a>Per registrare l'origine controllare DLL plug-in  

1. Aggiungere due voci con i **HKEY_LOCAL_MACHINE** chiave nel **SOFTWARE** sottochiave che specifica la sottochiave nome società aggiungendo la sottochiave del nome di prodotto. Il modello consiste **HKEY_LOCAL_MACHINE\SOFTWARE\\\<nome società >\\\<nome prodotto >\\\<voce >**  =  *valore*. Le due voci vengono sempre chiamate **SCCServerName** e **SCCServerPath**. Ognuno è una stringa normale.  

    Ad esempio, se il nome della società è Microsoft e il controllo del codice sorgente è denominato SourceSafe, quindi questo percorso del Registro di sistema sarebbe **HKEY_LOCAL_MACHINE\Software\Microsoft\SourceSafe.**. Questa sottochiave, la prima voce **SCCServerName**, è una stringa leggibile dall'utente di denominazione del prodotto. La seconda voce **SCCServerPath**, il percorso completo all'origine di controllare le DLL del plug-in cui deve connettersi l'IDE. Di seguito sono riportate le voci del Registro di sistema di esempio:  

   |Voce del Registro di sistema di esempio|Valore di esempio|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|  

   > [!NOTE]
   >  SCCServerPath è il percorso completo per il plug-in SourceSafe. Controllo del codice sorgente del plug-in userà i nomi di società e prodotti diversi ma gli stessi percorsi di voce del Registro di sistema.  

2. Le seguenti voci del Registro di sistema facoltativo sono utilizzabile per modificare il comportamento del controllo del codice sorgente del plug-in. Passare queste voci nella sottochiave stessa come **SccServerName** e **SccServerPath**.  

   - Il **HideInVisualStudioregistry** voce può essere usata se non si desidera l'origine-plug-in controllo dalla finestra di **Selezione plug-in** elenco di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Questa voce influirà anche su un passaggio automatico per il plug-in del controllo del codice sorgente. Un possibile utilizzo di questa voce è se è fornire un pacchetto del controllo codice sorgente che sostituisce i plug-in del controllo del codice sorgente ma si vuole semplificare per l'utente di eseguire la migrazione tramite il controllo del codice sorgente del plug-in per il pacchetto del controllo codice sorgente. Quando viene installato il pacchetto del controllo codice sorgente, imposta questa voce del Registro di sistema, che nasconde il plug-in.  

      **HideInVisualStudio** è un valore DWORD e viene impostato su *1* per nascondere il plug-in o *0* per mostrare il plug-in. Se non viene visualizzata la voce del Registro di sistema, il comportamento predefinito è per mostrare il plug-in.  

   - Il **DisableSccManager** voce del Registro di sistema può essere usato per disabilitare o nascondere il **avviare \<Source Control Server >** opzioni di menu che in genere viene visualizzato sotto il **File**  >  **Controllo del codice sorgente** sottomenu. Selezionare questo menu opzione chiama il [SccRunScc](../../extensibility/sccrunscc-function.md) (funzione). Plug-in del controllo del codice sorgente potrebbe non supportare un programma esterno e pertanto è possibile disabilitare o nascondere anche le **avviare** opzione di menu.  

      **DisableSccManager** è un valore DWORD e viene impostato su *0* per abilitare il **avviare \<Source Control Server >** opzione di menu, impostare *1* per disabilitare l'opzione di menu e impostato su *2* per nascondere l'opzione di menu. Se questa voce del Registro di sistema non viene visualizzato, il comportamento predefinito è visualizzare l'opzione di menu.  

   | Voce del Registro di sistema di esempio | Valore di esempio |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |


3. Aggiungere la sottochiave **SourceCodeControlProvider**, sotto il **HKEY_LOCAL_MACHINE** chiave nel **SOFTWARE** sottochiave.  

    Sotto questa sottochiave, la voce del Registro di sistema **ProviderRegKey** è impostato su una stringa che rappresenta la sottochiave che è stato inserito nel Registro di sistema nel passaggio 1. Il modello consiste **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *SOFTWARE\\< nome società\>\\< nome del prodotto \>*.  

    Di seguito è riportato il contenuto di esempio per questa sottochiave.  

   |Voce del Registro di sistema|Valore di esempio|  
   |--------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Controllo del codice sorgente del plug-in userà la stessa sottochiave e i nomi delle voci, ma il valore sarà diverso.  

4. Creare una sottochiave denominata **InstalledSCCProviders** sotto il **SourceCodeControlProvider** sottochiave e quindi inserire una voce sotto tale sottochiave.  

    Il nome di questa voce è il nome leggibile dall'utente del provider (lo stesso come il valore specificato per la voce SCCServerName) e il valore è, ancora una volta, la sottochiave creata nel passaggio 1. Il modello consiste **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<display name>** = *SOFTWARE\\< nome società\> \\< nome del prodotto\>*.  

    Ad esempio:  

   |Voce del Registro di sistema di esempio|Valore di esempio|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Possono esistere più origine plug-in del controllo registrato in questo modo. Si tratta di come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Trova tutti installati plug-in basato su API dei plug-in del controllo origine.  

## <a name="how-an-ide-locates-the-dll"></a>Modalità di individuazione della DLL di un IDE  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE offre due modi per trovare l'origine controllano DLL plug-in:  

- Trovare il controllo del codice sorgente predefinito plug-in e connettersi ad esso in modo invisibile.  

- Trova origine registrata tutti i plug-in del controllo, da cui l'utente sceglie una.  

  Per individuare la DLL il primo modo, l'IDE cerca sotto il **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** sottochiave per la voce **ProviderRegKey**. Il valore di questa voce punta a un'altra sottochiave. L'IDE cerca una voce denominata **SccServerPath** in tale sottochiave nella seconda **HKEY_LOCAL_MACHINE**. Il valore di questa voce punta IDE alla DLL.  

> [!NOTE]
>  L'IDE non caricare le DLL da percorsi relativi (ad esempio, *.\NewProvider.DLL*). Specificare un percorso completo alla DLL (ad esempio, *c:\Providers\NewProvider.DLL*). Ciò aumenta la protezione dell'IDE, impedendo il caricamento delle DLL del plug-in non autorizzati o rappresentato.  

 Per individuare la DLL il secondo modo, l'IDE cerca sotto il **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** sottochiave per tutte le voci. Ogni voce ha un nome e un valore. L'IDE visualizza un elenco di questi nomi per l'utente. Quando l'utente sceglie un nome, l'IDE rileva che il valore per il nome selezionato che punta a una sottochiave. L'IDE cerca una voce denominata **SccServerPath** in tale sottochiave **HKEY_LOCAL_MACHINE**. Il valore di tale voce punta IDE alla DLL corretta.  

 Un plug-in del controllo del codice sorgente è necessario supportare entrambe le modalità di individuazione della DLL e, di conseguenza, imposta **ProviderRegKey**, sovrascrivendo qualsiasi impostazione precedente. Ancora più importante, è necessario aggiungere se stesso all'elenco di **InstalledSccProviders** in modo che l'utente può avere una scelta di quale plug-in del controllo del codice sorgente da utilizzare.  

> [!NOTE]
>  Poiché il **HKEY_LOCAL_MACHINE** chiave viene usata, controllo del codice sorgente di un solo plug-in può essere registrato come controllo del codice sorgente l'impostazione predefinita del plug-in un determinato computer (tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente agli utenti di determinare quale plug-in del controllo del codice sorgente si desidera effettivamente utilizzare per una particolare soluzione). Durante il processo di installazione, verificare se è già impostato un plug-in del controllo del codice sorgente; In questo caso, chiedere all'utente di impostare il controllo del codice sorgente nuovo plug-in viene installato come valore predefinito o meno. Durante la disinstallazione, non rimuovere altri sottochiavi del Registro di sistema che sono comuni a tutte le origine plug-in del controllo nella **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; rimuovere solo la sottochiave SCC particolare.  

## <a name="how-the-ide-detects-version-1213-support"></a>Come l'IDE rileva il supporto della versione 1.2 o 1.3  
 Come viene [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rilevare la presenza di una funzionalità di versione 1.2 e 1.3 plug-in supporta API dei plug-in del controllo origine? Per dichiarare funzionalità avanzata, il plug-in del controllo del codice sorgente deve implementare la funzione corrispondente:  

 Prima di tutto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controlla il valore restituito dalla chiamata di [SccGetVersion](../../extensibility/sccgetversion-function.md). Deve essere maggiore o uguale a 1.2.  

 Successivamente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina se la nuova funzionalità specifica è supportata esaminando il `lpSccCaps` argomento per il [SccInitialize](../../extensibility/sccinitialize-function.md).  

 Se entrambe queste condizioni vengono soddisfatte, le nuove funzioni supportate nelle versioni 1.2 e 1.3 possono essere chiamate.  

## <a name="see-also"></a>Vedere anche  
 [Introduzione a plug-in controllo codice sorgente](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)