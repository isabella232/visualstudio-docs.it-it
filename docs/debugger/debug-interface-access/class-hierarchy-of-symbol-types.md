---
title: Gerarchia di classi dei tipi di simboli | Microsoft Docs
description: Esaminare un elenco di tipi di simboli nella gerarchia di classi dell'SDK Visual Studio di accesso all'interfaccia di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7e46e0f5c9b8b4afc3757875996dfc74bb86df33
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630726"
---
# <a name="class-hierarchy-of-symbol-types"></a>Gerarchia di classi dei tipi di simboli
Nella tabella seguente vengono descritti i tipi di simboli nella gerarchia di classi.

## <a name="symbol-types"></a>Tipi di simboli

|Tipo di simbolo|Descrizione|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|Simbolo usato per rappresentare ogni classe, struttura e unione.|
|[Enum (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Simbolo per i tipi enumerati.|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Simbolo per i tipi di puntatore.|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Simbolo per i tipi di matrice.|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Simbolo per i tipi di base|
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Simbolo che introduce nomi per altri tipi.|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Simbolo utilizzato per ogni classe di base di un tipo definito dall'utente (UDT).|
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Simbolo per le classi Friend e le funzioni Friend.|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Simbolo per ogni firma di funzione univoca.|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Simbolo per ogni parametro di una funzione.|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Simbolo per le dimensioni della tabella virtuale.|
|[VTable](../../debugger/debug-interface-access/vtable.md)|Simbolo per una tabella virtuale.|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Simbolo per il tipo definito dal fornitore.|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Simbolo per un tipo definito nei metadati.|
|[Dimensione](../../debugger/debug-interface-access/dimension.md)|Simbolo per le dimensioni della matrice.|

> [!NOTE]
> Ogni simbolo può avere proprietà che contengono informazioni sul simbolo, nonché riferimenti ad altri simboli. Queste proprietà sono elencate negli argomenti relativi ai singoli simboli.

## <a name="see-also"></a>Vedi anche
- [Enumerazione CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)