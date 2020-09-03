---
title: Condividere il callback di log di Unity con VSTU | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: dc54c51f078e5b800a9cc9f2de687db7b1fa0387
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815044"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU
Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per evitare questa eventualità, usare l'evento `VisualStudioIntegration.LogCallback` per cooperare con VSTU.

## <a name="demonstrates"></a>Dimostra
 Viene illustrato come condividere il callback di log Unity creato da Visual Studio Tools per Unity.

## <a name="example"></a>Esempio

```csharp
#if ENABLE_VSTU
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
#endif
```

## <a name="see-also"></a>Vedere anche
 [Esempio: generazione di file di progetto](../cross-platform/customize-project-files-created-by-vstu.md)
