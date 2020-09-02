---
title: Condividere il callback di log di Unity con VSTU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: b58d693980ffc55ccfe613d52e868bccca9908b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145729"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per evitare questa eventualità, usare l'evento `VisualStudioIntegration.LogCallback` per cooperare con VSTU.  
  
## <a name="demonstrates"></a>Dimostra  
 Viene illustrato come condividere il callback di log Unity creato da Visual Studio Tools per Unity.  
  
## <a name="example"></a>Esempio  
  
```csharp  
using System;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio: generazione di file di progetto](../cross-platform/customize-project-files-created-by-vstu.md)
