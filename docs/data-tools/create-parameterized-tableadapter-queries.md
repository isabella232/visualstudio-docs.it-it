---
title: Creare query TableAdapter con parametri
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 94712279b09a4def616ed264483b894c673bafc4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062087"
---
# <a name="create-parameterized-tableadapter-queries"></a>Creare query TableAdapter con parametri

Una query con parametri restituisce dati che soddisfano le condizioni di una clausola WHERE all'interno della query. Ad esempio, è possibile aggiungere un parametro a un elenco di clienti in modo da visualizzare solo i clienti di una determinata città aggiungendo `WHERE City = @City` alla fine dell'istruzione SQL che restituisce un elenco di clienti.

Creare query TableAdapter con parametri in di **Progettazione Dataset**. È anche possibile crearli in un'applicazione Windows con il **origine dati con parametri** comando le **dati** menu. Il **origine dati con parametri** comando consente di creare controlli del form in cui è possibile immettere i valori dei parametri ed eseguire la query.

> [!NOTE]
> Quando si crea una query con parametri, usare la notazione di parametro specifico per il database di su che scrittura di codice. Ad esempio, nelle origini dati Access e OleDb viene usato il punto interrogativo (?) per indicare i parametri, quindi la clausola WHERE risulterebbe simile a `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Creare una query TableAdapter con parametri

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Per creare una query con parametri in Progettazione DataSet

- Creare un nuovo oggetto TableAdapter aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati. Per altre informazioni, vedere [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).

     -oppure-

- Aggiungere una query a un oggetto TableAdapter esistente aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Per creare una query con parametri durante la progettazione di un form associato a dati

1. Selezionare un controllo nel form che sia già associato a un dataset. Per altre informazioni, vedere [controlli di associare Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. Nel **Data** dal menu **Aggiungi Query**.

3. Inserire i dati mancanti nella finestra di dialogo **Generatore di criteri per la ricerca** aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Per aggiungere una query a un form associato a dati esistente

1. Aprire il modulo in **Progettazione Windows Form**.

2. Nel **dati** dal menu **Aggiungi Query** oppure **Smart tag dati**.

    > [!NOTE]
    > Se l'opzione **Aggiungi query** non è disponibile nel menu **Dati**, selezionare nel form il controllo che consente di visualizzare l'origine dati a cui si vuole aggiungere la parametrizzazione. Ad esempio, se nel form i dati sono visualizzati in un controllo <xref:System.Windows.Forms.DataGridView>, selezionarlo. Se i dati del form sono visualizzati in controlli singoli, selezionare qualsiasi controllo associato a dati.

3. Nel **tabella di origine dati selezionare** area, selezionare la tabella a cui si desidera aggiungere la parametrizzazione.

4. Digitare un nome nella casella **Nuovo nome query** se si intende creare una nuova query.

     -oppure-

     Selezionare una query nella casella **Nome query esistente**.

5. Nel **testo della Query** , digitare una query che accetta parametri.

6. Scegliere **OK**.

     Un controllo per l'immissione del parametro e un pulsante **Carica** verranno aggiunti al form in un controllo <xref:System.Windows.Forms.ToolStrip>.

### <a name="query-for-null-values"></a>Eseguire una query per valori null

TableAdapter parametri possono essere assegnati i valori null quando si desidera eseguire una query per i record privi di valori corrente. Ad esempio, si consideri la query seguente con un `ShippedDate` parametro nel relativo `WHERE` clausola:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Se si trattasse di una query su un oggetto TableAdapter, è possibile eseguire una query per tutti gli ordini che non siano stati spediti con il codice seguente:

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Per abilitare una query di accettare i valori null:

1. Nel **Progettazione Dataset**, selezionare la query TableAdapter che deve accettare i valori dei parametri null.

2. Nel **delle proprietà** finestra, seleziona **parametri**, quindi fare clic sui puntini di sospensione (**...** ) per aprire la **Editor delle raccolte Parameters**.

3. Selezionare il parametro che consente valori null e impostare il **AllowDbNull** proprietà `true`.

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)