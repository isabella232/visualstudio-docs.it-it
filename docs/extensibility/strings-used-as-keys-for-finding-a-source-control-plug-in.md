---
title: Stringhe usate come chiavi per trovare un plug-in del controllo del codice sorgente
description: Informazioni sulle stringhe che sono le chiavi per l'accesso al Registro di sistema per trovare informazioni sul plug-in controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 878dc8239361b0490d17f25ad0b96f748f39cf6e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117579"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente
Le stringhe seguenti sono le chiavi per l'accesso al Registro di sistema per trovare informazioni sul plug-in del controllo del codice sorgente.

 `STR_SCC_PROVIDER_REG_LOCATION`, , e sono chiavi del Registro di sistema o valori usati per registrare una DLL come plug-in di controllo del codice `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH` `STR_SCCPROVIDERNAME` sorgente per Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE` , e vengono usati per descrivere il `SCC_STATUS_FILE` formato di MSSCCPRJ. File SCC.

## <a name="string-keys-and-values"></a>Chiavi e valori stringa

|Chiave|Valore|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Controllo del codice sorgente|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Un file di controllo del codice sorgente|
|`SCC_NSE`|Estensione dello spazio dei nomi|
|`SCC_NSE_PREFIX`|Prefisso protocale|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|Raccolta HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Procedura: Installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
