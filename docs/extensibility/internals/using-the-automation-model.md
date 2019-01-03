---
title: Usando il modello di automazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4b13613c93c96b2ce709a9c9e1d082d0f7e8242
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826640"
---
# <a name="using-the-automation-model"></a>Uso del modello di automazione
Dopo aver connesso il pacchetto VSPackage all'automazione, è possibile ottenere le proprietà e metodi chiamando il <xref:EnvDTE.DTEClass.GetObject%2A> metodo su di <xref:EnvDTE._DTE> oggetto, passando una stringa che rappresenta l'oggetto da recuperare.  
  
## <a name="obtaining-project-objects"></a>Recupero di oggetti del progetto  
 Di seguito sono riportati due esempi di codice che illustrano come un consumer di automazione Ottiene il progetto di oggetti di automazione. Per informazioni su come ottenere l'oggetto DTE, vedere [come: Ottenere riferimenti a DTE e DTE2 oggetti](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
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
  
 A questo punto, è possibile usare gli oggetti di progetto standard che fanno parte di un VSPackage specifico per spostare verso il basso il modello di gerarchia.  
  
 Esempio di codice seguente viene illustrato come ottenere un oggetto personalizzato che è una proprietà di un tipo di progetto personalizzato.:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 Il codice seguente elenca i nomi di tutte le proprietà nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente **generali** opzione il **strumenti** menu:  
  
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
 <xref:EnvDTE.DTEClass.GetObject%2A>