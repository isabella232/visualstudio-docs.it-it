---
title: Analisi codice per il codice gestito
ms.date: 08/27/2020
description: Informazioni sugli analizzatori di codice basati su .NET Compiler Platform in Visual Studio. Comprendere il motivo per cui questi analizzatori sostituiscono l'analisi statica FxCop degli assembly gestiti.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 542747f650888b384a9f9c4910b0d9caea93e948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860568"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Panoramica dell'analisi del codice per .NET in Visual Studio

Visual Studio è in grado di eseguire l'analisi codice del codice gestito in due modi: con l' [analisi legacy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), nota anche come analisi statica FxCop degli assembly gestiti e con gli [analizzatori di codice più moderni basati su .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Gli analizzatori di codice basati su .NET Compiler Platform, che analizzano il codice in tempo reale durante la digitazione, sostituiscono l'analisi del codice statica FxCop legacy, che analizza solo il codice compilato.
