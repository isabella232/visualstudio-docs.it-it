---
title: IntelliSenseHostFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d0e66f70b91985882df5691d05175995b4f6ca8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328086"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Specifica i flag host IntelliSense.

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
|`IHF_READONLYCONTEXT`|Buffer del contesto è di sola lettura.|
|`IHF_NOSEPARATESUBJECT`|Nessun testo dell'oggetto. Buffer del contesto contiene IntelliSense-target (implica `!IHF_READONLYCONTEXT`).|
|`IHF_SINGLELINESUBJECT`|Testo dell'oggetto non è più-riga in grado di supportare.|
|`IHF_FORCECOMMITTOCONTEXT`|Uguale a `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La modifica (nell'oggetto o al contesto) deve essere eseguita in modalità sovrascrittura.|

## <a name="requirements"></a>Requisiti
 SingleFileeditor.idl

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.TextManager.Interop>