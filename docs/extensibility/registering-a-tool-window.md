---
title: Registrazione di una finestra degli strumenti | Microsoft Docs
description: Informazioni su come registrare le finestre degli strumenti con Visual Studio usando ProvideToolWindowAttribute e ProvideToolWindowVisibilityAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fb0163c9c28f1ceb51a2685b92d081b3012757b1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028696"
---
# <a name="register-a-tool-window"></a>Registrare una finestra degli strumenti
È possibile registrare le finestre degli strumenti usando <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Esempio

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 Nel codice precedente, registra <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> le finestre degli strumenti e con `PersistedWindowPane` `DynamicWindowPane` Visual Studio. La finestra degli strumenti persistente è ancorata e a schede **con Esplora soluzioni** e alla finestra dinamica vengono fornite una posizione iniziale e una dimensione predefinite. La finestra dinamica viene resa temporanea, a indicare che non viene creata all'avvio. Viene scritto un `DontForceCreate` valore nella chiave del Registro di `ToolWindows` sistema. Per altre informazioni, vedere [Configurazione della visualizzazione della finestra degli strumenti.](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015)