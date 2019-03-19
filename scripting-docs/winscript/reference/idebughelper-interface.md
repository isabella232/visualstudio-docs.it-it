---
title: Interfaccia IDebugHelper | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1708b742a484a2e7d6d48cf759f15c08711e13d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148060"
---
# <a name="idebughelper-interface"></a>Interfaccia IDebugHelper
Viene usato come una factory per visualizzatori oggetti e punti di connessione semplici. Il gestore di debug di processi (PDM) implementa questa interfaccia, che viene usata da motori di script.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugHelper` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Restituisce un visualizzatore di proprietà che esegue il wrapping di una variante.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Restituisce un visualizzatore di proprietà che esegue il wrapping di una variante e consente la conversione personalizzata di valori VARIANT o tipi VARTYPE in stringhe.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Restituisce un'interfaccia di eventi che esegue il wrapping di un determinato `IDispatch` oggetto.|