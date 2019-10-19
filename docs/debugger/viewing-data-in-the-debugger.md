---
title: Creare visualizzazioni personalizzate dei dati nel debugger | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63dc11736e92013719fcda2bae0ba9599a8835aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568995"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Creare visualizzazioni personalizzate dei dati nel debugger di Visual Studio (C#, Visual Basic, C++)

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugger sono disponibili molti strumenti per esaminare e modificare lo stato del programma. La maggior parte di questi strumenti è utilizzabile solo in modalità di interruzione.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Creare visualizzazioni personalizzate dei dati nelle finestre delle variabili e nei suggerimenti dati

 Molte delle [finestre del debugger](../debugger/debugger-windows.md), ad esempio le finestre **auto** e **espressioni di controllo** , consentono di esaminare le variabili. È possibile personalizzare il C++ modo in cui i tipi, gli oggetti gestiti e i tipi personalizzati vengono visualizzati nelle finestre delle variabili del debugger e nei [suggerimenti](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)dati. Per altre informazioni, vedere [creare visualizzazioni personalizzate di C++ oggetti](../debugger/create-custom-views-of-native-objects.md) e [creare visualizzazioni personalizzate di oggetti gestiti](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Creare visualizzatori personalizzati

 I visualizzatori consentono di visualizzare il contenuto di un oggetto o di una variabile in modo significativo. Nel debugger di Visual Studio, un visualizzatore si riferisce alle diverse finestre che è possibile aprire usando l'icona ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del Visualizzatore") lente di ingrandimento. Ad esempio, il Visualizzatore HTML Mostra come una stringa HTML verrebbe interpretata e visualizzata in un browser. È possibile accedere ai visualizzatori da suggerimenti dati, la finestra **espressioni di controllo** , la finestra **auto** e la finestra **variabili locali** . La finestra di dialogo controllo **immediato** fornisce anche un visualizzatore. Per altre informazioni, vedere [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Vedere anche

- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Finestra di comando](../ide/reference/command-window.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
