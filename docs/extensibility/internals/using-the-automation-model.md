---
title: Uso del modello di automazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f1e1479232a684758359de7527f0c2fc9990cc7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722087"
---
# <a name="using-the-automation-model"></a>Uso del modello di automazione
Dopo aver connesso il pacchetto VSPackage a automazione, è possibile ottenere le proprietà e i metodi chiamando il metodo <xref:EnvDTE.DTEClass.GetObject%2A> sull'oggetto <xref:EnvDTE._DTE>, passando una stringa che rappresenta l'oggetto che si desidera recuperare.

## <a name="obtaining-project-objects"></a>Recupero di oggetti progetto
 Di seguito sono riportati due esempi di codice che illustrano il modo in cui un consumer di automazione ottiene gli oggetti di automazione del progetto. Per informazioni su come ottenere l'oggetto DTE, vedere [How to: get references to the DTE and DTE2 Objects](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 A questo punto, è possibile usare gli oggetti di progetto standard che fanno parte di un VSPackage specifico per spostare il modello di gerarchia.

 Nell'esempio di codice seguente viene illustrato come ottenere un oggetto personalizzato che è una proprietà di un tipo di progetto personalizzato.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Il codice seguente elenca i nomi di tutte le proprietà nell'opzione **generale** ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nel menu **strumenti** :

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Vedere anche
- <xref:EnvDTE.DTEClass.GetObject%2A>