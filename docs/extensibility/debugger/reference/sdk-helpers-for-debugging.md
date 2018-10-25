---
title: Helper SDK per eseguire il debug | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d352e22b95540cfc1901eb214c2d5180b6024f27
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821526"
---
# <a name="sdk-helpers-for-debugging"></a>Helper SDK per il debug
Queste funzioni e le dichiarazioni sono funzioni di supporto globale per l'implementazione del provider di simboli, analizzatori di espressioni e motori di debug in C++.  
  
> [!NOTE]
>  Non esistono gestiti sono versioni di queste funzioni e le dichiarazioni in questo momento.  
  
## <a name="overview"></a>Panoramica  
 Affinché il provider di simboli, analizzatori di espressioni e motori di debug da utilizzare da Visual Studio, è necessario registrarli. Questa operazione viene eseguita tramite l'impostazione di sottochiavi e voci, note anche come impostazione "metriche"." Le funzioni globali seguenti sono progettate per semplificare il processo di aggiornamento di queste metriche. Vedere la sezione sulle posizioni del Registro di sistema per individuare il layout di ogni sottochiave del Registro di sistema che viene aggiornato da queste funzioni.  
  
## <a name="general-metric-functions"></a>Funzioni di metrica generale  
 Queste sono funzioni generali utilizzate dai motori di debug. Specializzato funzioni per gli analizzatori di espressioni e i provider di simboli sono descritti in dettaglio in un secondo momento.  
  
### <a name="getmetric-method"></a>Metodo GetMetric  
 Recupera un valore della metrica dal Registro di sistema.  
  
```cpp  
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
|pszMachine|[in] Nome di un computer remoto probabilmente verrà scritto il cui Registro (`NULL` significa computer locale).|  
|pszType|[in] Uno dei tipi di metriche.|  
|guidSection|[in] GUID di un motore specifico dell'analizzatore di espressioni, eccezione, e così via. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|  
|pszMetric|[in] Per ottenere la metrica. Corrisponde al nome di un valore specifico.|  
|pdwValue|[in] Percorso di archiviazione del valore di metrica. Esistono diverse versioni di GetMetric che può restituire un valore DWORD (come in questo esempio), un oggetto BSTR, un GUID o una matrice di GUID.|  
|pszAltRoot|[in] Una radice del Registro di sistema alternativo da utilizzare. Impostare su `NULL` per usare il valore predefinito.|  
  
### <a name="setmetric-method"></a>Metodo SetMetric  
 Imposta il valore della metrica specificato nel Registro di sistema.  
  
```cpp  
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
|pszType|[in] Uno dei tipi di metriche.|  
|guidSection|[in] GUID di un motore specifico dell'analizzatore di espressioni, eccezione, e così via. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|  
|pszMetric|[in] Per ottenere la metrica. Corrisponde al nome di un valore specifico.|  
|dwValue|[in] Percorso di archiviazione del valore della metrica. Esistono diverse versioni di SetMetric che può archiviare un valore DWORD (in questo esempio), un oggetto BSTR, un GUID o una matrice di GUID.|  
|fUserSpecific|[in] TRUE se la metrica è specifica dell'utente e se deve essere scritto per hive dell'utente anziché hive computer locale.|  
|pszAltRoot|[in] Una radice del Registro di sistema alternativo da utilizzare. Impostare su `NULL` per usare il valore predefinito.|  
  
### <a name="removemetric-method"></a>Metodo RemoveMetric  
 Rimuove la metrica specificata dal Registro di sistema.  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszType|[in] Uno dei tipi di metriche.|  
|guidSection|[in] GUID di un motore specifico dell'analizzatore di espressioni, eccezione, e così via. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|  
|pszMetric|[in] La metrica deve essere rimosso. Corrisponde al nome di un valore specifico.|  
|pszAltRoot|[in] Una radice del Registro di sistema alternativo da utilizzare. Impostare su `NULL` per usare il valore predefinito.|  
  
### <a name="enummetricsections-method"></a>Metodo EnumMetricSections  
 Enumera le diverse sezioni di metrica nel Registro di sistema.  
  
```cpp  
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
|pszMachine|[in] Nome di un computer remoto probabilmente verrà scritto il cui Registro (`NULL` significa computer locale).|  
|pszType|[in] Uno dei tipi di metriche.|  
|rgguidSections|[in, out] Preallocate matrice di GUID da compilare.|  
|pdwSize|[in] Il numero massimo di GUID che possono essere archiviati nel `rgguidSections` matrice.|  
|pszAltRoot|[in] Una radice del Registro di sistema alternativo da utilizzare. Impostare su `NULL` per usare il valore predefinito.|  
  
## <a name="expression-evaluator-functions"></a>Funzioni dell'analizzatore di espressioni  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetEEMetric|Recupera un valore della metrica dal Registro di sistema.|  
|SetEEMetric|Imposta il valore della metrica specificato nel Registro di sistema.|  
|RemoveEEMetric|Rimuove la metrica specificata dal Registro di sistema.|  
|GetEEMetricFile|Ottiene un nome di file dalla metrica specificata e li carica, restituendo il contenuto del file sotto forma di stringa.|  
  
## <a name="exception-functions"></a>Funzioni di eccezione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetExceptionMetric|Recupera un valore della metrica dal Registro di sistema.|  
|SetExceptionMetric|Imposta il valore della metrica specificato nel Registro di sistema.|  
|RemoveExceptionMetric|Rimuove la metrica specificata dal Registro di sistema.|  
|RemoveAllExceptionMetrics|Rimuove tutte le metriche di eccezione dal Registro di sistema.|  
  
## <a name="symbol-provider-functions"></a>Funzioni di Provider di simboli  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetSPMetric|Recupera un valore della metrica dal Registro di sistema.|  
|SetSPMetric|Imposta il valore della metrica specificato nel Registro di sistema.|  
|RemoveSPMetric|Rimuove la metrica specificata dal Registro di sistema.|  
  
## <a name="enumeration-functions"></a>Funzioni di enumerazione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|EnumMetricSections|Enumera tutte le metriche per un tipo di metrica specificata.|  
|EnumDebugEngine|Enumera i motori di debug registrati.|  
|EnumEEs|Enumera gli analizzatori di espressioni registrati.|  
|EnumExceptionMetrics|Enumera tutte le metriche di eccezione.|  
  
## <a name="metric-definitions"></a>Definizioni delle metriche  
 Queste definizioni utilizzabile per i nomi delle metriche predefiniti. I nomi corrispondono a diverse chiavi del Registro di sistema e i nomi di valore e sono state definite come stringhe wide-char: ad esempio, `extern LPCWSTR metrictypeEngine`.  
  
|Tipi di metriche predefiniti|Descrizione: La chiave di base per...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Tutti le metriche del motore di debug.|  
|metrictypePortSupplier|Tutte le metriche di fornitori di porte.|  
|metrictypeException|Tutte le metriche di eccezione.|  
|metricttypeEEExtension|Tutte le estensioni dell'analizzatore di espressioni.|  
  
|Proprietà del motore di debug|Descrizione|  
|-----------------------------|-----------------|  
|metricAddressBP|Impostare su diverso da zero per indicare il supporto per i punti di interruzione di indirizzo.|  
|metricAlwaysLoadLocal|Impostare su diverso da zero per sempre caricare il motore di debug in locale.|  
|metricLoadInDebuggeeSession|NON UTILIZZATO|  
|metricLoadedByDebuggee|Impostare su diverso da zero per indicare che il motore di debug verrà caricato sempre con o tramite il programma sottoposto a debug.|  
|metricAttach|Impostare su diverso da zero per indicare il supporto per l'allegato a programmi esistenti.|  
|metricCallStackBP|Impostare su diverso da zero per indicare il supporto dei punti di interruzione dello stack di chiamate.|  
|metricConditionalBP|Impostare su diverso da zero per indicare il supporto per l'impostazione di punti di interruzione condizionale.|  
|metricDataBP|Impostare su diverso da zero per indicare il supporto per l'impostazione di punti di interruzione su modifiche dei dati.|  
|metricDisassembly|Impostare su diverso da zero per indicare il supporto per la produzione di un elenco di disassemblaggio.|  
|metricDumpWriting|Impostare su diverso da zero per indicare il supporto per dump la scrittura (il dump di memoria da un dispositivo di output).|  
|metricENC|Impostare su zero per indicare il supporto per la modifica e continuazione. **Nota:** un motore di debug personalizzato non deve mai impostato in questo o deve sempre impostata su 0.|  
|metricExceptions|Impostare su diverso da zero per indicare il supporto per le eccezioni.|  
|metricFunctionBP|Impostare su diverso da zero per indicare il supporto per i punti di interruzione denominati (i punti di interruzione che si interrompono quando viene chiamato un determinato nome di funzione).|  
|metricHitCountBP|Impostare su diverso da zero per indicare il supporto per l'impostazione di punti di interruzione "Colpisci punto" (punti di interruzione che vengono attivati solo dopo che viene raggiunto un determinato numero di volte).|  
|metricJITDebug|Impostare su zero per indicare il supporto per il debug just-in-time (il debugger viene avviato quando si verifica un'eccezione in un processo in esecuzione).|  
|metricMemory|NON UTILIZZATO|  
|metricPortSupplier|Impostare il CLSID del fornitore della porta se implementata.|  
|metricRegisters|NON UTILIZZATO|  
|metricSetNextStatement|Impostare su diverso da zero per indicare il supporto per l'impostazione dell'istruzione successiva (che ignora l'esecuzione di istruzioni intermedi).|  
|metricSuspendThread|Impostare su diverso da zero per indicare il supporto per sospendere l'esecuzione di thread.|  
|metricWarnIfNoSymbols|Impostare su diverso da zero per indicare che l'utente dovrebbe ricevere una notifica se non sono presenti alcun simbolo.|  
|metricProgramProvider|Impostare il CLSID del provider di programma.|  
|metricAlwaysLoadProgramProviderLocal|Impostare questa opzione a diverso da zero per indicare che il provider di programma deve essere sempre caricato in locale.|  
|metricEngineCanWatchProcess|Impostare questa opzione su diversi da zero per indicare che il motore di debug controllerà per elaborare gli eventi anziché il provider di programma.|  
|metricRemoteDebugging|Impostare questa opzione su diversi da zero per indicare il supporto per il debug remoto.|  
|metricEncUseNativeBuilder|Impostare questa opzione a diverso da zero per indicare che la modifica e continuazione Manager deve usare encbuild.dll del motore di debug per la compilazione per modifica e continuazione. **Nota:** un motore di debug personalizzato non deve mai impostato in questo o deve sempre impostata su 0.|  
|metricLoadUnderWOW64|Impostare questa opzione su diversi da zero per indicare che il motore di debug deve essere caricato nel processo oggetto del debug in WOW durante il debug di un processo a 64 bit. in caso contrario, il motore di debug verrà caricato nel processo di Visual Studio (che è in esecuzione in WOW64).|  
|metricLoadProgramProviderUnderWOW64|Impostare questa opzione su diversi da zero per indicare che il provider di programma deve essere caricato nel processo oggetto del debug durante il debug di un processo a 64 bit in WOW; in caso contrario, verrà caricato nel processo di Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Impostare questa opzione su diversi da zero per indicare che il processo deve essere interrotta se attraverso i limiti di codice gestito e viene generata un'eccezione non gestita.|  
|metricAutoSelectPriority|Impostare una priorità per la selezione automatica del motore di debug (superiore valori è uguale a priorità più alta).|  
|metricAutoSelectIncompatibleList|Chiave del Registro di sistema che contiene le voci che specificano i GUID per i motori di debug da ignorare nella selezione automatica. Queste voci sono un numero (0, 1, 2 e così via) con un GUID espresso sotto forma di stringa.|  
|metricIncompatibleList|Chiave del Registro di sistema che contiene le voci che specificano i GUID per i motori di debug che non sono compatibili con il motore di debug.|  
|metricDisableJITOptimization|Impostare questa opzione su diversi da zero per indicare che le ottimizzazioni di just-in-time (per il codice gestito) devono essere disabilitate durante il debug.|  
  
|Proprietà dell'analizzatore di espressioni|Descrizione|  
|-------------------------------------|-----------------|  
|metricEngine|Contiene il numero di motori di debug che supportano l'analizzatore di espressioni specificato.|  
|metricPreloadModules|Impostare questa opzione su diversi da zero per indicare che è necessario precaricare i moduli all'avvio di un analizzatore di espressioni in un programma.|  
|metricThisObjectName|Impostare il nome dell'oggetto "this".|  
  
|Proprietà di estensione dell'analizzatore di espressioni|Descrizione|  
| - |-----------------|  
|metricExtensionDll|Nome della dll che supporta questa estensione.|  
|metricExtensionRegistersSupported|Elenco dei registri è supportato.|  
|metricExtensionRegistersEntryPoint|Punto di ingresso per l'accesso ai registri.|  
|metricExtensionTypesSupported|Elenco dei tipi supportati.|  
|metricExtensionTypesEntryPoint|Punto di ingresso per accedere a tipi.|  
  
|Proprietà di fornitori di porte|Descrizione|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Il CLSID del selettore porta (una finestra di dialogo l'utente può usare per selezionare le porte e aggiungere le porte da utilizzare per il debug).|  
|metricDisallowUserEnteredPorts|Diverso da zero se non è possibile aggiungere le porte immesso dall'utente per il fornitore della porta (in questo modo la finestra di dialogo di selezione porta essenzialmente di sola lettura).|  
|metricPidBase|L'ID di processo di base usata dal fornitore della porta quando si assegnano gli ID dei processi.|  
  
|Tipi predefiniti SP Store|Descrizione|  
|-------------------------------|-----------------|  
|storetypeFile|I simboli vengono archiviati in un file separato.|  
|storetypeMetadata|I simboli vengono archiviati come metadati in un assembly.|  
  
|Varie proprietà|Descrizione|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Impostare questa opzione su diversi da zero per visualizzare codice nonuser.|  
|metricJustMyCodeStepping|Impostare questa opzione su diversi da zero per indicare che l'esecuzione di istruzioni può trovarsi solo nel codice utente.|  
|metricCLSID|CLSID di un oggetto di un tipo specifico di metrica.|  
|MetricName|Nome descrittivo per un oggetto di un tipo specifico di metrica.|  
|metricLanguage|Nome della lingua.|  
  
## <a name="registry-locations"></a>Percorsi del Registro di sistema  
 Le metriche vengono letti da e scritte nel Registro di sistema, in particolare il `VisualStudio` sottochiave.  
  
> [!NOTE]
>  La maggior parte dei casi, verranno scritte le metriche per la chiave HKEY_LOCAL_MACHINE. Tuttavia, talvolta HKEY_CURRENT_USER sarà la chiave di destinazione. Dbgmetric.lib gestisce entrambe le chiavi. Quando si recupera una metrica, la ricerca HKEY_CURRENT_USER per primo, quindi HKEY_LOCAL_MACHINE. Quando si sta impostando una metrica, un parametro specifica la chiave di primo livello da usare.  
  
 *[chiave del Registro di sistema]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[root versione]*\  
  
 *[metrica root]*\  
  
 *[tipo di metrica]*\  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[chiave del Registro di sistema]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|  
|*[root versione]*|La versione di Visual Studio (ad esempio, `7.0`, `7.1`, o `8.0`). Tuttavia, questa radice può essere modificata anche usando il **/rootsuffix** passa a **devenv.exe**. Per VSIP, questo modificatore viene in genere **Exp**, pertanto la radice di versione potrebbe essere, ad esempio, 8.0Exp.|  
|*[metrica root]*|Si tratta `AD7Metrics` o `AD7Metrics(Debug)`, a seconda del fatto che viene utilizzata la versione di debug di dbgmetric.lib. **Nota:** dbgmetric.lib viene usato, o meno questa convenzione di denominazione debba essere rispettata nel caso di differenze tra debug e rilascio versioni che devono essere riflessa nel Registro di sistema.|  
|*[tipo di metrica]*|Il tipo di metrica da scrivere: `Engine`, `ExpressionEvaluator`, `SymbolProvider`e così via. Questi sono tutti definiti come dbgmetric.h come `metricTypeXXXX`, dove `XXXX` è il nome del tipo specifico.|  
|*[metrica]*|Il nome di una voce a cui assegnare un valore per impostare la metrica. L'organizzazione effettivo delle metriche dipende dal tipo delle metriche.|  
|*[valore della metrica]*|Il valore assegnato alla metrica. Il tipo che di valore deve essere (stringa), numero, e così via dipende la metrica.|  
  
> [!NOTE]
>  Tutti i GUID vengono archiviati nel formato `{GUID}`. Ad esempio `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Motori di debug  
 Di seguito è l'organizzazione delle metriche di motori di debug nel Registro di sistema. `Engine` è il nome del tipo di metrica per un motore di debug e corrisponde a *[tipo di metrica]* nel sottoalbero del Registro di sistema precedente.  
  
 `Engine`\  
  
 *[motore guid]*\  
  
 `CLSID` = *[guid classe]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 `PortSupplier`\  
  
 `0` = *[guid fornitore porte]*  
  
 `1` = *[guid fornitore porte]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[motore guid]*|Il GUID del motore di debug.|  
|*[guid classe]*|Il GUID della classe che implementa questo motore di debug.|  
|*[guid fornitore porte]*|Il GUID del fornitore della porta, se presente. Molti motori di debug usano il fornitore della porta predefinita e pertanto non si specificano i propri fornitori. In questo caso, la sottochiave `PortSupplier` sarà presente.|  
  
### <a name="port-suppliers"></a>Fornitori di porte  
 Di seguito è l'organizzazione delle metriche supplier porta nel Registro di sistema. `PortSupplier` è il nome del tipo di metrica per un fornitore di porte e corrisponde a *[tipo di metrica]*.  
  
 `PortSupplier`\  
  
 *[guid fornitore porte]*\  
  
 `CLSID` = *[guid classe]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid fornitore porte]*|Il GUID del fornitore della porta|  
|*[guid classe]*|Il GUID della classe che implementa il fornitore della porta|  
  
### <a name="symbol-providers"></a>Provider di simboli  
 Di seguito è l'organizzazione delle metriche supplier simbolo nel Registro di sistema. `SymbolProvider` è il nome del tipo di metrica per il provider di simboli e corrisponde a *[tipo di metrica]*.  
  
 `SymbolProvider`\  
  
 *[guid provider simbolo]*\  
  
 `file`\  
  
 `CLSID` = *[guid classe]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 `metadata`\  
  
 `CLSID` = *[guid classe]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid provider simbolo]*|Il GUID del provider di simboli|  
|*[guid classe]*|Il GUID della classe che implementa questo provider di simboli|  
  
### <a name="expression-evaluators"></a>Analizzatori di espressioni  
 Di seguito è l'organizzazione delle metriche dell'analizzatore di espressioni nel Registro di sistema. `ExpressionEvaluator` è il nome del tipo di metrica per l'analizzatore di espressioni e corrisponde a *[tipo di metrica]*.  
  
> [!NOTE]
>  Il tipo di metrica `ExpressionEvaluator` non è definito in dbgmetric.h, perché si presuppone che tutte le modifiche delle metriche per gli analizzatori di espressioni passeranno attraverso le funzioni di metrica dell'analizzatore di espressioni espressione appropriata (il layout del `ExpressionEvaluator` sottochiave è leggermente complicata, in modo che i dettagli sono nascosti all'interno di dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[guid language]*\  
  
 *[guid fornitore]*\  
  
 `CLSID` = *[guid classe]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 `Engine`\  
  
 `0` = *[guid del motore di debug]*  
  
 `1` = *[guid del motore di debug]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid language]*|Il GUID di una lingua|  
|*[guid fornitore]*|Il GUID del fornitore|  
|*[guid classe]*|Il GUID della classe che implementa questo analizzatore di espressioni|  
|*[guid del motore di debug]*|Il GUID del motore di debug questo analizzatore di espressioni funziona con|  
  
### <a name="expression-evaluator-extensions"></a>Estensioni dell'analizzatore di espressioni  
 Di seguito è l'organizzazione delle metriche di estensione dell'analizzatore di espressioni nel Registro di sistema. `EEExtensions` è il nome del tipo di metrica per l'espressione di estensioni dell'analizzatore di espressioni e corrisponde a *[tipo di metrica]*.  
  
 `EEExtensions`\  
  
 *[estensione guid]*\  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[estensione guid]*|Il GUID di un'estensione dell'analizzatore di espressioni|  
  
### <a name="exceptions"></a>Eccezioni  
 Di seguito è l'organizzazione delle metriche delle eccezioni nel Registro di sistema. `Exception` è il nome del tipo di metrica relativi alle eccezioni e corrisponde a *[tipo di metrica]*.  
  
 `Exception`\  
  
 *[guid del motore di debug]*\  
  
 *[tipi di eccezione]*\  
  
 *[eccezione]*\  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[eccezione]*\  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid del motore di debug]*|Il GUID del motore di debug supporta le eccezioni.|  
|*[tipi di eccezione]*|Un titolo generale per la sottochiave che identifica la classe di eccezioni che possono essere gestiti. Sono nomi tipici **eccezioni C++**, **eccezioni Win32**, **eccezioni Common Language Runtime**, e **dei controlli runtime nativi**. Questi nomi vengono usati anche per identificare una classe particolare di eccezione per l'utente.|  
|*[eccezione]*|Un nome per un'eccezione: ad esempio, **com_error** oppure **CTRL + INTERR**. Questi nomi vengono usati anche per identificare una particolare eccezione all'utente.|  
  
## <a name="requirements"></a>Requisiti  
 Questi file si trovano nel [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] directory di installazione SDK (per impostazione predefinita *[unità]* \Programmi\Microsoft Visual Studio 2010 SDK\\).  
  
 Intestazione: includes\dbgmetric.h  
  
 Libreria: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)