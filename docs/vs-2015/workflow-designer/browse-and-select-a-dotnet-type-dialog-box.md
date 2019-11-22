---
title: Finestra di dialogo Cerca e seleziona un tipo .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8e25ad181202a2c7994c116e2220426ca3d8509
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297618"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Finestra di dialogo Cerca e seleziona un tipo .NET
Nella finestra **Proprietà** , finestre di dialogo o finestre di progettazione, ad esempio la finestra di progettazione variabili, quando si seleziona **Cerca tipi...** da un elenco di tipi di dati, è la finestra di dialogo **Cerca e seleziona un tipo .NET** (a cui si fa riferimento in un formato abbreviato come "browser dei tipi"). In questa finestra di dialogo è possibile scegliere un tipo dalla visualizzazione albero di assembly e progetti.

 È possibile usare questa finestra di dialogo in numerosi scenari utente, ad esempio:

- Quando si imposta un tipo di variabile o argomento.

- Quando si seleziona un tipo per un'attività generica.

- Quando si aggiunge un oggetto catch all'attività <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> Il browser del tipo può visualizzare i tipi di matrice irregolari, ma non i tipi di matrice multidimensionale. Per informazioni dettagliate, vedere [matrici frastagliate](https://go.microsoft.com/fwlink/?LinkId=195226) e [matrici multidimensionali](https://go.microsoft.com/fwlink/?LinkId=195227) .

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selezione di un tipo di riferimento o di valore da Browser tipi.

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Per selezionare un tipo di riferimento o di valore dal browser dei tipi

1. Nella casella **Nome tipo** digitare il nome del tipo che si desidera usare.

2. Effettuare una delle operazioni riportate di seguito:

    - Quando il nome del tipo che si intende usare viene visualizzato nell'albero nella casella **Nome tipo**, fare doppio clic su di esso per selezionarlo.

    - Digitare nella casella **Nome tipo** un numero di caratteri sufficiente a identificare in modo univoco il tipo che si desidera usare, quindi premere INVIO per selezionare il tipo.

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Per selezionare un tipo generico dal browser dei tipi

1. Nella casella **Nome tipo** digitare il nome del tipo che si desidera usare.

2. Quando il nome del tipo che si intende usare viene visualizzato nell'albero nella casella **Nome tipo**, fare doppio clic su di esso per selezionarlo e visualizzare caselle a discesa.

     Selezionare il tipo che si desidera usare per chiudere il tipo generico dalle caselle a discesa, quindi scegliere **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Tipi visualizzati nel browser dei tipi
 I tipi visualizzati nel browser dei tipi possono variare in base alla modalità di avvio di tale browser. Se il browser dei tipi è stato avviato da un progetto flusso di lavoro all'interno di **vs2010**, per impostazione predefinita vengono visualizzati tutti i tipi degli assembly e dei progetti a cui si fa riferimento. Se il browser dei tipi è stato avviato esternamente a un sistema del progetto **vs2010** (ad esempio in un'applicazione flusso di lavoro riallocata o in un file del flusso di lavoro autonomo), per impostazione predefinita vengono visualizzati i tipi di tutti gli assembly caricati nel dominio applicazione.

 I tipi del browser dei tipi possono essere filtrati in base agli sviluppatori di ActivityDesigner. Per qualsiasi attività specificata, è possibile visualizzare solo un subset dei tipi. Per l'attività <xref:System.Activities.Statements.TryCatch>, ad esempio, nel browser dei tipi sono visualizzati solo i tipi derivati da <xref:System.Exception>.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtraggio dei risultati della ricerca nel browser dei tipi
 L'elenco di tipi presente nella casella **Nome tipo** diventa più corto man mano che si digitano altri caratteri per trovare una corrispondenza. Nell'elenco filtrato vengono visualizzati solo i tipi il cui nome completo inizia con la stringa digitata oppure i tipi il cui nome breve inizia con la stringa digitata.

 Di seguito è riportato un esempio:

1. Digitando **Operation**, si trova la corrispondenza con <xref:System.OperationCanceledException> ma non con <xref:System.InvalidOperationException>. Per trovare la corrispondenza con <xref:System.InvalidOperationException>, cominciare a digitare System.I o Invalid.

2. Digitando **Generic**, si trova la corrispondenza con <xref:System.GenericUriParser> ma non con i tipi dello spazio dei nomi <xref:System.Collections.Generic>. Per cercare i tipi nello spazio dei nomi <xref:System.Collections.Generic>, digitare il nome completo dello spazio dei nomi.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selezionare un contratto di servizio tramite la finestra di dialogo del browser dei tipi
 Quando si seleziona un tipo di contratto di servizio, il browser del tipo visualizza solo i tipi che dispongono di un attributo di <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Vedere anche
 [Uso degli Activity Designer](../workflow-designer/using-the-activity-designers.md)