---
title: Stringhe usate come chiavi per la ricerca del plug-in un controllo del codice sorgente | Microsoft Docs
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
ms.openlocfilehash: 31c2b30fb41976cdbbab13fa22d438c63bddbbef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331709"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente
Le stringhe seguenti sono le chiavi per l'accesso del Registro di sistema per trovare informazioni sul controllo del codice sorgente del plug-in.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, e `STR_SCCPROVIDERNAME` sono le chiavi del Registro di sistema o i valori utilizzati per registrare una DLL come un plug-in del controllo del codice sorgente per Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, e `SCC_STATUS_FILE` vengono usati per descrivere il formato del MSSCCPRJ. File di controllo del codice sorgente.

## <a name="string-keys-and-values"></a>Chiavi String e valori

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
|`SCC_STATUS_FILE`|MSSCCPRJ.SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Un file di controllo del codice sorgente|
|`SCC_NSE`|Estensione Namespace|
|`SCC_NSE_PREFIX`|Prefisso Protocal|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Procedura: installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)