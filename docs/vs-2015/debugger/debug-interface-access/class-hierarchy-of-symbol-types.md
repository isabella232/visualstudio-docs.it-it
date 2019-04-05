---
title: Gerarchia dei tipi di simboli delle classi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ece5c23a04901eaf0c17e7dfbf59f1ce7c5ccfa2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955160"
---
# <a name="class-hierarchy-of-symbol-types"></a>Gerarchia di classi dei tipi di simboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nella tabella seguente vengono descritti i tipi di simboli nella gerarchia delle classi.  
  
## <a name="symbol-types"></a>Tipi di simboli  
  
|Tipo di simbolo|Descrizione|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Simbolo utilizzato per rappresentare ogni classe, struttura e unione.|  
|[Enum (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Simboli per i tipi enumerati.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Simboli per i tipi di puntatore.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Simboli per i tipi di matrice.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Simboli per i tipi di base|  
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Simbolo che introduce i nomi per gli altri tipi.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Simbolo utilizzato per ogni classe di base di un tipo definito dall'utente (UDT).|  
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Simboli per le funzioni friend e classi friend.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Simbolo per ogni firma della funzione univoco.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Simbolo per ogni parametro a una funzione.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Simboli per le dimensioni della tabella virtuale.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Simbolo per una tabella virtuale.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Simbolo per il tipo definito dal fornitore.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Simbolo per un tipo definito nei metadati.|  
|[Dimensione](../../debugger/debug-interface-access/dimension.md)|Simboli per le dimensioni di matrice.|  
  
> [!NOTE]
>  Ciascun simbolo può avere proprietà che contengono informazioni sui simboli, nonché i riferimenti a altri simboli. Queste proprietà sono elencate negli argomenti simbolo singoli.  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazione CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
