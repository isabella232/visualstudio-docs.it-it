---
title: La registrazione di una finestra degli strumenti | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2ec947455383fd1d2a22ec98f8627ee53fbbad5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530256"
---
# <a name="registering-a-tool-window"></a>Registrazione di una finestra degli strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [la registrazione di una finestra degli strumenti](https://docs.microsoft.com/visualstudio/extensibility/registering-a-tool-window).  
  
È possibile registrare le finestre degli strumenti usando <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Esempio  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 Nel codice precedente, il <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra le finestre degli strumenti PersistedWindowPane e DynamicWindowPane con Visual Studio. La finestra degli strumenti persistente viene ancorata e a schede con **Esplora soluzioni**, e la finestra dinamica è stata assegnata un valore predefinito a partire da posizione e dimensioni. La finestra dinamica viene resa temporanea, che indica che non è stato creato all'avvio. Scrive un valore DontForceCreate nella chiave di ToolWindows nel Registro di sistema. Per altre informazioni, vedere [configurazione visualizzazione della finestra degli strumenti](../extensibility/tool-window-display-configuration.md).
