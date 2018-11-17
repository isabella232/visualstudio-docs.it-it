---
title: Creare viste personalizzate di oggetti gestiti | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 607844200ad2ccc7f50cea834c24da3adea14413
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808466"
---
# <a name="create-custom-views-of-managed-objects"></a>Creare viste personalizzate di oggetti gestiti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile personalizzare la modalità di visualizzazione dei tipi di dati nelle finestre delle variabili del debugger in Visual Studio.  
  
## <a name="attributes"></a>Attributi  
 In C# e Visual Basic, è possibile aggiungere espansioni per dati personalizzati tramite <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Nel codice [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] Visual Basic non supporta l'attributo DebuggerBrowsable. Questa limitazione è stata rimossa nelle versioni più recenti di .NET Framework.  
  
## <a name="visualizers"></a>Visualizzatori  
 È possibile scrivere un visualizzatore per visualizzare qualsiasi tipo di dati gestito. Per altre informazioni, vedere [procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Codice nativo  
 Per il codice nativo, è possibile aggiungere espansioni per tipi di dati personalizzati al file autoexp.dat, che si trova nella directory Programmi\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. Le istruzioni relative alla sintassi delle regole `autoexp` sono contenute nel file stesso.  
  
> [!CAUTION]
>  La struttura di questo file e la sintassi delle regole autoexp possono variare in base alle diverse versioni di Visual Studio.  
  
 Le visualizzazioni del tipo nativo possono anche essere personalizzate scrivendo un componente aggiuntivo dell'analizzatore di espressioni. Per altre informazioni, vedere [EEAddIn Sample: debug di espressione dell'analizzatore di espressioni componenti](http://msdn.microsoft.com/en-us/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso dell'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Uso dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Espressioni di controllo e controllo immediato Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Miglioramento del debug tramite gli attributi di visualizzazione del debugger](http://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)



