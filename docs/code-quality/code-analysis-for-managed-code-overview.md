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
ms.openlocfilehash: 08a90f1d2157088f060fe15a5a370413a55b79e7e04e736f7ac0e5a4c9b76e7b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121405604"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Panoramica dell'analisi del codice per .NET in Visual Studio

Visual Studio possibile eseguire l'analisi del codice gestito in due modi: con l'analisi [legacy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), nota anche come analisi statica FxCop degli assembly gestiti, e con i più moderni analizzatori di codice basati su [.NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). .NET Compiler Platform analizzatori di codice basati su , che analizzano il codice in tempo reale durante la digitazione, sostituiscono l'analisi del codice statico FxCop legacy, che analizza solo il codice compilato.
