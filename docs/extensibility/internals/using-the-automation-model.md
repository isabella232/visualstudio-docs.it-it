---
title: Uso del modello di automazione | Microsoft Docs
description: Informazioni su come ottenere le proprietà e i metodi del pacchetto VSPackage dopo che è stato connesso al modello di automazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad8c02f846a946933ac07d4aa546ad3ce3a2a82f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488167"
---
# <a name="using-the-automation-model"></a>Uso del modello di automazione
Dopo aver connesso il pacchetto VSPackage a automazione, è possibile ottenere le proprietà e i metodi chiamando il <xref:EnvDTE.DTEClass.GetObject%2A> metodo sull' <xref:EnvDTE._DTE> oggetto, passando una stringa che rappresenta l'oggetto che si vuole recuperare.

## <a name="obtaining-project-objects"></a>Recupero di oggetti progetto
 Di seguito sono riportati due esempi di codice che illustrano il modo in cui un consumer di automazione ottiene gli oggetti di automazione del progetto. Per informazioni su come ottenere l'oggetto DTE, vedere [How to: get references to the DTE and DTE2 Objects](/previous-versions/68shb4dw(v=vs.140)).

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

 Il codice seguente elenca i nomi di tutte le proprietà nell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opzione **generale** dell'ambiente nel menu **strumenti** :

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