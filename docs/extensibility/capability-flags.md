---
title: Flag di funzionalità | Microsoft Docs
description: Informazioni sui flag SCC_CAP_xxx che indicano le funzionalità di un plug-in di controllo del codice sorgente e i flag SCC_EXCAP_xxx che indicano le funzionalità estese.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3af4fa8c91d44a8ea8bd5075ca7aac05b6d1475e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089745"
---
# <a name="capability-flags"></a>Flag di funzionalità
I SCC_CAP_ *xxx sono* flag di bit usati per indicare le funzionalità di un plug-in del controllo del codice sorgente. I SCC_EXCAP_ *xxx sono* flag incrementali che indicano funzionalità estese e si risolvono in valori interi.

|Codice di funzionalità|Valore|Descrizione|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Supporta il [comando SccRemove](../extensibility/sccremove-function.md) e .|
|`SCC_CAP_RENAME`|0x00000002L|Supporta il [comando SccRename](../extensibility/sccrename-function.md) e .|
|`SCC_CAP_DIFF`|0x00000004L|Supporta il [comando SccDiff](../extensibility/sccdiff-function.md) e .|
|`SCC_CAP_HISTORY`|0x00000008L|Supporta il [comando SccHistory](../extensibility/scchistory-function.md) e .|
|`SCC_CAP_PROPERTIES`|0x00000010L|Supporta il [comando SccProperties](../extensibility/sccproperties-function.md) e .|
|`SCC_CAP_RUNSCC`|0x00000020L|Supporta il [comando SccRunScc](../extensibility/sccrunscc-function.md) e .|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Supporta [sccGetCommandOptions e](../extensibility/sccgetcommandoptions-function.md) il comando .|
|`SCC_CAP_QUERYINFO`|0x00000080L|Supporta il [comando SccQueryInfo](../extensibility/sccqueryinfo-function.md) e .|
|`SCC_CAP_GETEVENTS`|0x00000100L|Supporta il [comando SccGetEvents](../extensibility/sccgetevents-function.md) e .|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Supporta il [comando SccGetProjPath](../extensibility/sccgetprojpath-function.md) e .|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Supporta il [comando SccAddFromScc](../extensibility/sccaddfromscc-function.md) e .|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Supporta un commento al checkout.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Supporta un commento sull'archiviazione.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Supporta un commento su Aggiungi.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Supporta un commento su Remove.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Scrive testo in una funzione di output fornita dall'IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Supporta l'archiviazione di file senza delta.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Supporta più cronologia dei file.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Supporta il confronto di file senza distinzione tra maiuscole e minuscole.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Supporta il confronto di file che ignora gli spazi vuoti.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Supporta la ricerca di file aggiuntivi.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Supporta i commenti per la creazione del progetto.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Supporta la diff in tutti gli stati se sotto controllo.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Il plug-in non supporta un'interfaccia utente per Get, ma l'IDE può comunque chiamare [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Il plug-in è rientrante e thread-safe. Nella versione 1.0 non si presuppone che i plug-in siano rientranti e thread-safe. Se un plug-in 1.1 imposta questo bit, l'host può aprire più progetti in parallelo.|

## <a name="capability-bits-added-in-version-12"></a>Bit di funzionalità aggiunti nella versione 1.2

|Codice di funzionalità|Valore|Descrizione|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Supporta [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Supporta [SccGetParentProjectPath.](../extensibility/sccgetparentprojectpath-function.md)|
|`SCC_CAP_BATCH`|0x00040000L|Supporta [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Supporta [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Supporta [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Supporta più estrazioni in un file e [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Supporta il file *MSSCCPRJ.SCC* (soggetto a override utente/amministratore) e [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bit di funzionalità aggiunti nella versione 1.3
 Questi flag vengono passati uno alla volta alla [funzione SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) per determinare se la funzionalità è supportata.

|Codice di funzionalità esteso|Valore|Descrizione|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Supporta `SCC_CHECKOUT_LOCALVER` l'opzione per le estrazioni.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Supporta [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Supporta [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Supporta la ricerca di directory aggiuntive.|
|`SCC_EXCAP_QUERYCHANGES`|5|Supporta l'enumerazione delle modifiche ai file.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Supporta [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Supporta [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Supporta la chiamata di SccQueryInfo su più thread.|
|`SCC_EXCAP_REMOVE_DIR`|9|Supporta la funzione SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Può eliminare i file estratti.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|È possibile rinominare i file estratti.|

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
