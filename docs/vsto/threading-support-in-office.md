---
title: Supporto del threading in Office
description: Il threading è supportato nel modello Microsoft Office a oggetti. Il Office a oggetti non è thread-safe, ma può funzionare con più thread in una Office soluzione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3bd8ea22fc78f0acd4f9474f56ca4cd9353688dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046204"
---
# <a name="threading-support-in-office"></a>Supporto del threading in Office
  Questo articolo fornisce informazioni sul supporto del threading nel modello Microsoft Office a oggetti. Il Office a oggetti non è thread-safe, ma è possibile usare più thread in una Office soluzione. Office applicazioni sono Component Object Model server (COM). COM consente ai client di chiamare server COM su thread arbitrari. Per i server COM che non sono thread-safe, COM fornisce un meccanismo per serializzare le chiamate simultanee in modo che nel server sia eseguito un solo thread logico alla volta. Questo meccanismo è noto come modello di apartment a thread singolo (STA). Poiché le chiamate vengono serializzate, i chiamanti potrebbero essere bloccati per periodi di tempo mentre il server è occupato o sta gestendo altre chiamate in un thread in background.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Conoscenza necessaria quando si usano più thread
 Per usare più thread, è necessario avere almeno una conoscenza di base degli aspetti seguenti del multithreading:

- API di Windows

- Concetti relativi al multithreading COM

- Concorrenza

- Sincronizzazione

- Marshaling

  Per informazioni generali sul multithreading, vedere [Threading gestito.](/dotnet/standard/threading/)

  Office viene eseguito nell'oggetto STA principale. Comprendere le implicazioni di questa operazione consente di comprendere come usare più thread con Office.

## <a name="basic-multithreading-scenario"></a>Scenario di multithreading di base
 Il codice in Office soluzioni viene sempre eseguito nel thread principale dell'interfaccia utente. È possibile migliorare le prestazioni dell'applicazione eseguendo un'attività separata in un thread in background. L'obiettivo è completare due attività apparentemente contemporaneamente anziché un'attività seguita dall'altra, il che dovrebbe comportare un'esecuzione più uniforme (il motivo principale per cui si usano più thread). Ad esempio, il codice evento potrebbe essere presente nel thread principale dell'interfaccia utente di Excel e in un thread in background è possibile eseguire un'attività che raccoglie i dati da un server e aggiorna le celle nell'interfaccia utente di Excel con i dati del server.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Thread in background che chiamano nel Office a oggetti
 Quando un thread in background effettua una chiamata all'applicazione Office, viene effettuato automaticamente il marshalling della chiamata attraverso il limite STA. Tuttavia, non esiste alcuna garanzia che l'applicazione Office possa gestire la chiamata nel momento in cui viene gestita dal thread in background. Esistono diverse possibilità:

1. Il Office deve inviare messaggi perché la chiamata abbia la possibilità di immettere . Se l'elaborazione viene erta senza produrre, questa operazione potrebbe richiedere tempo.

2. Se nell'apartment è già presente un altro thread logico, il nuovo thread non può essere inserito. Ciò si verifica spesso quando un thread logico entra nell'applicazione Office e quindi esegue una chiamata rientrante all'apartment del chiamante. L'applicazione è bloccata in attesa della restituzione della chiamata.

3. Excel essere in uno stato tale che non possa gestire immediatamente una chiamata in ingresso. Ad esempio, l Office appliazione potrebbe visualizzare una finestra di dialogo modale.

   Per le possibilità 2 e 3, COM fornisce [l'interfaccia IMessageFilter.](/windows/desktop/api/objidl/nn-objidl-imessagefilter) Se il server lo implementa, tutte le chiamate entrano tramite il [metodo HandleIncomingCall.](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) Per la possibilità 2, le chiamate vengono rifiutate automaticamente. Per la possibilità 3, il server può rifiutare la chiamata, a seconda delle circostanze. Se la chiamata viene rifiutata, il chiamante deve decidere cosa fare. In genere, il chiamante [implementa IMessageFilter,](/windows/desktop/api/objidl/nn-objidl-imessagefilter)nel qual caso verrebbe notificato il rifiuto dal [metodo RetryRejectedCall.](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall)

   Tuttavia, nel caso di soluzioni create usando gli strumenti di sviluppo Office in Visual Studio, l'interoperabilità COM converte tutte le chiamate rifiutate in ("Il filtro messaggi indica che l'applicazione è <xref:System.Runtime.InteropServices.COMException> occupata"). Ogni volta che si effettua una chiamata al modello a oggetti in un thread in background, è necessario essere pronti a gestire questa eccezione. In genere, ciò comporta un nuovo tentativo per un determinato periodo di tempo e quindi la visualizzazione di una finestra di dialogo. Tuttavia, è anche possibile creare il thread in background come STA e quindi registrare un filtro messaggi per tale thread per gestire questo caso.

## <a name="start-the-thread-correctly"></a>Avviare correttamente il thread
 Quando si crea un nuovo thread STA, impostare lo stato dell'apartment su STA prima di avviare il thread. Nell'esempio di codice seguente viene illustrato come procedere.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs" id="Snippet5":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb" id="Snippet5":::

 Per altre informazioni, vedere [Procedure consigliate per il threading gestito.](/dotnet/standard/threading/managed-threading-best-practices)

## <a name="modeless-forms"></a>Moduli non modabili
 Un form non modabile consente un certo tipo di interazione con l'applicazione mentre il form viene visualizzato. L'utente interagisce con il form e il form interagisce con l'applicazione senza chiudersi. Il Office a oggetti supporta form non modali gestiti. Tuttavia, non devono essere usati in un thread in background.

## <a name="see-also"></a>Vedi anche
- [Threading (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Threading (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Usare thread e threading](/dotnet/standard/threading/using-threads-and-threading)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
