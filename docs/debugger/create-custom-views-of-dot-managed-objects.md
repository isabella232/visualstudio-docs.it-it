---
title: Creare viste personalizzate di oggetti | Microsoft Docs
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
ms.openlocfilehash: 911f0423184f22919be016691b9333b2f62d1b61
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744796"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Creare viste personalizzate di oggetti (C#, Visual Basic, C++)
È possibile personalizzare la modalità di visualizzazione dei tipi di dati nelle finestre delle variabili del debugger in Visual Studio.

## <a name="native-code"></a>Codice nativo

Per C++ codice, è possibile aggiungere espansioni di tipo di dati personalizzati usando il framework Natvis, come descritto in [creare viste personalizzate di C++ gli oggetti nel debugger](/visualstudio/debugger/create-custom-views-of-native-objects). Per C++/codice dell'interfaccia della riga, è anche possibile usare gli attributi, descritti di seguito in questo articolo.

## <a name="attributes"></a>Attributi

In C#, Visual Basic, e C++ (C++solo codice /CLI), è possibile aggiungere espansioni per dati personalizzati tramite <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

Nel codice di .NET Framework 2.0, Visual Basic non supporta l'attributo DebuggerBrowsable. Questa limitazione è stata rimossa nelle versioni più recenti di .NET Framework.

## <a name="visualizers"></a>Visualizzatori

È possibile scrivere un visualizzatore per visualizzare qualsiasi tipo di dati gestito. Per altre informazioni, vedere [Procedura: Scrivere un visualizzatore](/visualstudio/debugger/create-custom-visualizers-of-data).

## <a name="see-also"></a>Vedere anche

- [Indicare al debugger gli elementi da visualizzare utilizzando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Indicare al debugger il tipo per cui viene illustrato l'utilizzo dell'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Miglioramento del debug tramite gli attributi di visualizzazione del debugger](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)