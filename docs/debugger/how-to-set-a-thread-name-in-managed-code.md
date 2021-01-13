---
title: Impostare un nome di thread nel codice gestito | Microsoft Docs
description: Impostare un nome di thread nel codice gestito durante il debug di app multithread in Visual Studio. La denominazione dei thread viene utilizzata per tenere traccia dei thread nella finestra thread.
ms.custom: SEO-VS-2020
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c52d2ae3407833594049459a489641135bba172c
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148442"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Procedura: impostare il nome di un thread in codice gestito
La denominazione dei thread è possibile in tutte le edizioni di Visual Studio. Tale denominazione è utile per tenere traccia dei thread nella finestra **Thread**.

 Per impostare il nome di un thread in codice gestito, usare la proprietà <xref:System.Threading.Thread.Name%2A>.

## <a name="example"></a>Esempio

```csharp
public class Needle
{
    // This method will be called when the thread is started.
    public void Baz()
    {
        Console.WriteLine("Needle Baz is running on another thread");
    }
}

public void Main()
{
    Console.WriteLine("Thread Simple Sample");
    Needle oNeedle = new Needle();
    // Create a Thread object.
    System.Threading.Thread oThread = new System.Threading.Thread(oNeedle.Baz);
    // Set the Thread name to "MyThread".
    oThread.Name = "MyThread";
    // Starting the thread invokes the ThreadStart delegate
    oThread.Start();
}
```

```VB
Public Class Needle
    ' This method will be called when the thread is started.
    Sub Baz()
        Console.WriteLine("Needle Baz is running on another thread")
    End Sub
End Class

Sub Main()
    Console.WriteLine("Thread Simple Sample")
    Dim oNeedle As New Needle()
   ' Create a Thread object.
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)
    ' Set the Thread name to "MyThread".
    oThread.Name = "MyThread"
    ' Starting the thread invokes the ThreadStart delegate
    oThread.Start()
End Sub
```

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Procedura: impostare il nome di un thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)