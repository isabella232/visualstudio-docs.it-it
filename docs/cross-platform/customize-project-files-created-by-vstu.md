---
title: Personalizzare i file di progetto creati con VSTU | Microsoft Docs
description: Informazioni su come personalizzare i file di progetto creati da Visual Studio Tools per Unity (VSTU). Esaminare un esempio di codice C#.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a2e4abb707f07e0a781460e5efe6996325e5ca00
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039425"
---
# <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU
Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto. Eseguire la registrazione con l'evento `VisualStudioIntegration.ProjectFileGeneration` per modificare il file di progetto ogni volta che viene rigenerato.

## <a name="demonstrates"></a>Dimostra
 Viene illustrato come personalizzare i file di progetto di Visual Studio generati da Visual Studio Tools per Unity.

## <a name="example"></a>Esempio

```csharp
#if ENABLE_VSTU
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
#endif
```

## <a name="see-also"></a>Vedere anche
 [Esempio: callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md)
