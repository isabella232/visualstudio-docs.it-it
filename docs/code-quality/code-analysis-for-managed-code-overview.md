---
title: Analisi codice per il codice gestito
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 016bcdc7cd3e3619457beb321800e98544efb6c9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2020
ms.locfileid: "89091401"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Panoramica dell'analisi del codice per .NET in Visual Studio

Visual Studio è in grado di eseguire l'analisi codice del codice gestito in due modi: con l' [analisi legacy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), nota anche come analisi statica FxCop degli assembly gestiti e con gli [analizzatori di codice più moderni basati su .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Gli analizzatori di codice basati su .NET Compiler Platform, che analizzano il codice in tempo reale durante la digitazione, sostituiscono l'analisi del codice statica FxCop legacy, che analizza solo il codice compilato.
