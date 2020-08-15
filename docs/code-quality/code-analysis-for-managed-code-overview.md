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
ms.openlocfilehash: 901c66a97a763345ee32b1a1540a7998934d0ff3
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248984"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Panoramica dell'analisi codice per il codice gestito in Visual Studio

Visual Studio è in grado di eseguire l'analisi codice del codice gestito in due modi: con l' [analisi legacy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), nota anche come analisi statica FxCop degli assembly gestiti e con gli [analizzatori di codice più moderni basati su .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Gli analizzatori di codice basati su .NET Compiler Platform, che analizzano il codice in tempo reale durante la digitazione, sostituiscono l'analisi del codice statica FxCop legacy, che analizza solo il codice compilato.
