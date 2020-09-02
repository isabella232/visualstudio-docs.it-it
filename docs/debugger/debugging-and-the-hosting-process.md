---
title: Debug e processo di hosting | Microsoft Docs
ms.date: 08/01/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77df2eae643b658e915662e0f50f6a376141d27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "73188462"
---
# <a name="debugging-and-the-hosting-process"></a>Debug e processo di hosting
Il processo di hosting di Visual Studio migliora le prestazioni del debugger e offre ulteriori funzionalità, ad esempio il debug in contesti di attendibilità parziale e la valutazione delle espressioni per la fase di progettazione. Se necessario, è possibile disabilitare il processo di hosting. Nelle sezioni riportate di seguito vengono descritte alcune differenze tra l'esecuzione del debug con e senza processo di hosting.

> [!NOTE]
> A partire da Visual Studio 2017, l'opzione per eseguire il debug con il processo di hosting non è più necessaria ed è stata rimossa. Per altre informazioni, vedere [debug: Visual Studio 2017 mira ad accelerare il processo meno preferito](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Debug in contesti di attendibilità parziale e sicurezza ClickOnce
 Il debug in contesti di attendibilità parziale richiede il processo di hosting. Se il processo di hosting viene disabilitato, questo tipo di debug non potrà funzionare anche se la sicurezza con attendibilità parziale è attivata nella pagina **Sicurezza** di **Proprietà progetto**. Per altre informazioni, vedere [procedura: eseguire il debug di un'applicazione parzialmente attendibile](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Valutazione delle espressioni per la fase di progettazione
 Le espressioni per la fase di progettazione usano sempre il processo di hosting. La disattivazione del processo di hosting in **Proprietà progetto** comporta la disattivazione della valutazione delle espressioni per la fase di progettazione per i progetti Libreria di classi. Per altri tipi di progetto la valutazione delle espressioni per la fase di progettazione non viene disabilitata. In Visual Studio viene invece avviato l'eseguibile usato per la valutazione per la fase di progettazione senza il processo di hosting. Questa differenza potrebbe produrre risultati diversi.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Differenze in AppDomain.CurrentDomain.FriendlyName
 Nell'oggetto`AppDomain.CurrentDomain.FriendlyName` vengono restituiti risultati diversi a seconda che il processo di hosting sia attivato o meno. Se si chiama `AppDomain.CurrentDomain.FriendlyName` con il processo di hosting abilitato, viene restituito *APP_NAME* `.vhost.exe` . Se si chiama il processo di hosting disabilitato, viene restituito *APP_NAME* `.exe` .

## <a name="assemblygetcallingassemblyfullname-differences"></a>Differenze in Assembly.GetCallingAssembly().FullName
 Nell'oggetto`Assembly.GetCallingAssembly().FullName` vengono restituiti risultati diversi a seconda che il processo di hosting sia attivato o meno. Se si chiama `Assembly.GetCallingAssembly().FullName` con il processo di hosting abilitato, viene restituito `mscorlib`. Se l'oggetto `Assembly.GetCallingAssembly().FullName` viene chiamato con il processo di hosting disabilitato, viene restituito il nome dell'applicazione.

## <a name="see-also"></a>Vedere anche

- [Procedura: Eseguire il debug di un'applicazione parzialmente attendibile](debugger-security.md)