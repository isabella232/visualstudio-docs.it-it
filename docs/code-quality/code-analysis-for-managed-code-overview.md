---
title: Analisi codice per il codice gestito
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f4e5aad0ffcd6febce411d952b1b36a0669b109a
ms.sourcegitcommit: bb72ce6ec173f3ae06c7ae57322c43690f27553c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2020
ms.locfileid: "76967302"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Panoramica dell'analisi codice per il codice gestito in Visual Studio

Visual Studio è in grado di eseguire l'analisi codice del codice gestito in due modi: con l' [analisi legacy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), nota anche come analisi statica FxCop degli assembly gestiti e con gli [analizzatori di codice più moderni basati su .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Gli analizzatori di codice basati su .NET Compiler Platform, che analizzano il codice in tempo reale durante la digitazione, sostituiscono l'analisi del codice statica FxCop legacy, che analizza solo il codice compilato.

