---
title: Usando il modello di automazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22ee836f5a4330c551181f01229e82eb14623fb8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675216"
---
# <a name="using-the-automation-model"></a>Uso del modello di automazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dopo aver connesso il pacchetto VSPackage all'automazione, è possibile ottenere le proprietà e metodi chiamando il <xref:EnvDTE.DTEClass.GetObject%2A> metodo su di <xref:EnvDTE._DTE> oggetto, passando una stringa che rappresenta l'oggetto da recuperare.  
  
## <a name="obtaining-project-objects"></a>Recupero di oggetti del progetto  
 Di seguito sono riportati due esempi di codice che illustrano come un consumer di automazione Ottiene il progetto di oggetti di automazione. Per informazioni su come ottenere l'oggetto DTE, vedere [come: Ottenere riferimenti a DTE e DTE2 oggetti](https://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
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
  
 Il codice seguente elenca i nomi di tutte le proprietà nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente **generali** opzione il **strumenti** menu:  
  
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
