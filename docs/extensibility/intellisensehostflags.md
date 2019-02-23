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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 882410d68c671a83b13bd14026e5bea4c31cb37e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683558"
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