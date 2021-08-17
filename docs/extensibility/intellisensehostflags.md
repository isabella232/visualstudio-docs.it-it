---
title: IntelliSenseHostFlags | Microsoft Docs
description: L'enumerazione IntelliSenseHostFlags specifica i flag host IntelliSense. Questo articolo descrive i valori di enumerazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0672f7a4d8788c0efac9e11b5ae3359338791ebbf572fed0a9b12d0e185f00b8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376456"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Specifica i flag host di IntelliSense.

## <a name="syntax"></a>Sintassi

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Parametri

|Membri|Descrizione|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Il buffer di contesto è di sola lettura.|
|`IHF_NOSEPARATESUBJECT`|Nessun testo dell'oggetto. Il buffer di contesto contiene la destinazione IntelliSense (implica `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Il testo dell'oggetto non supporta più righe.|
|`IHF_FORCECOMMITTOCONTEXT`|Uguale a `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La modifica (nell'oggetto o nel contesto) deve essere eseguita in modalità sovrascritta.|

## <a name="requirements"></a>Requisiti
 SingleFileeditor.idl

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.TextManager.Interop>
