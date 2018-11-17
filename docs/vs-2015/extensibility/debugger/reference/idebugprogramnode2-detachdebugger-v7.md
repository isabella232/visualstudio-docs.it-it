---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 756af9cbe89a84ed892fb229fcba01daa8984e1e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780386"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

DEPRECATO. NON USARE.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un'implementazione deve sempre restituire `E_NOTIMPL`.  
  
## <a name="remarks"></a>Note  
  
> [!WARNING]
>  A partire [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL`.  
  
 Questo metodo viene chiamato quando il debugger viene chiuso in modo imprevisto. Quando questo metodo viene chiamato, la Germania deve essere ripreso il programma come se l'utente disconnesso da quest'ultimo. Nessun altro evento di debug deve essere inviato. Il programma deve essere in uno stato in cui è associabile da un'altra istanza del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

