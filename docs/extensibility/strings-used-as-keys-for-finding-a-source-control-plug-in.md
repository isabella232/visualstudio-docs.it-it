---
title: Stringhe utilizzate come chiavi per la ricerca di un plug-in del controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07962ff9e0f9371b1fc308a35600a6819602b4f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719458"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente
Le stringhe seguenti sono le chiavi per accedere al registro di sistema per trovare informazioni sul plug-in del controllo del codice sorgente.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH` e `STR_SCCPROVIDERNAME` sono le chiavi del registro di sistema o i valori utilizzati per registrare una DLL come plug-in del controllo del codice sorgente per Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE` e `SCC_STATUS_FILE` vengono utilizzati per descrivere il formato di MSSCCPRJ. File SCC.

## <a name="string-keys-and-values"></a>Chiavi e valori di stringa

|Chiave|Value|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Controllo del codice sorgente|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|Mssccprj. SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Un file di controllo del codice sorgente|
|`SCC_NSE`|Estensione dello spazio dei nomi|
|`SCC_NSE_PREFIX`|Prefisso protocal|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Procedura: Installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)