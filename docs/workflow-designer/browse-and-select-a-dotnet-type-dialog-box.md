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
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963234"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Finestra di dialogo Cerca e seleziona un tipo .NET

Nella  finestra Proprietà, nelle finestre di dialogo o nelle finestre  di progettazione, ad esempio la finestra di progettazione delle variabili, quando si seleziona Sfoglia per tipi da un elenco di tipi di dati, viene visualizzata la finestra di dialogo Sfoglia e seleziona un tipo **.NET** , a cui viene fatto riferimento in forma abbreviata come "browser dei tipi". In questa finestra di dialogo è possibile scegliere un tipo dalla visualizzazione albero di assembly e progetti.

È possibile usare questa finestra di dialogo in numerosi scenari utente, ad esempio:

- Quando si imposta un tipo di variabile o argomento.

- Quando si seleziona un tipo per un'attività generica.

- Quando si aggiunge un oggetto catch all'attività <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> Il browser del tipo può visualizzare i tipi di matrice irregolari, ma non i tipi di matrice multidimensionale. Per [informazioni dettagliate, vedere](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) Matrici di matrici e [matrici multidimensionali.](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90))

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selezione di un tipo di riferimento o di valore da Browser tipi.

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Per selezionare un tipo di riferimento o di valore dal browser dei tipi

1. Nella **casella Nome** tipo immettere il nome del tipo che si vuole usare.

2. Eseguire una delle operazioni seguenti:

    - Quando il nome del tipo da usare viene visualizzato  nell'albero nella casella Nome tipo , fare doppio clic sul tipo per selezionarlo.

    - Digitare un numero sufficiente di caratteri nella casella **Nome** tipo per identificare in modo univoco il tipo da usare e quindi premere INVIO per selezionare il tipo

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Per selezionare un tipo generico dal browser dei tipi

1. Nella **casella Nome** tipo digitare il nome del tipo che si vuole usare.

2. Quando il nome del tipo che si desidera utilizzare  viene visualizzato nell'albero nella casella Nome tipo , fare clic sul tipo per selezionarlo in modo da visualizzare le caselle a discesa.

     Selezionare il tipo che si vuole usare per chiudere il generico dalle caselle a discesa e quindi fare clic su **OK.**

## <a name="types-displayed-in-the-type-browser"></a>Tipi visualizzati nel browser dei tipi

I tipi visualizzati nel browser dei tipi possono variare in base alla modalità di avvio di tale browser. Se il browser dei tipi è stato avviato da un progetto flusso di lavoro all'interno di **vs2010,** per impostazione predefinita vengono visualizzati tutti i tipi negli assembly di riferimento e nei progetti a cui si fa riferimento. Se il browser dei tipi è stato avviato dall'esterno di un sistema di progetto **vs2010** (ad esempio in un'applicazione flusso di lavoro rihosted o in un file del flusso di lavoro autonomo), per impostazione predefinita vengono visualizzati i tipi di tutti gli assembly caricati nell'AppDomain.

I tipi del browser dei tipi possono essere filtrati in base agli sviluppatori di ActivityDesigner. Per qualsiasi attività specificata, è possibile visualizzare solo un subset dei tipi. Per l'attività <xref:System.Activities.Statements.TryCatch>, ad esempio, nel browser dei tipi sono visualizzati solo i tipi derivati da <xref:System.Exception>.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtraggio dei risultati della ricerca nel browser dei tipi

L'elenco dei tipi nella **casella Nome** tipo diventa più breve quando si digitano più caratteri per trovare una corrispondenza. Nell'elenco filtrato vengono visualizzati solo i tipi il cui nome completo inizia con la stringa digitata o i tipi il cui nome breve inizia con la stringa digitata.

Ad esempio:

1. **L'operazione di** <xref:System.OperationCanceledException> digitazione corrisponde a ma non a <xref:System.InvalidOperationException> . Per trovare la corrispondenza con <xref:System.InvalidOperationException>, cominciare a digitare System.I o Invalid.

2. La **digitazione generica** <xref:System.GenericUriParser> corrisponde ma non ai tipi nello spazio dei nomi <xref:System.Collections.Generic> . Per cercare i tipi nello spazio <xref:System.Collections.Generic> dei nomi , digitare il nome completo dello spazio dei nomi.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selezionare un contratto di servizio tramite la finestra di dialogo del browser dei tipi

Quando si seleziona un tipo di contratto di servizio, il browser del tipo visualizza solo i tipi che dispongono di un attributo di <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Vedi anche

- [Utilizzo degli ActivityDesigner](control-flow-activity-designers.md)
