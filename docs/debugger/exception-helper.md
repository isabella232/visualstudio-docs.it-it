---
title: Esaminare un'eccezione-Visual Studio | Microsoft Docs
ms.date: 1/18/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d044ed5ddaf4b7eb7a66bc09c8b3de3502a50f
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350498"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Esaminare un'eccezione usando l'helper eccezioni 

La gestione delle eccezioni è un problema comune, indipendentemente dalla tecnologia o dal livello di esperienza. Può essere un'esperienza frustrante capire perché le eccezioni causano problemi nel codice. Quando si esegue il debug di un'eccezione in Visual Studio, è opportuno ridurre tale frustrazione fornendo informazioni rilevanti sull'eccezione per facilitare il debug del problema.

![Helper eccezioni](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Sospendi sull'eccezione
Quando il debugger interrompe un'eccezione, viene visualizzata un'icona di errore di eccezione a destra della riga di codice. Accanto all'icona dell'eccezione verrà visualizzato un helper eccezioni non modale.

![Helper eccezioni accanto a una riga di codice](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Controllare le informazioni sull'eccezione
È possibile leggere immediatamente il tipo di eccezione e il messaggio di eccezione nell'helper eccezioni e se l'eccezione è stata generata o non gestita. È possibile esaminare e visualizzare le proprietà dell'oggetto eccezione facendo clic sul collegamento **Visualizza dettagli** .

## <a name="analyze-null-references"></a>Analizza riferimenti null
A partire da Visual Studio 2017, per il codice .NET e C/C++, quando si raggiunge un `NullReferenceException` oggetto o `AccessViolation` , vengono visualizzate le informazioni di analisi null nell'helper eccezioni. L'analisi viene visualizzata come testo sotto il messaggio dell'eccezione. Nell'illustrazione seguente le informazioni sono visualizzate come "**s** is null".

![Analisi null Helper eccezioni](media/debugger-exception-helper-default.png)


> [!NOTE]
> L'analisi di riferimento null nel codice gestito richiede .NET versione 4.6.2. L'analisi dei valori null non è attualmente supportata per piattaforma UWP (Universal Windows Platform) (UWP) e per altre applicazioni .NET Core. È disponibile solo durante il debug di codice che non dispone di ottimizzazioni del codice JIT (just-in-Time).

## <a name="configure-exception-settings"></a>Configurare le impostazioni delle eccezioni 
È possibile configurare il debugger in modo che si interrompa quando viene generata un'eccezione del tipo corrente dalla sezione **Impostazioni eccezioni** dell'helper eccezioni. Se il debugger viene sospeso in corrispondenza di un'eccezione generata, è possibile utilizzare la casella di controllo per disabilitare l'interruzione di tale tipo di eccezione quando viene generata in futuro. Se non si vuole interrompere questa particolare eccezione quando viene generata in questo particolare modulo, selezionare la casella di controllo in base al nome del modulo in **tranne quando viene generata da:** nella finestra **Impostazioni eccezioni** . 

## <a name="inspect-inner-exceptions"></a>Esaminare le eccezioni interne 
Se l'eccezione presenta eccezioni interne ([innerException](https://docs.microsoft.com/dotnet/api/system.exception.innerexception), è possibile visualizzarle nell'helper eccezioni. Se sono presenti più eccezioni, è possibile spostarsi tra di esse usando le frecce sinistra e destra visualizzate sopra lo stack di chiamate.

![Helper eccezione con eccezione interna](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Controllare le eccezioni rigenerate
Nei casi in cui è stata rilevata un'eccezione `thrown` , l'helper eccezioni Mostra lo stack di chiamate dalla prima volta che è stata generata l'eccezione. Se l'eccezione è stata generata più volte, viene visualizzato solo lo stack di chiamate dell'eccezione originale.

![Helper eccezioni con eccezioni rigenerate](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Condividere una sessione di debug con Live Share
Dall'helper eccezioni è possibile avviare una sessione di [Live Share](https://docs.microsoft.com/visualstudio/liveshare/) usando il collegamento **avvia Live Share sessione...**. Tutti gli utenti che partecipano alla sessione Live Share possono visualizzare l'helper eccezioni insieme a qualsiasi altra informazione di debug.
