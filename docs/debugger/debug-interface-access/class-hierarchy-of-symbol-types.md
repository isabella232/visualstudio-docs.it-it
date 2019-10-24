---
title: Gerarchia di classi dei tipi di simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c42ea4bb2d5c2ad91538bec8b31774a5a41aa4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745450"
---
# <a name="class-hierarchy-of-symbol-types"></a>Gerarchia di classi dei tipi di simboli
Nella tabella seguente vengono descritti i tipi di simboli della gerarchia di classi.

## <a name="symbol-types"></a>Tipi di simboli

|Tipo di simbolo|Descrizione|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|Simbolo utilizzato per rappresentare ogni classe, struttura e Unione.|
|[Enum (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Simbolo per i tipi enumerati.|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Simbolo per i tipi di puntatore.|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Simbolo per i tipi di matrice.|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Simbolo per i tipi di base|
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Simbolo che introduce i nomi per altri tipi.|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Simbolo usato per ogni classe di base di un tipo definito dall'utente (UDT).|
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Simbolo per classi friend e funzioni Friend.|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Simbolo per ogni firma di funzione univoca.|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Simbolo per ogni parametro di una funzione.|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Simbolo per le dimensioni della tabella virtuale.|
|[VTable](../../debugger/debug-interface-access/vtable.md)|Simbolo per una tabella virtuale.|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Simbolo per il tipo definito dal fornitore.|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Simbolo per un tipo definito nei metadati.|
|[Dimensione](../../debugger/debug-interface-access/dimension.md)|Simbolo per le dimensioni della matrice.|

> [!NOTE]
> Ogni simbolo può includere proprietà che contengono informazioni sul simbolo, nonché riferimenti ad altri simboli. Queste proprietà sono elencate nei singoli argomenti dei simboli.

## <a name="see-also"></a>Vedere anche
- [Enumerazione CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)