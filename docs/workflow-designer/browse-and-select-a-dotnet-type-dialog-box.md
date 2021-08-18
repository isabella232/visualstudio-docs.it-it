---
title: Finestra di dialogo Cerca e seleziona un tipo .NET
description: Informazioni su come usare la finestra di dialogo Sfoglia e seleziona un tipo .NET per scegliere un tipo da una visualizzazione albero di assembly e progetti in Progettazione flussi di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- dotnet
ms.openlocfilehash: b0258a69738f340ca8a2a58d1c3b900171625e5d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068131"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Finestra di dialogo Cerca e seleziona un tipo .NET

Nella  finestra Proprietà, nelle finestre di dialogo o nelle finestre  di progettazione, ad esempio la finestra di progettazione delle variabili, quando si seleziona Sfoglia per i tipi da un elenco di tipi di dati, viene visualizzata la finestra di dialogo Sfoglia e seleziona un tipo **.NET** ,a cui si fa riferimento in forma abbreviata come "browser dei tipi". In questa finestra di dialogo è possibile scegliere un tipo dalla visualizzazione albero di assembly e progetti.

È possibile usare questa finestra di dialogo in numerosi scenari utente, ad esempio:

- Quando si imposta un tipo di variabile o argomento.

- Quando si seleziona un tipo per un'attività generica.

- Quando si aggiunge un oggetto catch all'attività <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> Il browser del tipo può visualizzare i tipi di matrice irregolari, ma non i tipi di matrice multidimensionale. Per informazioni dettagliate, vedere Matrici [frastagliate](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) [e matrici multidimensionali.](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90))

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selezione di un tipo di riferimento o di valore da Browser tipi.

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Per selezionare un tipo di riferimento o di valore dal browser dei tipi

1. Nella **casella Nome** tipo immettere il nome del tipo da usare.

2. Eseguire una delle operazioni seguenti:

    - Quando il nome del tipo da usare viene visualizzato nell'albero nella casella **Nome** tipo , fare doppio clic sul tipo per selezionarlo.

    - Digitare un numero di caratteri sufficiente nella casella **Nome** tipo per identificare in modo univoco il tipo che si vuole usare e quindi premere INVIO per selezionare il tipo

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Per selezionare un tipo generico dal browser dei tipi

1. Nella **casella Nome** tipo digitare il nome del tipo da usare.

2. Quando il nome del tipo da usare viene visualizzato  nell'albero nella casella Nome tipo , fare clic sul tipo per selezionarlo per visualizzare le caselle a discesa.

     Selezionare il tipo da usare per chiudere il generico dalle caselle a discesa e quindi fare clic su **OK.**

## <a name="types-displayed-in-the-type-browser"></a>Tipi visualizzati nel browser dei tipi

I tipi visualizzati nel browser dei tipi possono variare in base alla modalità di avvio di tale browser. Se il browser dei tipi è stato avviato da un progetto del flusso di lavoro all'interno di **vs2010,** per impostazione predefinita vengono visualizzati tutti i tipi negli assembly a cui si fa riferimento e nei progetti a cui si fa riferimento. Se il browser dei tipi è stato avviato dall'esterno di un sistema di progetto **vs2010** ,ad esempio in un'applicazione del flusso di lavoro rihosted o in un file del flusso di lavoro autonomo, per impostazione predefinita vengono visualizzati i tipi di tutti gli assembly caricati in AppDomain.

I tipi del browser dei tipi possono essere filtrati in base agli sviluppatori di ActivityDesigner. Per qualsiasi attività specificata, è possibile visualizzare solo un subset dei tipi. Per l'attività <xref:System.Activities.Statements.TryCatch>, ad esempio, nel browser dei tipi sono visualizzati solo i tipi derivati da <xref:System.Exception>.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtraggio dei risultati della ricerca nel browser dei tipi

L'elenco dei tipi nella casella **Nome** tipo diventa più breve quando si digitano più caratteri per trovare una corrispondenza. Nell'elenco filtrato vengono visualizzati solo i tipi il cui nome completo inizia con la stringa digitata o i tipi il cui nome breve inizia con la stringa digitata.

Esempio:

1. **L'operazione di digitazione** <xref:System.OperationCanceledException> corrisponde ma non <xref:System.InvalidOperationException> . Per trovare la corrispondenza con <xref:System.InvalidOperationException>, cominciare a digitare System.I o Invalid.

2. La **digitazione di corrispondenze** <xref:System.GenericUriParser> generiche ma non di tipi nello spazio dei <xref:System.Collections.Generic> nomi . Per cercare i tipi nello spazio <xref:System.Collections.Generic> dei nomi , digitare il nome completo dello spazio dei nomi.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selezionare un contratto di servizio tramite la finestra di dialogo del browser dei tipi

Quando si seleziona un tipo di contratto di servizio, il browser del tipo visualizza solo i tipi che dispongono di un attributo di <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Vedi anche

- [Utilizzo degli ActivityDesigner](control-flow-activity-designers.md)
