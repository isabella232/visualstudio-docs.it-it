---
title: Analisi codice per il codice gestito
ms.date: 08/27/2020
description: Informazioni sugli analizzatori di codice basati su .NET Compiler Platform in Visual Studio. Comprendere perché questi analizzatori sostituiscono l'analisi statica FxCop degli assembly gestiti.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 5fbd9e0df806e038e4016a128a4340aa46777470
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031731"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Panoramica dell'analisi del codice per .NET in Visual Studio

Visual Studio possibile eseguire l'analisi del codice gestito in due modi: con l'analisi [legacy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), nota anche come analisi statica FxCop degli assembly gestiti, e con i più moderni analizzatori di codice basati su [.NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). .NET Compiler Platform analizzatori di codice basati su , che analizzano il codice in tempo reale durante la digitazione, sostituiscono l'analisi del codice statico FxCop legacy, che analizza solo il codice compilato.
