---
title: Creare visualizzazioni personalizzate dei dati nel debugger | Microsoft Docs
description: Informazioni sui vari modi per esaminare e modificare lo stato del programma nel debugger di Visual Studio. Sono incluse le finestre auto e espressioni di controllo, i suggerimenti dati e i visualizzatori.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d51821597c68a9b8e0c97e4cac3c7dc7ec2b8cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884351"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Creare visualizzazioni personalizzate dei dati nel debugger di Visual Studio (C#, Visual Basic, C++)

Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugger fornisce molti strumenti per controllare e modificare lo stato del programma. La maggior parte di questi strumenti è utilizzabile solo in modalità di interruzione.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Creare visualizzazioni personalizzate dei dati nelle finestre delle variabili e nei suggerimenti dati

 Molte delle [finestre del debugger](../debugger/debugger-windows.md), ad esempio le finestre **auto** e **espressioni di controllo** , consentono di esaminare le variabili. È possibile personalizzare il modo in cui i tipi C++, gli oggetti gestiti e i tipi personalizzati vengono visualizzati nelle finestre delle variabili del debugger e nei [suggerimenti](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)dati. Per altre informazioni, vedere [creare viste personalizzate di oggetti C++](../debugger/create-custom-views-of-native-objects.md) e [creare visualizzazioni personalizzate di oggetti gestiti](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Creare visualizzatori personalizzati

 I visualizzatori consentono di visualizzare il contenuto di un oggetto o di una variabile in modo significativo. Nel debugger di Visual Studio, un visualizzatore si riferisce alle diverse finestre che è possibile aprire usando l'icona ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del Visualizzatore") lente di ingrandimento. Ad esempio, il Visualizzatore HTML Mostra come una stringa HTML verrebbe interpretata e visualizzata in un browser. È possibile accedere ai visualizzatori da suggerimenti dati, la finestra **espressioni di controllo** , la finestra **auto** e la finestra **variabili locali** . La finestra di dialogo controllo **immediato** fornisce anche un visualizzatore. Per altre informazioni, vedere [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Vedi anche

- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Finestra di comando](../ide/reference/command-window.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
