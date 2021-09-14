---
title: Esaminare un'eccezione
titleSuffix: ''
description: Informazioni sulle informazioni fornite Visual Studio per eseguire il debug delle eccezioni e su come disabilitare in modo selettivo l'interruzione in caso di eccezioni.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0b93a717d4a3f22db860f2bbef51bc51e0f8cc85
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626495"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Esaminare un'eccezione usando l'helper eccezioni 

La gestione delle eccezioni è un problema comune, indipendentemente dalla tecnologia o dal livello di esperienza. Può essere un'esperienza frustrante capire perché le eccezioni causano problemi nel codice. Quando si esegue il debug di un'eccezione in Visual Studio, si vuole ridurre la frustrazione fornendo informazioni sulle eccezioni rilevanti per facilitare il debug del problema più rapidamente.

![Helper eccezioni](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Sospendere l'eccezione
Quando il debugger si interrompe in caso di eccezione, a destra di tale riga di codice viene visualizzata un'icona di errore di eccezione. Accanto all'icona dell'eccezione verrà visualizzato un helper eccezioni non modale.

![Helper eccezioni accanto a una riga di codice](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Esaminare le informazioni sulle eccezioni
È possibile leggere immediatamente il tipo di eccezione e il messaggio di eccezione nell'helper eccezioni e se l'eccezione è stata generata o non gestita. È possibile esaminare e visualizzare le proprietà dell'oggetto Exception facendo clic sul **collegamento Visualizza** dettagli.

## <a name="analyze-null-references"></a>Analizzare i riferimenti Null
A partire da Visual Studio 2017, sia per il codice .Net che per il codice C/C++, quando si preme o , vengono visualizzate informazioni di analisi `NullReferenceException` `AccessViolation` null nell'helper eccezioni. L'analisi viene visualizzata come testo sotto il messaggio di eccezione. Nella figura seguente le informazioni vengono visualizzate come **"s** era null".

![Analisi null dell'helper eccezioni](media/debugger-exception-helper-default.png)


> [!NOTE]
> L'analisi dei riferimenti Null nel codice gestito richiede .NET versione 4.6.2. L'analisi Null non è attualmente supportata per la piattaforma UWP (Universal Windows Platform) e altre applicazioni .NET Core. È disponibile solo durante il debug di codice che non dispone di ottimizzazioni del codice JIT (Just-In-Time).

## <a name="configure-exception-settings"></a>Configurare le impostazioni delle eccezioni 
È possibile configurare il debugger in modo che si interrompa quando viene generata un'eccezione del tipo corrente dalla sezione Exception **Impostazioni** dell'helper eccezioni. Se il debugger viene sospeso in corrispondenza di un'eccezione generata, è possibile usare la casella di controllo per disabilitare l'interruzione di tale tipo di eccezione quando viene generata in futuro. Se non si vuole interrompere questa particolare eccezione quando viene generata in questo modulo specifico, selezionare la casella  di controllo in Tranne quando generata **da:** nella finestra Eccezione Impostazioni. 

## <a name="inspect-inner-exceptions"></a>Esaminare le eccezioni interne 
Se l'eccezione include eccezioni interne ([InnerException](/dotnet/api/system.exception.innerexception), è possibile visualizzarle nell'helper eccezioni. Se sono presenti più eccezioni, è possibile spostarsi tra di esse usando le frecce sinistra e destra visualizzate sopra lo stack di chiamate.

![Helper eccezioni con eccezione interna](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Esaminare le eccezioni generate di nuovo
Nei casi in cui è stata generata un'eccezione, l'helper eccezioni mostra lo stack di chiamate dalla prima volta che l'eccezione `thrown` è stata generata. Se l'eccezione è stata generata più volte, viene visualizzato solo lo stack di chiamate dell'eccezione originale.

![Helper eccezioni con eccezioni generate di nuovo](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Condividere una sessione di debug con Live Share
Dall'helper eccezioni è possibile avviare una sessione [Live Share](/visualstudio/liveshare/) usando il collegamento Avvia Live Share **sessione...**. Tutti gli utenti che Live Share sessione possono visualizzare l'helper eccezioni insieme a qualsiasi altra informazione di debug.