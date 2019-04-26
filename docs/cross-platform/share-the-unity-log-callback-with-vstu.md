---
title: Condividere il callback di log di Unity con VSTU | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: aa8a4a229102a6a9439ffb36582cd03e322a086b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815665"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU
Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per evitare questa eventualità, usare l'evento `VisualStudioIntegration.LogCallback` per cooperare con VSTU.

## <a name="demonstrates"></a>Dimostrazione
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
 [Esempio: Generazione dei file di progetto](../cross-platform/customize-project-files-created-by-vstu.md)
