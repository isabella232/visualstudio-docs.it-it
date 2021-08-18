---
title: Uso del modello di automazione | Microsoft Docs
description: Informazioni su come ottenere le proprietà e i metodi del pacchetto VSPackage dopo la connessione al modello di automazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d57979e3913f9bfbfd4b782574de012b3f8523bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086437"
---
# <a name="using-the-automation-model"></a>Uso del modello di automazione
Dopo aver connesso il VSPackage all'automazione, è possibile ottenere le proprietà e i metodi chiamando il metodo sull'oggetto , passando una stringa che rappresenta l'oggetto <xref:EnvDTE.DTEClass.GetObject%2A> <xref:EnvDTE._DTE> che si vuole recuperare.

## <a name="obtaining-project-objects"></a>Recupero Project oggetti
 Di seguito sono riportati due esempi di codice che illustrano come un consumer di automazione ottiene gli oggetti di automazione del progetto. Per informazioni su come ottenere l'oggetto DTE, vedere Procedura: Ottenere riferimenti [agli oggetti DTE e DTE2](/previous-versions/68shb4dw(v=vs.140)).

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

 A questo punto, è possibile usare gli oggetti di progetto standard che fanno parte di un pacchetto VSPackage specifico per spostarsi verso il basso nel modello di gerarchia.

 Nell'esempio di codice seguente viene illustrato come ottenere un oggetto personalizzato che è una proprietà di un tipo di progetto personalizzato:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Il codice seguente elenca i nomi di tutte le proprietà nell'opzione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Generale** dell'ambiente del  menu Strumenti:

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