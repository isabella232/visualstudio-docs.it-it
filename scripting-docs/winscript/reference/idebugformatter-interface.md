---
title: Interfaccia IDebugFormatter | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 353a85ab51252c92086fa478d95b2e29ab3db62d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348035"
---
# <a name="idebugformatter-interface"></a>Interfaccia IDebugFormatter
Consente a un linguaggio o un IDE di personalizzare la conversione tra valori VARIANT o tipi VARTYPE e stringhe.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugFormatter` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Restituisce una stringa che rappresenta il valore di variante specificato.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Restituisce una variante che contiene la stringa specificata.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Restituisce una stringa che rappresenta il valore VARTYPE specificato.|