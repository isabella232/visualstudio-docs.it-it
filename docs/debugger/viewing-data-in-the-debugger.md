---
title: Creare viste personalizzate di dati nel debugger | Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e5c5466515e0e58fd94d7a949b04d060a90925d1
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227226"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Creare viste personalizzate dei dati nel debugger di Visual Studio (C#, Visual Basic, C++)

Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugger fornisce molti strumenti per analizzare e modificare lo stato del programma. La maggior parte di questi strumenti è utilizzabile solo in modalità di interruzione.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Creare visualizzazioni personalizzate dei dati nelle finestre delle variabili e i suggerimenti dati

 Molte del [finestre del debugger](../debugger/debugger-windows.md), ad esempio il **Auto** e **Watch** windows, consentono di controllare le variabili. È possibile personalizzare i tipi come nativi, gli oggetti gestiti e i tipi personalizzati vengono visualizzati nelle finestre delle variabili del debugger e in [suggerimenti dati](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Per altre informazioni, vedere [creare viste personalizzate di oggetti nativi](../debugger/create-custom-views-of-native-objects.md) e [creare viste personalizzate di oggetti](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Creare visualizzatori personalizzati

 Visualizzatori consentono inoltre di visualizzare il contenuto di un oggetto o una variabile in modo significativo. Nel debugger di Visual Studio, un visualizzatore si riferisce alle diverse finestre che è possibile aprire usando la lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore") icona. Ad esempio, il visualizzatore HTML viene illustrato come verrebbe interpretata e visualizzata in un browser una stringa HTML. I visualizzatori sono accessibili da suggerimenti dati, il **Watch** finestra, il **Auto** finestra e il **variabili locali** finestra. Il **controllo immediato** nella finestra di dialogo fornisce anche un visualizzatore. Per altre informazioni, vedere [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Vedere anche

 [Esaminare innanzitutto il debugger](../debugger/debugger-feature-tour.md) [finestra di comando](../ide/reference/command-window.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)