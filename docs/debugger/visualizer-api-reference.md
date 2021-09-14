---
title: Informazioni di riferimento sulle API del visualizzatore | Microsoft Docs
description: Un visualizzatore visualizza un tipo specifico di elemento dati e può consentire anche la modifica. Per crearne uno, usare l'API Visualizzatore documentata in questa sezione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- APIs, visualizers
- reference, visualizer APIs
- visualizers, API reference
ms.assetid: b9ff4ed0-9e80-49df-9016-a81189319afd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7dbf4105320531a21f478ef8947129e0fa754c28
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627810"
---
# <a name="visualizer-api-reference"></a>Informazioni di riferimento sulle API del visualizzatore

Le API del visualizzatore vengono fornite per gli utenti che desiderano scrivere un visualizzatore per il debugger di Visual Studio. Un visualizzatore è una piccola applicazione che estende le funzionalità dell'interfaccia utente del debugger di Visual Studio e consente di visualizzare e facoltativamente modificare un oggetto dati di un tipo specifico per il quale è stato progettato.

## <a name="in-this-section"></a>Contenuto della sezione

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource?displayProperty=fullName>

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Scrittura di un visualizzatore in C #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Procedura: scrivere un visualizzatore](create-custom-visualizers-of-data.md)
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)