---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1bb6813992e616d964f3e86f8f42645d50700058
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774844"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Consente il [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] dell'interfaccia utente per visualizzare il testo all'interno di **informazioni sul trasporto** sezione del **Connetti a processo** nella finestra di dialogo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata da fornitori di porte.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortSupplierDescription2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera la descrizione e una descrizione dei metadati per il fornitore della porta.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

