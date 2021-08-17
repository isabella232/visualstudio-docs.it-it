---
title: Creare visualizzazioni personalizzate dei dati nel debugger | Microsoft Docs
description: Informazioni sui vari modi per controllare e modificare lo stato del programma Visual Studio debugger. Sono incluse le finestre Auto e Espressioni di controllo, Suggerimenti dati e Visualizzatori.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9cdce099df34fbf7937ed83d1adc70fe36c13176
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043908"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Creare visualizzazioni personalizzate dei dati nel debugger Visual Studio (C#, Visual Basic, C++)

Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugger offre molti strumenti per controllare e modificare lo stato del programma. La maggior parte di questi strumenti è utilizzabile solo in modalità di interruzione.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Creare visualizzazioni personalizzate dei dati nelle finestre delle variabili e nei suggerimenti dati

 Molte delle finestre [del debugger,](../debugger/debugger-windows.md)ad esempio le **finestre Auto** ed **Espressioni di** controllo, consentono di esaminare le variabili. È possibile personalizzare la modalità di visualizzazione dei tipi C++, degli oggetti gestiti e dei tipi personalizzati nelle finestre delle variabili del debugger e nei [suggerimenti dati.](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) Per altre informazioni, vedere [Creare visualizzazioni personalizzate di oggetti C++](../debugger/create-custom-views-of-native-objects.md) e [Creare visualizzazioni personalizzate di oggetti gestiti.](../debugger/create-custom-views-of-managed-objects.md)

## <a name="create-custom-visualizers"></a>Creare visualizzatori personalizzati

 I visualizzatori consentono di visualizzare il contenuto di un oggetto o di una variabile in modo significativo. Nel debugger Visual Studio, un visualizzatore fa riferimento alle diverse finestre che è possibile aprire usando la lente di ingrandimento ![VisualizzatoreIcona icona a](../debugger/media/dbg-tips-visualizer-icon.png "Icona del visualizzatore") forma di lente di ingrandimento. Ad esempio, il visualizzatore HTML mostra come viene interpretata e visualizzata una stringa HTML in un browser. È possibile accedere ai visualizzatori dai suggerimenti dati, **dalla** finestra Espressioni di controllo, dalla **finestra** Auto e dalla **finestra Variabili** locali. Nella **finestra di dialogo** Controllo immediato è disponibile anche un visualizzatore. Per altre informazioni, vedere [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Vedi anche

- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Finestra di comando](../ide/reference/command-window.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
