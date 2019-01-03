---
title: Supporto del threading in Office
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48a7ab96b26dc9410eef6977c53af7a3cf4a9841
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857893"
---
# <a name="threading-support-in-office"></a>Supporto del threading in Office
  Questo articolo fornisce informazioni sul supporto di threading nel modello a oggetti Microsoft Office. Il modello a oggetti Office non è thread-safe, ma è possibile lavorare con più thread in una soluzione Office. Le applicazioni di Office sono server modello COM (Component Object). COM consente ai client di chiamare server COM in thread arbitrario. Per i server COM che non sono thread-safe, COM fornisce un meccanismo per la serializzazione di chiamate simultanee, in modo che solo un thread logico viene eseguito nel server in qualsiasi momento. Questo meccanismo è noto come il modello di apartment a thread singolo (STA). Poiché le chiamate vengono serializzate, i chiamanti potrebbero essere bloccati per periodi di tempo mentre il server è occupato o sta gestendo altre chiamate in un thread in background.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Conoscenze necessarie quando si usa più thread  
 Per usare più thread, è necessario disporre dei seguenti aspetti della conoscenza di base il multithreading:  
  
- API di Windows  
  
- COM a thread multipli concetti  
  
- Concorrenza  
  
- Sincronizzazione  
  
- Marshalling  
  
  Per informazioni generali sul multithreading, vedere [threading gestito](/dotnet/standard/threading/).  
  
  Office viene eseguita in sta principale. Comprendere le implicazioni di questo rende possibile comprendere come usare più thread con Office.  
  
## <a name="basic-multithreading-scenario"></a>Scenario multithreading semplice  
 Codice nelle soluzioni Office viene sempre eseguito nel thread principale dell'interfaccia utente. Si potrebbe voler smussare le prestazioni dell'applicazione mediante l'esecuzione di un'attività distinta su un thread in background. L'obiettivo è completare due attività apparentemente in una sola volta anziché una sola attività seguita da altro, con il risultato di esecuzione (vale a dire il motivo principale per l'utilizzo di più thread). Ad esempio, potrebbe essere il codice di eventi sul thread principale dell'interfaccia utente di Excel e in un thread in background è possibile eseguire un'attività che raccoglie i dati da un server e aggiorna le celle nell'interfaccia utente di Excel con i dati dal server.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Thread in background che effettuano chiamate nel modello a oggetti di Office  
 Quando un thread in background effettua una chiamata all'applicazione di Office, viene effettuato automaticamente il marshalling della chiamata attraverso il limite dell'APARTMENT. Tuttavia, non c'è garanzia che l'applicazione di Office può gestire la chiamata al momento che rende il thread in background. Esistono diverse possibilità:  
  
1. L'applicazione di Office è necessario che distribuisca i messaggi per la chiamata a ha la possibilità di immettere. Se sta facendo con intensa attività di elaborazione senza cede il controllo di ciò potrebbe richiedere tempo.  
  
2. Se è già in apartment con un altro thread logico, non è possibile immettere il nuovo thread. Ciò accade spesso quando un thread logico accede all'applicazione di Office e quindi effettua una chiamata rientrante all'apartment del chiamante. L'applicazione è bloccata in attesa del risultato della chiamata da restituire.  
  
3. Excel potrebbe essere in uno stato tale che non può gestire immediatamente una chiamata in ingresso. L'applicazione di Office, ad esempio, potrebbe essere visualizzata una finestra di dialogo modale.  
  
   Per le possibilità 2 e 3, COM fornisce le [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) interfaccia. Se il server implementa, tutte le chiamate entrano tramite il [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) (metodo). Possibilità di 2, le chiamate vengono rifiutate automaticamente. Possibilità di 3, il server può rifiutare la chiamata, a seconda delle circostanze. Se la chiamata viene rifiutata, il chiamante deve decidere cosa fare. In genere, l'oggetto implementa chiamante [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), nel qual caso sarebbe stato informato del rifiuto da parte le [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) (metodo).  
  
   Tuttavia, nel caso di soluzioni create mediante gli strumenti di sviluppo per Office in Visual Studio, l'interoperabilità COM converte tutte le chiamate rifiutate per una <xref:System.Runtime.InteropServices.COMException> ("filtro del messaggio indicato che l'applicazione è occupata"). Quando si esegue un modello a oggetti chiamata su un thread in background, è necessario essere preparati a gestire questa eccezione. In genere, che richiede nuovo tentativo per un determinato periodo di tempo e quindi la visualizzazione di una finestra di dialogo. Tuttavia, è possibile inoltre creare il thread in background come STA e quindi registrare un filtro dei messaggi per il thread gestire questa situazione.  
  
## <a name="start-the-thread-correctly"></a>Avviare il thread in modo corretto  
 Quando si crea un nuovo thread STA, impostare lo stato dell'apartment STA prima di avviare il thread. Nell'esempio di codice seguente viene illustrato come procedere.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Per altre informazioni, vedere [procedure consigliate di threading gestito](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Form non modali  
 Un form non modo consente un tipo di interazione con l'applicazione mentre viene visualizzato il modulo. L'utente interagisce con il modulo e quest ' ultimo interagisce con l'applicazione senza chiudere. Il modello a oggetti Office supporta gestito form non modali; ma dovrebbe non essere usati in un thread in background.  
  
## <a name="see-also"></a>Vedere anche  
 [Threading gestito](/dotnet/standard/threading/)  
 [Threading (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [Threading (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Uso thread e threading](/dotnet/standard/threading/using-threads-and-threading)   
 [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
