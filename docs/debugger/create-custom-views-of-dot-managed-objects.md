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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c2e4b2d34df1a1e870247112892d4cd00ff887f3
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227642"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Creare viste personalizzate di oggetti (C#, Visual Basic, C++)
È possibile personalizzare la modalità di visualizzazione dei tipi di dati nelle finestre delle variabili del debugger in Visual Studio.  

## <a name="native-code"></a>Codice nativo

Per codice C++, è possibile aggiungere espansioni di tipo di dati personalizzati usando il framework Natvis, come descritto in [creare viste personalizzate di oggetti nativi nel debugger](/visualstudio/debugger/create-custom-views-of-native-objects). Per C + + c++ /CLI codice dell'interfaccia della riga, è anche possibile usare gli attributi, descritti di seguito in questo articolo.

## <a name="attributes"></a>Attributi

In C#, Visual Basic e C++ (C + + / solo il codice dell'interfaccia della riga), è possibile aggiungere espansioni per dati personalizzati utilizzando <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
Nel codice [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] Visual Basic non supporta l'attributo DebuggerBrowsable. Questa limitazione è stata rimossa nelle versioni più recenti di .NET Framework.    

## <a name="visualizers"></a>Visualizzatori

È possibile scrivere un visualizzatore per visualizzare qualsiasi tipo di dati gestito. Per altre informazioni, vedere [Procedura: Scrivere un visualizzatore](/visualstudio/debugger/create-custom-visualizers-of-data).
  
## <a name="see-also"></a>Vedere anche  
 [Uso dell'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)   
 [Miglioramento del debug tramite gli attributi di visualizzazione del debugger](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)