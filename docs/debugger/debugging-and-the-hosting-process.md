---
title: Debug e processo di Hosting | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74f584eb9217e46215405aa0786e5fa10e6034a9
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37088903"
---
# <a name="debugging-and-the-hosting-process"></a>Debug e processo di hosting
Il processo di hosting di Visual Studio migliora le prestazioni del debugger e offre ulteriori funzionalità, ad esempio il debug in contesti di attendibilità parziale e la valutazione delle espressioni per la fase di progettazione. Se necessario, è possibile disabilitare il processo di hosting. Nelle sezioni riportate di seguito vengono descritte alcune differenze tra l'esecuzione del debug con e senza processo di hosting.

## <a name="partial-trust-debugging-and-click-once-security"></a>Debug in contesti di attendibilità parziale e sicurezza ClickOnce
 Il debug in contesti di attendibilità parziale richiede il processo di hosting. Se il processo di hosting viene disabilitato, questo tipo di debug non potrà funzionare anche se la sicurezza con attendibilità parziale è attivata nella pagina **Sicurezza** di **Proprietà progetto**. Per altre informazioni, vedere [procedura: eseguire il Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md).

## <a name="design-time-expression-evaluation"></a>Valutazione delle espressioni per la fase di progettazione
 Le espressioni per la fase di progettazione usano sempre il processo di hosting. La disattivazione del processo di hosting in **Proprietà progetto** comporta la disattivazione della valutazione delle espressioni per la fase di progettazione per i progetti Libreria di classi. Per altri tipi di progetto la valutazione delle espressioni per la fase di progettazione non viene disabilitata. In Visual Studio viene invece avviato l'eseguibile usato per la valutazione per la fase di progettazione senza il processo di hosting. Questa differenza potrebbe produrre risultati diversi.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Differenze in AppDomain.CurrentDomain.FriendlyName
 Nell'oggetto`AppDomain.CurrentDomain.FriendlyName` vengono restituiti risultati diversi a seconda che il processo di hosting sia attivato o meno. Se si chiama `AppDomain.CurrentDomain.FriendlyName` con il processo di hosting abilitato, viene restituito *nome_app*`.vhost.exe`. Se lo si chiama con il processo di hosting disabilitato, viene restituito *nome_app*`.exe`.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Differenze in Assembly.GetCallingAssembly().FullName
 Nell'oggetto`Assembly.GetCallingAssembly().FullName` vengono restituiti risultati diversi a seconda che il processo di hosting sia attivato o meno. Se si chiama `Assembly.GetCallingAssembly().FullName` con il processo di hosting abilitato, viene restituito `mscorlib`. Se l'oggetto `Assembly.GetCallingAssembly().FullName` viene chiamato con il processo di hosting disabilitato, viene restituito il nome dell'applicazione.

## <a name="see-also"></a>Vedere anche

- [Procedura: Eseguire il debug di un'applicazione parzialmente attendibile](../debugger/how-to-debug-a-partial-trust-application.md)