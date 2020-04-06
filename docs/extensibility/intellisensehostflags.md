---
title: Proprietà IntelliSenseHostFlags . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710265"
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
|`IHF_NOSEPARATESUBJECT`|Nessun testo dell'oggetto. Il buffer di contesto `!IHF_READONLYCONTEXT`contiene IntelliSense-target (implica ).|
|`IHF_SINGLELINESUBJECT`|Il testo dell'oggetto non è in grado di eseguire più righe.|
|`IHF_FORCECOMMITTOCONTEXT`|Come per `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La modifica (nel soggetto o nel contesto) deve essere eseguita in modalità sovrascrittura.|

## <a name="requirements"></a>Requisiti
 SingleFileeditor.idl

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.TextManager.Interop>
