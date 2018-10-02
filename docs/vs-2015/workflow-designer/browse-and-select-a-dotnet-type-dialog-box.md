---
title: Individuare e selezionare una finestra di dialogo tipo di .NET | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9347ee1d06e07f983b023e0bb67f1147b91e9adc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526191"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Finestra di dialogo Cerca e seleziona un tipo .NET
Nel **delle proprietà** finestra, le finestre di dialogo o le finestre di progettazione, ad esempio la finestra di progettazione variabile, quando si seleziona **Cerca tipi...** da un elenco dei tipi di dati, è il **individuare e selezionare un tipo .NET** finestra di dialogo (definito in una forma abbreviata come "browser tipi"). In questa finestra di dialogo è possibile scegliere un tipo dalla visualizzazione albero di assembly e progetti.  
  
 È possibile usare questa finestra di dialogo in numerosi scenari utente, ad esempio:  
  
-   Quando si imposta un tipo di variabile o argomento.  
  
-   Quando si seleziona un tipo per un'attività generica.  
  
-   Quando si aggiunge un oggetto catch all'attività <xref:System.Activities.Statements.TryCatch>.  
  
> [!NOTE]
>  Il browser del tipo può visualizzare i tipi di matrice irregolari, ma non i tipi di matrice multidimensionale. Visualizzare [matrici irregolari](http://go.microsoft.com/fwlink/?LinkId=195226) e [matrici multidimensionali](http://go.microsoft.com/fwlink/?LinkId=195227) per informazioni dettagliate.  
  
## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selezione di un tipo di riferimento o di valore da Browser tipi.  
  
#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Per selezionare un tipo di riferimento o di valore dal browser dei tipi  
  
1.  Nel **nome del tipo** immettere il nome del tipo che si desidera utilizzare.  
  
2.  Eseguire una delle operazioni seguenti:  
  
    -   Quando viene visualizzato il nome del tipo che si desidera utilizzare nell'albero di **nome del tipo di** finestra, fare doppio clic sul tipo per selezionarlo.  
  
    -   Digitare un numero di caratteri sufficiente nel **nome del tipo** finestra per identificare in modo univoco il tipo che si vuole usare e quindi premere INVIO per selezionare il tipo  
  
#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Per selezionare un tipo generico dal browser dei tipi  
  
1.  Nel **nome del tipo** casella digitare il nome del tipo che si desidera utilizzare.  
  
2.  Quando viene visualizzato il nome del tipo che si desidera utilizzare nell'albero di **nome del tipo** finestra, scegliere il tipo per selezionarlo e caselle di riepilogo a discesa vengono visualizzate.  
  
     Selezionare il tipo che si desidera utilizzare per chiudere il tipo generico dalle caselle a discesa e quindi fare clic su **OK**.  
  
## <a name="types-displayed-in-the-type-browser"></a>Tipi visualizzati nel browser dei tipi  
 I tipi visualizzati nel browser dei tipi possono variare in base alla modalità di avvio di tale browser. Se il browser dei tipi è stato avviato da un progetto di flusso di lavoro all'interno di **vs2010**, per impostazione predefinita, tutti i tipi negli assembly di riferimento e vengono visualizzati i progetti di riferimento. Se il browser dei tipi è stato avviato all'esterno di un **vs2010** progetto sistema (ad esempio in un'applicazione flusso di lavoro riallocata o in un file di flusso di lavoro autonomo), quindi per impostazione predefinita vengono visualizzati i tipi di tutti gli assembly caricati nel dominio applicazione .  
  
 I tipi del browser dei tipi possono essere filtrati in base agli sviluppatori di ActivityDesigner. Per qualsiasi attività specificata, è possibile visualizzare solo un subset dei tipi. Per l'attività <xref:System.Activities.Statements.TryCatch>, ad esempio, nel browser dei tipi sono visualizzati solo i tipi derivati da <xref:System.Exception>.  
  
## <a name="filtering-search-results-in-the-type-browser"></a>Filtraggio dei risultati della ricerca nel browser dei tipi  
 L'elenco dei tipi nel **nome del tipo** casella ottiene più breve durante la digitazione più caratteri per trovare una corrispondenza. Nell'elenco filtrato vengono visualizzati solo i tipi il cui nome completo inizia con la stringa digitata oppure i tipi il cui nome breve inizia con la stringa digitata.  
  
 Ad esempio:  
  
1.  Tipizzazione **operazione** corrisponda <xref:System.OperationCanceledException> ma non <xref:System.InvalidOperationException>. Per trovare la corrispondenza con <xref:System.InvalidOperationException>, cominciare a digitare System.I o Invalid.  
  
2.  Tipizzazione **generico** corrisponde a <xref:System.GenericUriParser> ma non con i tipi di <xref:System.Collections.Generic> dello spazio dei nomi. Per cercare i tipi nello spazio dei nomi <xref:System.Collections.Generic>, digitare il nome completo dello spazio dei nomi.  
  
## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selezionare un contratto di servizio tramite la finestra di dialogo del browser dei tipi  
 Quando si seleziona un tipo di contratto di servizio, il browser del tipo visualizza solo i tipi che dispongono di un attributo di <xref:System.ServiceModel.ServiceContractAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso degli Activity Designer](../workflow-designer/using-the-activity-designers.md)