---
title: Registrazione di una finestra degli strumenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701592"
---
# <a name="register-a-tool-window"></a>Registrare una finestra degli strumentiRegister a tool window
È possibile registrare <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> le <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>finestre degli strumenti utilizzando e .

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

 Nel codice precedente, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra `PersistedWindowPane` le `DynamicWindowPane` finestre degli strumenti e con Visual Studio.In the code above, the registers the and tool windows with Visual Studio. La finestra persistente degli strumenti è ancorata e a schede con **Esplora soluzioni**e alla finestra dinamica vengono assegnate una posizione e una dimensione iniziali predefinite. La finestra dinamica viene resa temporanea, che indica che non viene creata all'avvio. In questo `DontForceCreate` modo `ToolWindows` viene scritto un valore nella chiave nel Registro di sistema. Per ulteriori informazioni, vedere [Configurazione della visualizzazione della finestra degli strumenti](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015).
