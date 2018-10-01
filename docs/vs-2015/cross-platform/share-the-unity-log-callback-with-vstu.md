---
title: Condividere il callback di log di Unity con VSTU | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 8e1e0f2062195830443a169c67d9b75d2b1915ec
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531085"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [condividere il Callback di Log di Unity con VSTU](https://docs.microsoft.com/visualstudio/cross-platform/share-the-unity-log-callback-with-vstu).  
  
  
Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per evitare questa eventualità, usare l'evento `VisualStudioIntegration.LogCallback` per cooperare con VSTU.  
  
## <a name="demonstrates"></a>Dimostrazione  
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

