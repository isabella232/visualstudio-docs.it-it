---
title: Creare visualizzazioni personalizzate di oggetti gestiti | Microsoft Docs
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f5247a56667f5715d9f155c662eb333967878d71
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188644"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Creazione di visualizzazioni personalizzate di oggetti gestitiC#(, Visual Basic F#, C++,/CLI)
È possibile personalizzare la modalità di visualizzazione dei tipi di dati nelle finestre delle variabili del debugger in Visual Studio.

## <a name="attributes"></a>Attributi

In C#Visual Basic, F#e C++ (C++solo codice/CLI), è possibile aggiungere espansioni per i dati personalizzati tramite <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

Nel codice .NET Framework 2,0 Visual Basic non supporta l'attributo l'DebuggerBrowsable. Questa limitazione è stata rimossa nelle versioni più recenti di .NET.

## <a name="visualizers"></a>Visualizzatori

È possibile scrivere un visualizzatore per visualizzare qualsiasi tipo di dati gestito. Per altre informazioni, vedere [procedura: scrivere un visualizzatore](create-custom-visualizers-of-data.md).

> [!NOTE]
> Per C++ il codice, è possibile aggiungere espansioni di tipi di dati personalizzati usando natvis Framework, come descritto in [creare visualizzazioni personalizzate C++ di oggetti nel debugger](create-custom-views-of-native-objects.md).

## <a name="see-also"></a>Vedere anche

- [Indicare al debugger cosa visualizzare usando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Indicare al debugger quale tipo visualizzare usando l'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Miglioramento del debug tramite gli attributi di visualizzazione del debugger](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
