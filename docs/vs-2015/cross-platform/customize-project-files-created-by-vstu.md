---
title: Personalizzare i file di progetto creati con VSTU | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 9144eaf751c9e78c79d247121d34dd4365ea5414
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184613"
---
# <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto. Eseguire la registrazione con l'evento `VisualStudioIntegration.ProjectFileGeneration` per modificare il file di progetto ogni volta che viene rigenerato.  
  
## <a name="demonstrates"></a>Dimostrazione  
 Viene illustrato come personalizzare i file di progetto di Visual Studio generati da Visual Studio Tools per Unity.  
  
## <a name="example"></a>Esempio  
  
```csharp  
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
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio: callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md)

