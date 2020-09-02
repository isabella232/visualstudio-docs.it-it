---
title: Flag funzionalità | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739863"
---
# <a name="capability-flags"></a>Flag funzionalità
I flag di SCC_CAP_*xxx* sono flag di bit utilizzati per indicare le funzionalità di un plug-in del controllo del codice sorgente. I flag SCC_EXCAP_*xxx* sono flag incrementali che indicano le funzionalità estese e vengono risolti in valori integer.

|Codice funzionalità|Valore|Descrizione|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Supporta [SccRemove](../extensibility/sccremove-function.md) e Command.|
|`SCC_CAP_RENAME`|0x00000002L|Supporta [SccRename](../extensibility/sccrename-function.md) e Command.|
|`SCC_CAP_DIFF`|0x00000004L|Supporta [SccDiff](../extensibility/sccdiff-function.md) e Command.|
|`SCC_CAP_HISTORY`|0x00000008L|Supporta [SccHistory](../extensibility/scchistory-function.md) e Command.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Supporta [SccProperties](../extensibility/sccproperties-function.md) e Command.|
|`SCC_CAP_RUNSCC`|0x00000020L|Supporta [SccRunScc](../extensibility/sccrunscc-function.md) e Command.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Supporta [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e Command.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Supporta [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e Command.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Supporta [SccGetEvents](../extensibility/sccgetevents-function.md) e Command.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Supporta [SccGetProjPath](../extensibility/sccgetprojpath-function.md) e Command.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Supporta [SccAddFromScc](../extensibility/sccaddfromscc-function.md) e Command.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Supporta un commento sull'estrazione.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Supporta un commento sull'archiviazione.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Supporta un commento su Aggiungi.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Supporta un commento su Remove.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Scrive il testo in una funzione di output fornita dall'IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Supporta l'archiviazione di file senza Delta.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Supporta più cronologia file.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Supporta il confronto di file senza distinzione tra maiuscole e minuscole.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Supporta il confronto di file che ignora gli spazi vuoti.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Supporta la ricerca di file aggiuntivi.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Supporta i commenti su Crea progetto.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Supporta diff in tutti gli Stati se sotto controllo.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Il plug-in non supporta un'interfaccia utente per Get, ma IDE può comunque chiamare [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Il plug-in è rientrante e thread-safe. Nella versione 1,0 non si presuppone che i plug-in siano rientranti e thread-safe. Se un plug-in 1,1 imposta questo bit, l'host può aprire più progetti in parallelo.|

## <a name="capability-bits-added-in-version-12"></a>Bit funzionalità aggiunti nella versione 1,2

|Codice funzionalità|Valore|Descrizione|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Supporta [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Supporta [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Supporta [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Supporta [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Supporta [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Supporta più estrazioni in un file e in [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Supporta il file *Mssccprj. SCC* (soggetto a override dell'utente/amministratore) e il [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bit funzionalità aggiunti nella versione 1,3
 Questi flag vengono passati uno alla volta alla funzione [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) per determinare se la funzionalità è supportata.

|Codice funzionalità esteso|Valore|Descrizione|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Supporta l' `SCC_CHECKOUT_LOCALVER` opzione per le estrazioni.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Supporta [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Supporta [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Supporta la ricerca di directory aggiuntive.|
|`SCC_EXCAP_QUERYCHANGES`|5|Supporta l'enumerazione delle modifiche ai file.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Supporta [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Supporta [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Supporta la chiamata a SccQueryInfo su più thread.|
|`SCC_EXCAP_REMOVE_DIR`|9|Supporta la funzione SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Consente di eliminare i file estratti.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Consente di rinominare i file estratti.|

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
