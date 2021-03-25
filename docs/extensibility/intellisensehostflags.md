---
title: IntelliSenseHostFlags | Microsoft Docs
description: L'enumerazione IntelliSenseHostFlags specifica i flag host di IntelliSense. Questo articolo descrive i valori enum.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 83a3911670a10710ad6ae5cd6496fb76af6c27bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079137"
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
|`IHF_READONLYCONTEXT`|Il buffer del contesto è di sola lettura.|
|`IHF_NOSEPARATESUBJECT`|Nessun testo soggetto. Il buffer del contesto contiene la destinazione IntelliSense (implica `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Il testo dell'oggetto non è in grado di supportare più righe.|
|`IHF_FORCECOMMITTOCONTEXT`|Uguale a `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La modifica (in oggetto o contesto) deve essere eseguita in modalità sovratipo.|

## <a name="requirements"></a>Requisiti
 SingleFileeditor. idl

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.TextManager.Interop>
