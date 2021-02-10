---
title: Supporto del threading in Office
description: Il threading è supportato nel modello a oggetti Microsoft Office. Il modello a oggetti di Office non è thread-safe, ma può funzionare con più thread in una soluzione Office.
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
ms.workload:
- office
ms.openlocfilehash: 6fd35551c5c40494c169fb569113e3530f633a6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940800"
---
# <a name="threading-support-in-office"></a>Supporto del threading in Office
  Questo articolo fornisce informazioni sul supporto del threading nel modello a oggetti Microsoft Office. Il modello a oggetti di Office non è thread-safe, ma è possibile usare più thread in una soluzione Office. Le applicazioni di Office sono Server Component Object Model (COM). COM consente ai client di chiamare server COM su thread arbitrari. Per i server COM che non sono thread-safe, COM fornisce un meccanismo per serializzare le chiamate simultanee in modo da eseguire un solo thread logico sul server in qualsiasi momento. Questo meccanismo è noto come modello di Apartment a thread singolo (STA). Poiché le chiamate vengono serializzate, i chiamanti possono essere bloccati per periodi di tempo mentre il server è occupato o gestisce altre chiamate in un thread in background.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Informazioni necessarie quando si usano più thread
 Per usare più thread, è necessario avere almeno una conoscenza di base degli aspetti seguenti del multithreading:

- API di Windows

- Concetti COM multithreading

- Concorrenza

- Sincronizzazione

- Marshaling

  Per informazioni generali sul multithreading, vedere [Threading gestito](/dotnet/standard/threading/).

  Office viene eseguito nell'oggetto STA principale. Comprendere le implicazioni di questo consente di comprendere come usare più thread con Office.

## <a name="basic-multithreading-scenario"></a>Scenario multithreading di base
 Il codice nelle soluzioni Office viene sempre eseguito nel thread principale dell'interfaccia utente. Potrebbe essere necessario smussare le prestazioni dell'applicazione eseguendo un'attività separata in un thread in background. L'obiettivo è quello di completare due attività in modo apparentemente, anziché un'attività seguita dall'altra, che dovrebbe comportare un'esecuzione più uniforme (il motivo principale per usare più thread). Ad esempio, è possibile avere il codice evento sul thread principale dell'interfaccia utente di Excel e in un thread in background è possibile eseguire un'attività che raccoglie i dati da un server e aggiorna le celle nell'interfaccia utente di Excel con i dati del server.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Thread in background che effettuano chiamate nel modello a oggetti di Office
 Quando un thread in background effettua una chiamata all'applicazione di Office, viene eseguito automaticamente il marshalling della chiamata attraverso il limite STA. Tuttavia, non vi è alcuna garanzia che l'applicazione di Office possa gestire la chiamata nel momento in cui il thread in background lo rende. Sono disponibili diverse possibilità:

1. L'applicazione di Office deve pompare i messaggi affinché la chiamata abbia la possibilità di entrare. Se è in corso un'elaborazione intensa senza produrre questa operazione potrebbe richiedere tempo.

2. Se un altro thread logico è già presente nell'Apartment, non è possibile immettere il nuovo thread. Questo problema si verifica spesso quando un thread logico entra nell'applicazione di Office e quindi effettua una chiamata rientrante all'Apartment del chiamante. L'applicazione è bloccata in attesa che venga restituita la chiamata.

3. Excel potrebbe trovarsi in uno stato in modo tale che non sia in grado di gestire immediatamente una chiamata in ingresso. Ad esempio, l'applicazione di Office potrebbe visualizzare una finestra di dialogo modale.

   Per le possibilità 2 e 3, COM fornisce l'interfaccia [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) . Se il server lo implementa, tutte le chiamate entrano tramite il metodo [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) . Per la possibilità 2, le chiamate vengono rifiutate automaticamente. Per la possibilità 3, il server può rifiutare la chiamata, a seconda delle circostanze. Se la chiamata viene rifiutata, il chiamante deve decidere cosa fare. In genere, il chiamante implementa [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), nel qual caso riceverà una notifica del rifiuto da parte del metodo [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) .

   Tuttavia, nel caso di soluzioni create tramite gli strumenti di sviluppo di Office in Visual Studio, l'interoperabilità COM converte tutte le chiamate rifiutate in un <xref:System.Runtime.InteropServices.COMException> ("il filtro messaggi indica che l'applicazione è occupata"). Ogni volta che si effettua una chiamata a un modello a oggetti in un thread in background, è necessario essere pronti a gestire questa eccezione. In genere, ciò comporta un nuovo tentativo per un determinato periodo di tempo e quindi la visualizzazione di una finestra di dialogo. Tuttavia, è anche possibile creare il thread in background come STA e quindi registrare un filtro messaggi per tale thread per gestire questo caso.

## <a name="start-the-thread-correctly"></a>Avviare correttamente il thread
 Quando si crea un nuovo thread STA, impostare lo stato dell'Apartment su STA prima di avviare il thread. Nell'esempio di codice seguente viene illustrato come procedere.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 Per altre informazioni, vedere [procedure consigliate per il threading gestito](/dotnet/standard/threading/managed-threading-best-practices).

## <a name="modeless-forms"></a>Moduli non modale
 Un form non modale consente un tipo di interazione con l'applicazione mentre viene visualizzato il modulo. L'utente interagisce con il modulo e il modulo interagisce con l'applicazione senza chiudere. Il modello a oggetti di Office supporta i moduli gestiti non in modalità. Tuttavia, non devono essere usati in un thread in background.

## <a name="see-also"></a>Vedi anche
- [Threading (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Threading (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Usare thread e Threading](/dotnet/standard/threading/using-threads-and-threading)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
