---
description: Rappresenta un provider di simboli che ha accesso diretto a metadati e interfacce di simboli di base.
title: IDebugSymbolProviderDirect | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6cce774ff6c3ca3e1037a4a61f5c8b4f892aa1c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053152"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Rappresenta un provider di simboli che ha accesso diretto a metadati e interfacce di simboli di base.

## <a name="syntax"></a>Sintassi

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Recupera l'identificatore del dominio dell'applicazione in base all'indirizzo di debug.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Recupera le informazioni sui moduli nel gruppo di simboli.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Recupera le informazioni sul gruppo di simboli di cui è membro il provider di simboli.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Recupera le informazioni di importazione dei metadati.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Recupera le informazioni sul metodo in corrispondenza dell'indirizzo di debug specificato.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Recupera un lettore di simboli per il codice non gestito.|

## <a name="remarks"></a>Commenti
 Questa interfaccia può essere utilizzata al posto della maggior parte delle altre interfacce del provider di simboli. Consente l'accesso diretto ai metadati e alle `CorSym` interfacce.

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
