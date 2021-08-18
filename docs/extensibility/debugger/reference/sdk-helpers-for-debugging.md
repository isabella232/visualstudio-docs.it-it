---
title: Helper SDK per il debug | Microsoft Docs
description: Informazioni sulle funzioni e le dichiarazioni che sono funzioni helper globali per l'implementazione di motori di debug, analizzatori di espressioni e provider di simboli in C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fd85921256d8212a1d02d2d24277ff2ed71dde97
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103065"
---
# <a name="sdk-helpers-for-debugging"></a>Helper SDK per il debug
Queste funzioni e dichiarazioni sono funzioni helper globali per l'implementazione di motori di debug, analizzatori di espressioni e provider di simboli in C++.

> [!NOTE]
> Al momento non sono disponibili versioni gestite di queste funzioni e dichiarazioni.

## <a name="overview"></a>Panoramica
 Per poter usare i motori di debug, gli analizzatori di espressioni e i provider di simboli Visual Studio, è necessario registrarli. Questa operazione viene eseguita impostando le sottochiavi e le voci del Registro di sistema, note anche come "metriche di impostazione". Le funzioni globali seguenti sono progettate per semplificare il processo di aggiornamento di queste metriche. Per informazioni sul layout di ogni sottochiave del Registro di sistema aggiornata da queste funzioni, vedere la sezione Percorsi del Registro di sistema.

## <a name="general-metric-functions"></a>Funzioni di metrica generali
 Si tratta di funzioni generali usate dai motori di debug. Le funzioni specializzate per gli analizzatori di espressioni e i provider di simboli vengono fornite in dettaglio più avanti.

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
|pszMachine|[in] Nome di un computer remoto il cui registro verrà scritto ( `NULL` significa computer locale).|
|pszType|[in] Uno dei tipi di metrica.|
|guidSection|[in] GUID di un motore, un analizzatore, un'eccezione e così via specifici. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|
|pszMetric|[in] Metrica da ottenere. Corrisponde a un nome di valore specifico.|
|pdwValue|[in] Posizione di archiviazione del valore dalla metrica. Esistono diverse versioni di GetMetric che possono restituire un valore DWORD (come in questo esempio), un BSTR, un GUID o una matrice di GUID.|
|pszAltRoot|[in] Una radice alternativa del Registro di sistema da usare. Impostare su `NULL` per usare il valore predefinito.|

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
|pszType|[in] Uno dei tipi di metrica.|
|guidSection|[in] GUID di un motore, un analizzatore, un'eccezione e così via specifici. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|
|pszMetric|[in] Metrica da ottenere. Corrisponde a un nome di valore specifico.|
|dwValue|[in] Posizione di archiviazione del valore nella metrica. Esistono diverse versioni di SetMetric che possono archiviare un valore DWORD (in questo esempio), un BSTR, un GUID o una matrice di GUID.|
|fUserSpecific|[in] TRUE se la metrica è specifica dell'utente e deve essere scritta nell'hive dell'utente anziché nell'hive del computer locale.|
|pszAltRoot|[in] Una radice alternativa del Registro di sistema da usare. Impostare su `NULL` per usare il valore predefinito.|

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
|pszType|[in] Uno dei tipi di metrica.|
|guidSection|[in] GUID di un motore, un analizzatore, un'eccezione e così via specifici. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|
|pszMetric|[in] Metrica da rimuovere. Corrisponde a un nome di valore specifico.|
|pszAltRoot|[in] Una radice alternativa del Registro di sistema da usare. Impostare su `NULL` per usare il valore predefinito.|

### <a name="enummetricsections-method"></a>Metodo EnumMetricSections
 Enumera le varie sezioni delle metriche nel Registro di sistema.

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
|pszMachine|[in] Nome di un computer remoto il cui registro verrà scritto ( `NULL` significa computer locale).|
|pszType|[in] Uno dei tipi di metrica.|
|rgguidSections|[in, out] Matrice preallocata di GUID da riempire.|
|pdwSize|[in] Numero massimo di GUID che possono essere archiviati nella `rgguidSections` matrice.|
|pszAltRoot|[in] Una radice alternativa del Registro di sistema da usare. Impostare su `NULL` per usare il valore predefinito.|

## <a name="expression-evaluator-functions"></a>Funzioni dell'analizzatore di espressioni

|Funzione|Descrizione|
|--------------|-----------------|
|GetEEMetric|Recupera un valore della metrica dal Registro di sistema.|
|SetEEMetric|Imposta il valore della metrica specificato nel Registro di sistema.|
|RemoveEEMetric|Rimuove la metrica specificata dal Registro di sistema.|
|GetEEMetricFile|Ottiene un nome file dalla metrica specificata e lo carica, restituisce il contenuto del file come stringa.|

## <a name="exception-functions"></a>Funzioni di eccezione

|Funzione|Descrizione|
|--------------|-----------------|
|GetExceptionMetric|Recupera un valore della metrica dal Registro di sistema.|
|SetExceptionMetric|Imposta il valore della metrica specificato nel Registro di sistema.|
|RemoveExceptionMetric|Rimuove la metrica specificata dal Registro di sistema.|
|RemoveAllExceptionMetrics|Rimuove tutte le metriche delle eccezioni dal Registro di sistema.|

## <a name="symbol-provider-functions"></a>Funzioni del provider di simboli

|Funzione|Descrizione|
|--------------|-----------------|
|GetSPMetric|Recupera un valore della metrica dal Registro di sistema.|
|SetSPMetric|Imposta il valore della metrica specificato nel Registro di sistema.|
|RemoveSPMetric|Rimuove la metrica specificata dal Registro di sistema.|

## <a name="enumeration-functions"></a>Funzioni di enumerazione

|Funzione|Descrizione|
|--------------|-----------------|
|EnumMetricSections|Enumera tutte le metriche per un tipo di metrica specificato.|
|EnumDebugEngine|Enumera i motori di debug registrati.|
|EnumEEs|Enumera gli analizzatori di espressioni registrati.|
|EnumExceptionMetrics|Enumera tutte le metriche delle eccezioni.|

## <a name="metric-definitions"></a>Definizioni delle metriche
 Queste definizioni possono essere usate per i nomi delle metriche predefiniti. I nomi corrispondono a varie chiavi del Registro di sistema e ai nomi dei valori e sono tutti definiti come stringhe di caratteri wide, ad esempio `extern LPCWSTR metrictypeEngine` .

|Tipi di metrica predefiniti|Descrizione: chiave di base per.|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Tutte le metriche del motore di debug.|
|metrictypePortSupplier|Tutte le metriche dei fornitori di porte.|
|metrictypeException|Tutte le metriche delle eccezioni.|
|metricttypeEEExtension|Tutte le estensioni dell'analizzatore di espressioni.|

|Proprietà del motore di debug|Descrizione|
|-----------------------------|-----------------|
|metricAddressBP|Impostare su un valore diverso da zero per indicare il supporto per i punti di interruzione degli indirizzi.|
|metricAlwaysLoadLocal|Impostare su un valore diverso da zero per caricare sempre il motore di debug in locale.|
|metricLoadInDebuggeeSession|NON USATO|
|metricLoadedByDebuggee|Impostare su un valore diverso da zero per indicare che il motore di debug verrà sempre caricato con o dal programma in fase di debug.|
|metricaAttacco|Impostare su un valore diverso da zero per indicare il supporto per l'allegato ai programmi esistenti.|
|metricaCallStackBP|Impostare su un valore diverso da zero per indicare il supporto per i punti di interruzione dello stack di chiamate.|
|metricConditionalBP|Impostare su un valore diverso da zero per indicare il supporto per l'impostazione dei punti di interruzione condizionali.|
|metricaDataBP|Impostare su un valore diverso da zero per indicare il supporto per l'impostazione di punti di interruzione sulle modifiche nei dati.|
|metricaDisassembly|Impostare su un valore diverso da zero per indicare il supporto per la produzione di un elenco di disassembly.|
|metricaDumpWriting|Impostare su un valore diverso da zero per indicare il supporto per la scrittura di dump (dump della memoria in un dispositivo di output).|
|metricaENC|Impostare su un valore diverso da zero per indicare il supporto per Modifica e continuazione. **Nota:**  Un motore di debug personalizzato non deve mai impostarlo o deve sempre impostarlo su 0.|
|metricExceptions|Impostare su un valore diverso da zero per indicare il supporto per le eccezioni.|
|metricFunctionBP|Impostare su un valore diverso da zero per indicare il supporto per i punti di interruzione denominati (punti di interruzione quando viene chiamato un determinato nome di funzione).|
|metricHitCountBP|Impostare su un valore diverso da zero per indicare il supporto per l'impostazione di punti di interruzione "punto di accesso" (punti di interruzione attivati solo dopo essere stati raggiunto un determinato numero di volte).|
|metricaJITDebug|Impostare su un valore diverso da zero per indicare il supporto per il debug JIT (il debugger viene avviato quando si verifica un'eccezione in un processo in esecuzione).|
|metricaMemory|NON USATO|
|metricaPortSupplier|Impostare questo valore sul CLSID del fornitore di porte, se ne viene implementato uno.|
|metricRegisters|NON USATO|
|metricSetNextStatement|Impostare su un valore diverso da zero per indicare il supporto per l'impostazione dell'istruzione successiva , che ignora l'esecuzione di istruzioni intermedie.|
|metricSuspendThread|Impostare su un valore diverso da zero per indicare il supporto per la sospensione dell'esecuzione del thread.|
|metricaWarnIfNoSymbols|Impostare su un valore diverso da zero per indicare che l'utente deve ricevere una notifica se non sono presenti simboli.|
|metricProgramProvider|Impostare questo valore sul CLSID del provider di programmi.|
|metricAlwaysLoadProgramProviderLocal|Impostare questo valore su un valore diverso da zero per indicare che il provider di programmi deve essere sempre caricato in locale.|
|MetricaEngineCanWatchProcess|Impostare questo valore su un valore diverso da zero per indicare che il motore di debug guarderà gli eventi di elaborazione anziché il provider di programmi.|
|metricaRemoteDebugging|Impostare questo valore su un valore diverso da zero per indicare il supporto per il debug remoto.|
|metricEncUseNativeBuilder|Impostare questa opzione su un valore diverso da zero per indicare che Gestione modifiche e continuazione deve usare il encbuild.dll del motore di debug per la compilazione per Modifica e continuazione. **Nota:**  Un motore di debug personalizzato non deve mai impostarlo o deve sempre impostarlo su 0.|
|metricaLoadUnderWOW64|Impostare questa proprietà su un valore diverso da zero per indicare che il motore di debug deve essere caricato nel processo dell'oggetto del debug in WOW durante il debug di un processo a 64 bit. In caso contrario, il motore di debug verrà caricato nel Visual Studio processo (in esecuzione in WOW64).|
|metricLoadProgramProviderUnderWOW64|Impostare questa proprietà su un valore diverso da zero per indicare che il provider di programmi deve essere caricato nel processo dell'oggetto del debug durante il debug di un processo a 64 bit in WOW. In caso contrario, verrà caricato nel Visual Studio processo.|
|MetricaStopOnExceptionCrossingManagedBoundary|Impostare questa proprietà su un valore diverso da zero per indicare che il processo deve essere interrotta se viene generata un'eccezione non gestita attraverso i limiti del codice gestito/non gestito.|
|metricaAutoSelectPriority|Impostare questa opzione su una priorità per la selezione automatica del motore di debug (i valori più alti sono uguali alla priorità più alta).|
|metricaAutoSelectIncompatibleList|Chiave del Registro di sistema contenente voci che specificano GUID per i motori di debug da ignorare nella selezione automatica. Queste voci sono un numero (0, 1, 2 e così via) con un GUID espresso come stringa.|
|metricIncompatibleList|Chiave del Registro di sistema contenente voci che specificano GUID per motori di debug incompatibili con questo motore di debug.|
|metricaDisableJITOptimization|Impostare questo valore su un valore diverso da zero per indicare che le ottimizzazioni JIT (per il codice gestito) devono essere disabilitate durante il debug.|

|Proprietà dell'analizzatore di espressioni|Descrizione|
|-------------------------------------|-----------------|
|metricEngine|Contiene il numero di motori di debug che supportano l'analizzatore di espressioni specificato.|
|metricPreloadModules|Impostare questo valore su un valore diverso da zero per indicare che i moduli devono essere precaricati quando un analizzatore di espressioni viene avviato su un programma.|
|metricThisObjectName|Impostare questo valore sul nome dell'oggetto "this".|

|Proprietà dell'estensione dell'analizzatore di espressioni|Descrizione|
| - |-----------------|
|metricExtensionDll|Nome della DLL che supporta questa estensione.|
|MetricaExtensionRegistersSupported|Elenco di registri supportati.|
|MetricaExtensionRegistersEntryPoint|Punto di ingresso per l'accesso ai registri.|
|MetricaExtensionTypesSupported|Elenco dei tipi supportati.|
|metricExtensionTypesEntryPoint|Punto di ingresso per l'accesso ai tipi.|

|Proprietà fornitore porta|Descrizione|
|------------------------------|-----------------|
|metricPortPickerCLSID|CLSID del selettore di porte (una finestra di dialogo che l'utente può usare per selezionare le porte e aggiungere le porte da usare per il debug).|
|MetricaDisallowUserEnteredPorts|Diverso da zero se le porte immesse dall'utente non possono essere aggiunte al fornitore della porta. In questo modo la finestra di dialogo selezione porta è essenzialmente di sola lettura.|
|MetricaPidBase|ID del processo di base usato dal fornitore della porta durante l'allocazione degli ID di processo.|

|Tipi di archivio SP predefiniti|Descrizione|
|-------------------------------|-----------------|
|storetypeFile|I simboli vengono archiviati in un file separato.|
|storetypeMetadata|I simboli vengono archiviati come metadati in un assembly.|

|Proprietà varie|Descrizione|
|------------------------------|-----------------|
|MetricaShowNonUserCode|Impostare questo valore su un valore diverso da zero per visualizzare il codice non utente.|
|metricaJustMyCodeStepping|Impostare questo valore su un valore diverso da zero per indicare che l'esecuzione di istruzioni può verificarsi solo nel codice utente.|
|metricCLSID|CLSID per un oggetto di un tipo di metrica specifico.|
|metricName|Nome descrittivo per un oggetto di un tipo di metrica specifico.|
|metricLanguage|Nome della lingua.|

## <a name="registry-locations"></a>Percorsi del Registro di sistema
 Le metriche vengono lette e scritte nel Registro di sistema, in particolare nella `VisualStudio` sottochiave .

> [!NOTE]
> Nella maggior parte dei casi, le metriche verranno scritte nella HKEY_LOCAL_MACHINE chiave. Tuttavia, a volte HKEY_CURRENT_USER sarà la chiave di destinazione. Dbgmetric.lib gestisce entrambe le chiavi. Quando si riceve una metrica, cerca prima HKEY_CURRENT_USER e quindi HKEY_LOCAL_MACHINE. Quando si imposta una metrica, un parametro specifica la chiave di primo livello da usare.

 *[chiave del Registro di sistema]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[radice della versione]*\

 *[radice metrica]*\

 *[Tipo di metrica]*\

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

|Segnaposto|Descrizione|
|-----------------|-----------------|
|*[chiave del Registro di sistema]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|
|*[radice della versione]*|La versione di Visual Studio (ad esempio, `7.0` `7.1` , o `8.0` ). Tuttavia, questa radice può essere modificata anche usando l'opzione **/rootsuffix** **per** devenv.exe. Per VSIP, questo modificatore è in **genere Exp,** quindi la radice della versione sarebbe, ad esempio, 8.0Exp.|
|*[radice metrica]*|È o `AD7Metrics` `AD7Metrics(Debug)` , a seconda che sia utilizzata la versione di debug di dbgmetric.lib. **Nota:**  Se si usa o meno dbgmetric.lib, questa convenzione di denominazione deve essere rispettata in caso di differenze tra le versioni di debug e di versione che devono essere riflesse nel Registro di sistema.|
|*[Tipo di metrica]*|Tipo di metrica da scrivere: `Engine` , , e così `ExpressionEvaluator` `SymbolProvider` via. Queste sono tutte definite come in dbgmetric.h come `metricTypeXXXX` , dove è il nome del tipo `XXXX` specifico.|
|*[metrica]*|Nome di una voce a cui assegnare un valore per impostare la metrica. L'organizzazione effettiva delle metriche dipende dal tipo di metrica.|
|*[Valore metrica]*|Valore assegnato alla metrica. Il tipo che il valore deve avere (stringa, numero e così via) dipende dalla metrica.|

> [!NOTE]
> Tutti i GUID vengono archiviati nel formato `{GUID}` . Ad esempio, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Motori di debug
 Di seguito è riportata l'organizzazione delle metriche dei motori di debug nel Registro di sistema. `Engine` è il nome del tipo di metrica per un motore di debug e corrisponde a *[tipo* di metrica] nel sottoalbero del Registro di sistema precedente.

 `Engine`\

 *[guid motore]*\

 `CLSID` = *[class guid]*

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

 `PortSupplier`\

 `0` = *[port supplier guid]*

 `1` = *[port supplier guid]*

|Segnaposto|Descrizione|
|-----------------|-----------------|
|*[guid motore]*|GUID del motore di debug.|
|*[class guid]*|GUID della classe che implementa questo motore di debug.|
|*[port supplier guid]*|GUID del fornitore della porta, se presente. Molti motori di debug usano il fornitore di porte predefinito e pertanto non specificano il proprio fornitore. In questo caso, la sottochiave `PortSupplier` sarà assente.|

### <a name="port-suppliers"></a>Fornitori di porte
 Di seguito è riportata l'organizzazione delle metriche dei fornitori di porte nel Registro di sistema. `PortSupplier` è il nome del tipo di metrica per un fornitore di porte e corrisponde a *[tipo di metrica]*.

 `PortSupplier`\

 *[port supplier guid]*\

 `CLSID` = *[class guid]*

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

|Segnaposto|Descrizione|
|-----------------|-----------------|
|*[port supplier guid]*|GUID del fornitore della porta|
|*[class guid]*|GUID della classe che implementa questo fornitore di porte|

### <a name="symbol-providers"></a>Provider di simboli
 Di seguito è riportata l'organizzazione delle metriche dei fornitori di simboli nel Registro di sistema. `SymbolProvider` è il nome del tipo di metrica per il provider di simboli e corrisponde *a [tipo di metrica]*.

 `SymbolProvider`\

 *[guid del provider di simboli]*\

 `file`\

 `CLSID` = *[class guid]*

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

 `metadata`\

 `CLSID` = *[class guid]*

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

|Segnaposto|Descrizione|
|-----------------|-----------------|
|*[guid del provider di simboli]*|GUID del provider di simboli|
|*[class guid]*|GUID della classe che implementa questo provider di simboli|

### <a name="expression-evaluators"></a>Analizzatori di espressioni
 Di seguito è riportata l'organizzazione delle metriche dell'analizzatore di espressioni nel Registro di sistema. `ExpressionEvaluator` è il nome del tipo di metrica per l'analizzatore di espressioni e corrisponde *a [tipo di metrica]*.

> [!NOTE]
> Il tipo di metrica per non è definito in dbgmetric.h, poiché si presuppone che tutte le modifiche alle metriche per gli analizzatori di espressioni verranno gestite tramite le funzioni della metrica dell'analizzatore di espressioni appropriate (il layout della sottochiave è piuttosto complesso, quindi i dettagli sono nascosti all'interno `ExpressionEvaluator` `ExpressionEvaluator` di dbgmetric.lib).

 `ExpressionEvaluator`\

 *[guid del linguaggio]*\

 *[guid del fornitore]*\

 `CLSID` = *[class guid]*

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

 `Engine`\

 `0` = *[guid motore di debug]*

 `1` = *[guid motore di debug]*

|Segnaposto|Descrizione|
|-----------------|-----------------|
|*[guid del linguaggio]*|GUID di una lingua|
|*[guid del fornitore]*|GUID di un fornitore|
|*[class guid]*|GUID della classe che implementa questo analizzatore di espressioni|
|*[guid motore di debug]*|GUID di un motore di debug con cui funziona l'analizzatore di espressioni|

### <a name="expression-evaluator-extensions"></a>Estensioni dell'analizzatore di espressioni
 Di seguito è riportata l'organizzazione delle metriche dell'estensione dell'analizzatore di espressioni nel Registro di sistema. `EEExtensions` è il nome del tipo di metrica per le estensioni dell'analizzatore di espressioni e corrisponde *a [tipo di metrica]*.

 `EEExtensions`\

 *[guid estensione]*\

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

|Segnaposto|Descrizione|
|-----------------|-----------------|
|*[guid estensione]*|GUID di un'estensione dell'analizzatore di espressioni|

### <a name="exceptions"></a>Eccezioni
 Di seguito è riportata l'organizzazione delle metriche delle eccezioni nel Registro di sistema. `Exception` è il nome del tipo di metrica per le eccezioni e corrisponde *a [tipo di metrica]*.

 `Exception`\

 *[guid motore di debug]*\

 *[tipi di eccezione]*\

 *[eccezione]*\

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

 *[eccezione]*\

 *[metrica] = [valore metrica]*

 *[metrica] = [valore metrica]*

|Segnaposto|Descrizione|
|-----------------|-----------------|
|*[guid motore di debug]*|GUID di un motore di debug che supporta le eccezioni.|
|*[tipi di eccezione]*|Titolo generale per la sottochiave che identifica la classe di eccezioni che possono essere gestite. I nomi tipici **sono Eccezioni C++,** **Eccezioni Win32,** Eccezioni Common **Language Runtime** e Controlli Run-Time **native**. Questi nomi vengono usati anche per identificare una particolare classe di eccezione per l'utente.|
|*[eccezione]*|Nome per un'eccezione: ad **esempio,** _com_error **o Ctrl-Break**. Questi nomi vengono usati anche per identificare una particolare eccezione per l'utente.|

## <a name="requirements"></a>Requisiti
 Questi file si trovano nella directory di installazione [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] dell'SDK (per impostazione predefinita, *[unità]* \Programmi\Microsoft Visual Studio 2010 SDK \\ ).

 Intestazione: includes\dbgmetric.h

 Libreria: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Vedi anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
