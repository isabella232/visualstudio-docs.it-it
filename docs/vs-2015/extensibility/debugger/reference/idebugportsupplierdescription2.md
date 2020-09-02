---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3da559a2d843ddb1129236966093b8a41f4234b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538564"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Consente all' [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interfaccia utente di visualizzare il testo nella sezione **informazioni di trasporto** della finestra di dialogo **Connetti a processo** .  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dai fornitori di porte.  
  
## <a name="methods"></a>Metodi  
 La tabella seguente illustra i metodi di `IDebugPortSupplierDescription2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera i metadati della descrizione e della descrizione per il fornitore della porta.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
