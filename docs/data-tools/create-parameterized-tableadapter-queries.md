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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0926558c4d6e94032e2af2c75189f287da8d4811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642152"
---
# <a name="create-parameterized-tableadapter-queries"></a>Creare query TableAdapter con parametri

Una query con parametri restituisce dati che soddisfano le condizioni di una clausola WHERE all'interno della query. Ad esempio, è possibile aggiungere un parametro a un elenco di clienti in modo da visualizzare solo i clienti di una determinata città aggiungendo `WHERE City = @City` alla fine dell'istruzione SQL che restituisce un elenco di clienti.

È possibile creare query TableAdapter con parametri nel **Progettazione DataSet**. È inoltre possibile crearli in un'applicazione Windows con il comando imposta **origine dati parametrizzato** del menu **dati** . Il comando imposta **parametri origine dati** consente di creare controlli sul form in cui è possibile immettere i valori dei parametri ed eseguire la query.

> [!NOTE]
> Quando si crea una query con parametri, usare la notazione del parametro specifica del database con cui si esegue la codifica. Ad esempio, nelle origini dati Access e OleDb viene usato il punto interrogativo (?) per indicare i parametri, quindi la clausola WHERE risulterebbe simile a `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Creare una query TableAdapter con parametri

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Per creare una query con parametri in Progettazione DataSet

- Creare un nuovo oggetto TableAdapter aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati. Per altre informazioni, vedere [creare e configurare TableAdapter](../data-tools/create-and-configure-tableadapters.md).

     oppure

- Aggiungere una query a un oggetto TableAdapter esistente aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Per creare una query con parametri durante la progettazione di un form associato a dati

1. Selezionare un controllo nel form che sia già associato a un dataset. Per altre informazioni, vedere [associare Windows Forms controlli ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. Scegliere **Aggiungi query**dal menu **dati** .

3. Inserire i dati mancanti nella finestra di dialogo **Generatore di criteri per la ricerca** aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Per aggiungere una query a un form associato a dati esistente

1. Aprire il modulo in **Progettazione Windows Form**.

2. Scegliere **Aggiungi query** o **Smart tag dati**dal menu **dati** .

    > [!NOTE]
    > Se l'opzione **Aggiungi query** non è disponibile nel menu **Dati**, selezionare nel form il controllo che consente di visualizzare l'origine dati a cui si vuole aggiungere la parametrizzazione. Ad esempio, se nel form i dati sono visualizzati in un controllo <xref:System.Windows.Forms.DataGridView>, selezionarlo. Se i dati del form sono visualizzati in controlli singoli, selezionare qualsiasi controllo associato a dati.

3. Nell'area **Seleziona tabella origine dati** selezionare la tabella a cui si desidera aggiungere la parametrizzazione.

4. Digitare un nome nella casella **Nuovo nome query** se si intende creare una nuova query.

     oppure

     Selezionare una query nella casella **Nome query esistente**.

5. Nella casella di **testo query** Digitare una query che accetta parametri.

6. Scegliere **OK**.

     Un controllo per l'immissione del parametro e un pulsante **Carica** verranno aggiunti al form in un controllo <xref:System.Windows.Forms.ToolStrip>.

### <a name="query-for-null-values"></a>Eseguire una query per i valori null

Ai parametri TableAdapter è possibile assegnare valori null quando si desidera eseguire una query per i record senza valore corrente. Si consideri, ad esempio, la query seguente con un parametro `ShippedDate` nella relativa clausola `WHERE`:

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Se si trattasse di una query su un TableAdapter, era possibile eseguire una query per tutti gli ordini che non sono stati spediti con il codice seguente:

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Per consentire a una query di accettare valori null:

1. Nella **Progettazione DataSet**selezionare la query TableAdapter che deve accettare valori di parametro null.

2. Nella finestra **Proprietà** selezionare **parametri**, quindi fare clic sul pulsante con i puntini di sospensione ( **..** .) per aprire l' **Editor della raccolta Parameters**.

3. Selezionare il parametro che consente valori null e impostare la proprietà **AllowDBNull** su `true`.

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)