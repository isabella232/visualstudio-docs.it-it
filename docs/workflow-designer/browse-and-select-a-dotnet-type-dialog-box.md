---
title: Progettazione flussi di lavoro-Cerca e seleziona una finestra di dialogo di tipo .NET
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2efea8f23e42b9f4839c8a1ae0d74248738b9cf4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985348"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Finestra di dialogo Cerca e seleziona un tipo .NET

Nella finestra **Proprietà** , finestre di dialogo o finestre di progettazione, ad esempio la finestra di progettazione variabili, quando si seleziona **Cerca tipi** da un elenco di tipi di dati, è la finestra di dialogo **Cerca e seleziona un tipo .NET** (a cui si fa riferimento in un formato abbreviato come "tipo" browser "). In questa finestra di dialogo è possibile scegliere un tipo dalla visualizzazione albero di assembly e progetti.

È possibile usare questa finestra di dialogo in numerosi scenari utente, ad esempio:

- Quando si imposta un tipo di variabile o argomento.

- Quando si seleziona un tipo per un'attività generica.

- Quando si aggiunge un oggetto catch all'attività <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> Il browser del tipo può visualizzare i tipi di matrice irregolari, ma non i tipi di matrice multidimensionale. Per informazioni dettagliate, vedere [matrici frastagliate](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) e [matrici multidimensionali](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) .

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selezione di un tipo di riferimento o di valore da Browser tipi.

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Per selezionare un tipo di riferimento o di valore dal browser dei tipi

1. Nella casella **nome tipo** immettere il nome del tipo che si desidera utilizzare.

2. Effettuare una delle operazioni riportate di seguito:

    - Una volta visualizzato il nome del tipo che si desidera utilizzare nell'albero nella casella **nome tipo** , fare doppio clic sul tipo per selezionarlo.

    - Digitare un numero di caratteri sufficiente nella casella **nome tipo** per identificare in modo univoco il tipo che si vuole usare e quindi premere INVIO per selezionare il tipo

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Per selezionare un tipo generico dal browser dei tipi

1. Nella casella **nome tipo** Digitare il nome del tipo che si desidera utilizzare.

2. Una volta visualizzato il nome del tipo che si vuole usare nell'albero nella casella **nome tipo** , fare clic sul tipo per selezionarlo per fare in modo che vengano visualizzate le caselle di riepilogo a discesa.

     Selezionare il tipo che si desidera utilizzare per chiudere l'oggetto generico dalle caselle di riepilogo a discesa, quindi fare clic su **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Tipi visualizzati nel browser dei tipi

I tipi visualizzati nel browser dei tipi possono variare in base alla modalità di avvio di tale browser. Se il browser dei tipi è stato avviato da un progetto flusso di lavoro all'interno di **VS2010**, per impostazione predefinita vengono visualizzati tutti i tipi negli assembly a cui si fa riferimento e i progetti a cui si fa riferimento. Se il browser dei tipi è stato avviato dall'esterno di un sistema di progetto **VS2010** , ad esempio in un'applicazione flusso di lavoro riallocata o in un file di flusso di lavoro autonomo, per impostazione predefinita vengono visualizzati i tipi di tutti gli assembly caricati nel dominio AppDomain.

I tipi del browser dei tipi possono essere filtrati in base agli sviluppatori di ActivityDesigner. Per qualsiasi attività specificata, è possibile visualizzare solo un subset dei tipi. Per l'attività <xref:System.Activities.Statements.TryCatch>, ad esempio, nel browser dei tipi sono visualizzati solo i tipi derivati da <xref:System.Exception>.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtraggio dei risultati della ricerca nel browser dei tipi

L'elenco dei tipi nella casella **nome tipo** diventa più breve quando si digitano altri caratteri per trovare una corrispondenza. Solo i tipi il cui nome FullyQualified inizia con la stringa digitata o i tipi il cui nome breve inizia con la stringa digitata vengono visualizzati nell'elenco filtrato.

Esempio:

1. L' **operazione** di digitazione corrisponde <xref:System.OperationCanceledException> ma non <xref:System.InvalidOperationException>. Per trovare la corrispondenza con <xref:System.InvalidOperationException>, cominciare a digitare System.I o Invalid.

2. Digitando corrispondenze **generiche** <xref:System.GenericUriParser> ma non i tipi nello spazio dei nomi <xref:System.Collections.Generic>. Per cercare i tipi nello spazio dei nomi <xref:System.Collections.Generic>, digitare il nome completo dello spazio dei nomi.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selezionare un contratto di servizio tramite la finestra di dialogo del browser dei tipi

Quando si seleziona un tipo di contratto di servizio, il browser del tipo visualizza solo i tipi che dispongono di un attributo di <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Vedere anche

- [Uso degli Activity Designer](../workflow-designer/using-the-activity-designers.md)