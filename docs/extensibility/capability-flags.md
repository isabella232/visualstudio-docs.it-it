---
title: I flag funzionalità | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 958cbc17c843ba4d23ac83b928f7b517ada93080
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922127"
---
# <a name="capability-flags"></a>Flag funzionalità
Il SCC_CAP_*xxx* flag sono flag di bit utilizzato per indicare le funzionalità di un plug-in del controllo del codice sorgente. Il SCC_EXCAP_*xxx* flag sono incrementali flag che indicano le funzionalità estese e risolvibili in valori integer.  
  
|Codice di funzionalità|Value|Descrizione|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Supporta il [SccRemove](../extensibility/sccremove-function.md) e comando.|  
|`SCC_CAP_RENAME`|0x00000002L|Supporta il [SccRename](../extensibility/sccrename-function.md) e comando.|  
|`SCC_CAP_DIFF`|0x00000004L|Supporta il [SccDiff](../extensibility/sccdiff-function.md) e comando.|  
|`SCC_CAP_HISTORY`|0x00000008L|Supporta il [SccHistory](../extensibility/scchistory-function.md) e comando.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Supporta il [SccProperties](../extensibility/sccproperties-function.md) e comando.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Supporta il [SccRunScc](../extensibility/sccrunscc-function.md) e comando.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Supporta il [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e comando.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Supporta il [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e comando.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Supporta il [SccGetEvents](../extensibility/sccgetevents-function.md) e comando.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Supporta il [SccGetProjPath](../extensibility/sccgetprojpath-function.md) e comando.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Supporta il [SccAddFromScc](../extensibility/sccaddfromscc-function.md) e comando.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Supporta un commento durante l'estrazione.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Supporta un commento all'archiviazione.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Supporta un commento su Aggiungi.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Supporta un commento su Rimuovi.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Scrive testo in una funzione di output fornito dall'IDE.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Supporta l'archiviazione dei file senza i delta.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Supporta più la cronologia dei file.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Supporta il confronto di file tra maiuscole e minuscole.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Supporta file di confronto che ignora gli spazi vuoti.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Supporta la ricerca di file aggiuntivi.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Supporta i commenti su creare progetto.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Supporta diff in tutti gli stati se nel controllo.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Plug-in non supporta un'interfaccia utente per Get, ma potrebbe comunque chiamare IDE [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Plug-in è rientrante e thread-safe. Nella versione 1.0, alcun plug-in sono stati considerati come rientrante e thread-safe. Se questo bit viene impostato un 1.1 plug-in, l'host sia autorizzato ad aprire più progetti in parallelo.|  
  
## <a name="capability-bits-added-in-version-12"></a>Bits funzionalità aggiunte nella versione 1.2  
  
|Codice di funzionalità|Valore|Descrizione|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Supporta il [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Supporta il [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Supporta il [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Supporta il [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Supporta il [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Supporta le estrazioni multiple in un file e il [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Supporta il *Mssccprj. scc* file (soggetto a override o l'utente amministratore) e il [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## <a name="capability-bits-added-in-version-13"></a>Bits funzionalità aggiunte nella versione 1.3  
 Questi flag vengono passati uno alla volta per il [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) funzione per determinare se la funzionalità è supportata.  
  
|Codice funzionalità estesa|Valore|Descrizione|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Supporta il `SCC_CHECKOUT_LOCALVER` opzione per le estrazioni.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Supporta il [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Supporta il [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Supporta la ricerca di directory aggiuntive.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Supporta l'enumerazione delle modifiche al file.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Supporta il [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Supporta il [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Supporta la chiamata SccQueryInfo su più thread.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Supporta la funzione SccRemoveDir.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Può eliminare i file estratti.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Possibile rinominare i file estratti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)