---
title: Helper SDK per il debug | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3296613ffbe3148caa04989dfc9d609334b4c200
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840317"
---
# <a name="sdk-helpers-for-debugging"></a>Helper SDK per il debug
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Queste funzioni e dichiarazioni sono funzioni helper globali per l'implementazione di motori di debug, analizzatori di espressioni e provider di simboli in C++.  
  
> [!NOTE]
> Al momento non sono presenti versioni gestite di queste funzioni e dichiarazioni.  
  
## <a name="overview"></a>Panoramica  
 Affinché i motori di debug, gli analizzatori di espressioni e i provider di simboli vengano utilizzati da Visual Studio, è necessario registrarli. Questa operazione viene eseguita impostando le sottochiavi e le voci del registro di sistema, altrimenti note come "impostazione delle metriche". Le funzioni globali seguenti sono progettate per semplificare il processo di aggiornamento di queste metriche. Per informazioni sul layout di ogni sottochiave del registro di sistema aggiornata da queste funzioni, vedere la sezione relativa ai percorsi del registro di sistema.  
  
## <a name="general-metric-functions"></a>Funzioni metrica generali  
 Si tratta di funzioni generali usate dai motori di debug. Le funzioni specializzate per gli analizzatori di espressioni e i provider di simboli sono descritte in dettaglio in seguito  
  
### <a name="getmetric-method"></a>Getmetric (metodo)  
 Recupera un valore della metrica dal registro di sistema.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszMachine|in Nome di un computer remoto in cui verrà scritto il registro ( `NULL` indica il computer locale).|  
|pszType|in Uno dei tipi di metrica.|  
|guidSection|in GUID di un motore specifico, un analizzatore, un'eccezione e così via. Specifica una sottosezione sotto un tipo di metrica per un elemento specifico.|  
|pszMetric|in Metrica da ottenere. Corrisponde al nome di un valore specifico.|  
|pdwValue|in Posizione di archiviazione del valore dalla metrica. Sono disponibili diverse versioni di getmetric che possono restituire un valore DWORD (come in questo esempio), un BSTR, un GUID o una matrice di GUID.|  
|pszAltRoot|in Radice del registro di sistema alternativa da usare. Impostare su `NULL` per usare il valore predefinito.|  
  
### <a name="setmetric-method"></a>Metodo semetric  
 Imposta il valore della metrica specificato nel registro di sistema.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszType|in Uno dei tipi di metrica.|  
|guidSection|in GUID di un motore specifico, un analizzatore, un'eccezione e così via. Specifica una sottosezione sotto un tipo di metrica per un elemento specifico.|  
|pszMetric|in Metrica da ottenere. Corrisponde al nome di un valore specifico.|  
|dwValue|in Posizione di archiviazione del valore nella metrica. Esistono diverse versioni di semetrie che possono archiviare un valore DWORD (in questo esempio), un BSTR, un GUID o una matrice di GUID.|  
|fUserSpecific|in TRUE se la metrica è specifica dell'utente e se deve essere scritta nell'hive dell'utente anziché nell'hive del computer locale.|  
|pszAltRoot|in Radice del registro di sistema alternativa da usare. Impostare su `NULL` per usare il valore predefinito.|  
  
### <a name="removemetric-method"></a>Metodo RemoveMetric  
 Rimuove la metrica specificata dal registro di sistema.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszType|in Uno dei tipi di metrica.|  
|guidSection|in GUID di un motore specifico, un analizzatore, un'eccezione e così via. Specifica una sottosezione sotto un tipo di metrica per un elemento specifico.|  
|pszMetric|in Metrica da rimuovere. Corrisponde al nome di un valore specifico.|  
|pszAltRoot|in Radice del registro di sistema alternativa da usare. Impostare su `NULL` per usare il valore predefinito.|  
  
### <a name="enummetricsections-method"></a>Metodo EnumMetricSections  
 Enumera le varie sezioni della metrica nel registro di sistema.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszMachine|in Nome di un computer remoto in cui verrà scritto il registro ( `NULL` indica il computer locale).|  
|pszType|in Uno dei tipi di metrica.|  
|rgguidSections|[in, out] Matrice preallocata di GUID da compilare.|  
|pdwSize|in Numero massimo di GUID che è possibile archiviare nella `rgguidSections` matrice.|  
|pszAltRoot|in Radice del registro di sistema alternativa da usare. Impostare su `NULL` per usare il valore predefinito.|  
  
## <a name="expression-evaluator-functions"></a>Funzioni dell'analizzatore di espressioni  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetEEMetric|Recupera un valore della metrica dal registro di sistema.|  
|SetEEMetric|Imposta il valore della metrica specificato nel registro di sistema.|  
|RemoveEEMetric|Rimuove la metrica specificata dal registro di sistema.|  
|GetEEMetricFile|Ottiene un nome file dalla metrica specificata e lo carica, restituendo il contenuto del file sotto forma di stringa.|  
  
## <a name="exception-functions"></a>Funzioni di eccezione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetExceptionMetric|Recupera un valore della metrica dal registro di sistema.|  
|SetExceptionMetric|Imposta il valore della metrica specificato nel registro di sistema.|  
|RemoveExceptionMetric|Rimuove la metrica specificata dal registro di sistema.|  
|RemoveAllExceptionMetrics|Rimuove tutte le metriche di eccezione dal registro di sistema.|  
  
## <a name="symbol-provider-functions"></a>Funzioni del provider di simboli  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetSPMetric|Recupera un valore della metrica dal registro di sistema.|  
|SetSPMetric|Imposta il valore della metrica specificato nel registro di sistema.|  
|RemoveSPMetric|Rimuove la metrica specificata dal registro di sistema.|  
  
## <a name="enumeration-functions"></a>Funzioni di enumerazione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|EnumMetricSections|Enumera tutte le metriche per un tipo di metrica specificato.|  
|EnumDebugEngine|Enumera i motori di debug registrati.|  
|EnumEEs|Enumera gli analizzatori di espressioni registrati.|  
|EnumExceptionMetrics|Enumera tutte le metriche delle eccezioni.|  
  
## <a name="metric-definitions"></a>Definizioni delle metriche  
 Queste definizioni possono essere usate per i nomi delle metriche predefinite. I nomi corrispondono a diverse chiavi del registro di sistema e nomi di valore e sono tutti definiti come stringhe di caratteri wide: ad esempio, `extern LPCWSTR metrictypeEngine` .  
  
|Tipi di metrica predefiniti|Descrizione: chiave di base per....|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Tutte le metriche del motore di debug.|  
|metrictypePortSupplier|Tutte le metriche del fornitore della porta.|  
|metrictypeException|Tutte le metriche delle eccezioni.|  
|metricttypeEEExtension|Tutte le estensioni dell'analizzatore di espressioni.|  
  
|Proprietà del motore di debug|Descrizione|  
|-----------------------------|-----------------|  
|metricAddressBP|Impostare su un valore diverso da zero per indicare il supporto per i punti di interruzione dell'indirizzo.|  
|metricAlwaysLoadLocal|Impostare su un valore diverso da zero per caricare sempre localmente il motore di debug.|  
|metricLoadInDebuggeeSession|NON UTILIZZATO|  
|metricLoadedByDebuggee|Impostare su un valore diverso da zero per indicare che il motore di debug verrà sempre caricato con o dal programma di cui è in corso il debug.|  
|metricAttach|Impostare su un valore diverso da zero per indicare il supporto per l'allegato ai programmi esistenti.|  
|metricCallStackBP|Impostare su un valore diverso da zero per indicare il supporto per i punti di interruzione dello stack di chiamate.|  
|metricConditionalBP|Impostare su un valore diverso da zero per indicare il supporto per l'impostazione di punti di interruzione condizionali.|  
|metricDataBP|Impostare su un valore diverso da zero per indicare il supporto per l'impostazione dei punti di interruzione nelle modifiche ai dati.|  
|metricDisassembly|Impostare su un valore diverso da zero per indicare il supporto per la produzione di un elenco di Disassembly.|  
|metricDumpWriting|Impostare su un valore diverso da zero per indicare il supporto per la scrittura del dump, ovvero il dump della memoria in un dispositivo di output.|  
|metricENC|Impostare su un valore diverso da zero per indicare il supporto per modifica e continuazione. **Nota:**  Un motore di debug personalizzato non deve mai impostare questa impostazione o deve sempre impostarlo su 0.|  
|metricExceptions|Impostare su un valore diverso da zero per indicare il supporto per le eccezioni.|  
|metricFunctionBP|Impostare su un valore diverso da zero per indicare il supporto dei punti di interruzione denominati (punti di interruzione che si interrompono quando viene chiamato un determinato nome di funzione).|  
|metricHitCountBP|Impostare su un valore diverso da zero per indicare il supporto per l'impostazione di punti di interruzione (punti di interruzione) (punti di interruzione attivati solo dopo il raggiungimento di un determinato numero di volte).|  
|metricJITDebug|Impostare su un valore diverso da zero per indicare il supporto per il debug JIT (il debugger viene avviato quando si verifica un'eccezione in un processo in esecuzione).|  
|metricMemory|NON UTILIZZATO|  
|metricPortSupplier|Impostare questo oggetto sul CLSID del fornitore della porta, se ne è stato implementato uno.|  
|metricRegisters|NON UTILIZZATO|  
|metricSetNextStatement|Impostare su un valore diverso da zero per indicare il supporto per l'impostazione dell'istruzione successiva, che ignora l'esecuzione di istruzioni intermedie.|  
|metricSuspendThread|Impostare su un valore diverso da zero per indicare il supporto per la sospensione dell'esecuzione del thread.|  
|metricWarnIfNoSymbols|Impostare su un valore diverso da zero per indicare che l'utente deve ricevere una notifica se non sono presenti simboli.|  
|metricProgramProvider|Impostare questa impostazione sul CLSID del provider di programmi.|  
|metricAlwaysLoadProgramProviderLocal|Impostare questa impostazione su un valore diverso da zero per indicare che il provider del programma deve essere sempre caricato localmente.|  
|metricEngineCanWatchProcess|Impostare questa impostazione su un valore diverso da zero per indicare che il motore di debug eseguirà il controllo degli eventi di elaborazione anziché del provider di programmi.|  
|metricRemoteDebugging|Impostare questa impostazione su un valore diverso da zero per indicare il supporto per il debug remoto.|  
|metricEncUseNativeBuilder|Impostare questa impostazione su un valore diverso da zero per indicare che la gestione delle modifiche e delle continuazioni deve utilizzare la encbuild.dll del motore di debug per compilare per modifica e continuazione. **Nota:**  Un motore di debug personalizzato non deve mai impostare questa impostazione o deve sempre impostarlo su 0.|  
|metricLoadUnderWOW64|Impostare questa impostazione su un valore diverso da zero per indicare che è necessario caricare il motore di debug nel processo oggetto del debug in WOW durante il debug di un processo a 64 bit. in caso contrario, il motore di debug verrà caricato nel processo di Visual Studio (in esecuzione in WOW64).|  
|metricLoadProgramProviderUnderWOW64|Impostare questa impostazione su un valore diverso da zero per indicare che il provider del programma deve essere caricato nel processo oggetto del debug durante il debug di un processo a 64 bit in WOW; in caso contrario, verrà caricato nel processo di Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Impostare questa impostazione su un valore diverso da zero per indicare che il processo deve essere interrotto se viene generata un'eccezione non gestita attraverso i limiti del codice gestito/non gestito.|  
|metricAutoSelectPriority|Impostarla su una priorità per la selezione automatica del motore di debug (i valori più alti sono uguali a priorità più alta).|  
|metricAutoSelectIncompatibleList|Chiave del registro di sistema contenente le voci che specificano i GUID per i motori di debug da ignorare durante la selezione automatica. Queste voci sono un numero (0, 1, 2 e così via) con un GUID espresso come stringa.|  
|metricIncompatibleList|Chiave del registro di sistema contenente le voci che specificano i GUID per i motori di debug che non sono compatibili con questo motore di debug.|  
|metricDisableJITOptimization|Impostare questa impostazione su un valore diverso da zero per indicare che le ottimizzazioni JIT (per il codice gestito) devono essere disabilitate durante il debug.|  
  
|Proprietà dell'analizzatore di espressioni|Descrizione|  
|-------------------------------------|-----------------|  
|metricEngine|Che include il numero di motori di debug che supportano l'analizzatore di espressioni specificato.|  
|metricPreloadModules|Impostare questa impostazione su un valore diverso da zero per indicare che i moduli devono essere precaricati quando un analizzatore di espressioni viene avviato in un programma.|  
|metricThisObjectName|Impostare questa impostazione sul nome dell'oggetto "This".|  
  
|Proprietà dell'estensione dell'analizzatore di espressioni|Descrizione|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Nome della dll che supporta questa estensione.|  
|metricExtensionRegistersSupported|Elenco di registri supportati.|  
|metricExtensionRegistersEntryPoint|Punto di ingresso per l'accesso ai registri.|  
|metricExtensionTypesSupported|Elenco di tipi supportati.|  
|metricExtensionTypesEntryPoint|Punto di ingresso per l'accesso ai tipi.|  
  
|Proprietà fornitore porta|Descrizione|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Il CLSID della selezione della porta (una finestra di dialogo che l'utente può usare per selezionare le porte e aggiungere le porte da usare per il debug).|  
|metricDisallowUserEnteredPorts|Diverso da zero se le porte immesse dall'utente non possono essere aggiunte al fornitore della porta. in questo modo la finestra di dialogo Selezione porta è essenzialmente di sola lettura.|  
|metricPidBase|ID del processo di base utilizzato dal fornitore della porta durante l'allocazione degli ID processo.|  
  
|Tipi di archivio SP predefiniti|Descrizione|  
|-------------------------------|-----------------|  
|storetypeFile|I simboli vengono archiviati in un file separato.|  
|storetypeMetadata|I simboli vengono archiviati come metadati in un assembly.|  
  
|Proprietà varie|Descrizione|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Impostare questa impostazione su un valore diverso da zero per visualizzare il codice non utente.|  
|metricJustMyCodeStepping|Impostare questa impostazione su un valore diverso da zero per indicare che l'esecuzione dell'istruzione può essere eseguita solo nel codice utente.|  
|metricCLSID|CLSID per un oggetto di un tipo di metrica specifico.|  
|metricName|Nome descrittivo per un oggetto di un tipo di metrica specifico.|  
|metricLanguage|Nome della lingua.|  
  
## <a name="registry-locations"></a>Percorsi del registro di sistema  
 Le metriche vengono lette e scritte nel registro di sistema, in particolare nella `VisualStudio` sottochiave.  
  
> [!NOTE]
> Nella maggior parte dei casi, le metriche verranno scritte nella chiave HKEY_LOCAL_MACHINE. Tuttavia, a volte HKEY_CURRENT_USER sarà la chiave di destinazione. Dbgmetric. lib gestisce entrambe le chiavi. Quando si recupera una metrica, Cerca HKEY_CURRENT_USER prima, quindi HKEY_LOCAL_MACHINE. Quando si imposta una metrica, un parametro specifica la chiave di primo livello da usare.  
  
 *[chiave del registro di sistema]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[radice versione]*\  
  
 *[radice metrica]*\  
  
 *[tipo di metrica]*\  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[chiave del registro di sistema]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|  
|*[radice versione]*|Versione di Visual Studio (ad esempio,, `7.0` `7.1` o `8.0` ). Tuttavia, questa radice può anche essere modificata utilizzando l'opzione **/rootsuffix** per **devenv.exe**. Per VSIP, questo modificatore è in genere **Exp**, quindi la radice della versione sarebbe, ad esempio, 8.0 Exp.|  
|*[radice metrica]*|Si tratta `AD7Metrics` di o `AD7Metrics(Debug)` , a seconda che venga utilizzata la versione di debug di dbgmetric. lib. **Nota:**  Indipendentemente dal fatto che venga utilizzato dbgmetric. lib, è opportuno rispettare questa convenzione di denominazione se si riscontrano differenze tra le versioni di debug e di rilascio che devono essere riflesse nel registro di sistema.|  
|*[tipo di metrica]*|Tipo di metrica da scrivere:,, `Engine` `ExpressionEvaluator` `SymbolProvider` e così via. Sono tutti definiti come in dbgmetric. h come `metricTypeXXXX` , dove `XXXX` è il nome del tipo specifico.|  
|*metrica*|Nome di una voce a cui assegnare un valore per impostare la metrica. L'organizzazione effettiva della metrica dipende dal tipo di metrica.|  
|*[valore metrica]*|Valore assegnato alla metrica. Il tipo che il valore deve avere (stringa, numero e così via) dipende dalla metrica.|  
  
> [!NOTE]
> Tutti i GUID vengono archiviati nel formato `{GUID}` . Ad esempio: `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Motori di debug  
 Di seguito è riportata l'organizzazione delle metriche dei motori di debug nel registro di sistema. `Engine` è il nome del tipo di metrica per un motore di debug e corrisponde a *[tipo di metrica]* nel sottoalbero del registro di sistema precedente.  
  
 `Engine`\  
  
 *[GUID motore]*\  
  
 `CLSID` = *[GUID classe]*  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
 `PortSupplier`\  
  
 `0` = *[GUID fornitore porta]*  
  
 `1` = *[GUID fornitore porta]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[GUID motore]*|GUID del motore di debug.|  
|*[GUID classe]*|GUID della classe che implementa questo motore di debug.|  
|*[GUID fornitore porta]*|GUID del fornitore della porta, se disponibile. Molti motori di debug utilizzano il fornitore di porta predefinito e pertanto non specificano il proprio fornitore. In questo caso, la sottochiave `PortSupplier` sarà assente.|  
  
### <a name="port-suppliers"></a>Fornitori di porte  
 Di seguito è riportata l'organizzazione delle metriche del fornitore di porte nel registro di sistema. `PortSupplier` nome del tipo di metrica per un fornitore di porte e corrisponde a *[tipo di metrica]*.  
  
 `PortSupplier`\  
  
 *[GUID fornitore porta]*\  
  
 `CLSID` = *[GUID classe]*  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[GUID fornitore porta]*|GUID del fornitore della porta|  
|*[GUID classe]*|GUID della classe che implementa questo fornitore di porte|  
  
### <a name="symbol-providers"></a>Provider di simboli  
 Di seguito è riportata l'organizzazione delle metriche dei fornitori di simboli nel registro di sistema. `SymbolProvider` è il nome del tipo di metrica per il provider di simboli e corrisponde a *[tipo di metrica]*.  
  
 `SymbolProvider`\  
  
 *[GUID del provider di simboli]*\  
  
 `file`\  
  
 `CLSID` = *[GUID classe]*  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
 `metadata`\  
  
 `CLSID` = *[GUID classe]*  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[GUID del provider di simboli]*|GUID del provider di simboli|  
|*[GUID classe]*|GUID della classe che implementa il provider di simboli|  
  
### <a name="expression-evaluators"></a>Analizzatori di espressioni  
 Di seguito è illustrata l'organizzazione delle metriche dell'analizzatore di espressioni nel registro di sistema. `ExpressionEvaluator` nome del tipo di metrica per l'analizzatore di espressioni e corrisponde a *[tipo di metrica]*.  
  
> [!NOTE]
> Il tipo di metrica per `ExpressionEvaluator` non è definito in dbgmetric. h, perché si presuppone che tutte le modifiche della metrica per gli analizzatori di espressioni passino attraverso le funzioni metriche dell'analizzatore di espressioni appropriate (il layout della `ExpressionEvaluator` sottochiave è piuttosto complesso, quindi i dettagli sono nascosti all'interno di dbgmetric. lib).  
  
 `ExpressionEvaluator`\  
  
 *[GUID lingua]*\  
  
 *[GUID fornitore]*\  
  
 `CLSID` = *[GUID classe]*  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
 `Engine`\  
  
 `0` = *[GUID del motore di debug]*  
  
 `1` = *[GUID del motore di debug]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[GUID lingua]*|GUID di una lingua|  
|*[GUID fornitore]*|GUID di un fornitore|  
|*[GUID classe]*|GUID della classe che implementa questo analizzatore di espressioni|  
|*[GUID del motore di debug]*|GUID di un motore di debug utilizzato da questo analizzatore di espressioni|  
  
### <a name="expression-evaluator-extensions"></a>Estensioni dell'analizzatore di espressioni  
 Di seguito sono riportate le metriche dell'estensione dell'analizzatore di espressioni nel registro di sistema. `EEExtensions` nome del tipo di metrica per le estensioni dell'analizzatore di espressioni e corrisponde a *[tipo di metrica]*.  
  
 `EEExtensions`\  
  
 *[GUID estensione]*\  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[GUID estensione]*|GUID di un'estensione dell'analizzatore di espressioni|  
  
### <a name="exceptions"></a>Eccezioni  
 Di seguito sono riportate le metriche delle eccezioni nel registro di sistema. `Exception` nome del tipo di metrica per le eccezioni e corrisponde a *[tipo di metrica]*.  
  
 `Exception`\  
  
 *[GUID del motore di debug]*\  
  
 *[tipi di eccezione]*\  
  
 *eccezione*\  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
 *eccezione*\  
  
 *[metrica] = [valore metrica]*  
  
 *[metrica] = [valore metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[GUID del motore di debug]*|GUID di un motore di debug che supporta le eccezioni.|  
|*[tipi di eccezione]*|Titolo generale per la sottochiave che identifica la classe di eccezioni che è possibile gestire. I nomi tipici sono **eccezioni C++**, **eccezioni Win32**, **eccezioni Common Language Runtime**e **controlli run-time nativi**. Questi nomi vengono usati anche per identificare una particolare classe di eccezione per l'utente.|  
|*eccezione*|Nome di un'eccezione, ad esempio **_com_error** o break di **controllo**. Questi nomi vengono usati anche per identificare un'eccezione specifica all'utente.|  
  
## <a name="requirements"></a>Requisiti  
 Questi file si trovano nella [!INCLUDE[vs_dev10_ext](../../../includes/vs-dev10-ext-md.md)] directory di installazione di SDK (per impostazione predefinita, *[unità]* \programmi\microsoft Visual Studio 2010 SDK \\ ).  
  
 Intestazione: includes\dbgmetric.h  
  
 Libreria: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
