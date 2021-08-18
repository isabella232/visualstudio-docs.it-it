---
title: Creare query TableAdapter con parametri
description: Informazioni su come creare query TableAdapter con parametri. Una query con parametri restituisce dati che soddisfano le condizioni di una clausola WHERE all'interno della query.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 53ede3f31574ec2bbbd9b5cc2ce1f588b4ed5233
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052837"
---
# <a name="create-parameterized-tableadapter-queries"></a>Creare query TableAdapter con parametri

Una query con parametri restituisce dati che soddisfano le condizioni di una clausola WHERE all'interno della query. Ad esempio, è possibile aggiungere un parametro a un elenco di clienti in modo da visualizzare solo i clienti di una determinata città aggiungendo `WHERE City = @City` alla fine dell'istruzione SQL che restituisce un elenco di clienti.

È possibile creare query TableAdapter con parametri nel **Progettazione DataSet**. È anche possibile crearli in un'Windows con il comando **Parametrizza** origine dati **del** menu Dati. Il **comando Parametrizza origine dati** crea controlli nel form in cui è possibile immettere i valori dei parametri ed eseguire la query.

> [!NOTE]
> Quando si costruisce una query con parametri, usare la notazione dei parametri specifica per il database su cui si sta creando il codice. Ad esempio, nelle origini dati Access e OleDb viene usato il punto interrogativo (?) per indicare i parametri, quindi la clausola WHERE risulterebbe simile a `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Creare una query TableAdapter con parametri

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Per creare una query con parametri in Progettazione DataSet

- Creare un nuovo oggetto TableAdapter aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati. Per altre informazioni, vedere [Creare e configurare oggetti TableAdapter.](../data-tools/create-and-configure-tableadapters.md)

     -oppure-

- Aggiungere una query a un oggetto TableAdapter esistente aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Per creare una query con parametri durante la progettazione di un form associato a dati

1. Selezionare un controllo nel form che sia già associato a un dataset. Per altre informazioni, vedere [Associare Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. Scegliere **Aggiungi** query dal menu **Dati.**

3. Inserire i dati mancanti nella finestra di dialogo **Generatore di criteri per la ricerca** aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Per aggiungere una query a un form associato a dati esistente

1. Aprire il modulo in **Progettazione Windows Form**.

2. Scegliere **Aggiungi** query  o **Smart tag dati dal** menu Dati .

    > [!NOTE]
    > Se l'opzione **Aggiungi query** non è disponibile nel menu **Dati**, selezionare nel form il controllo che consente di visualizzare l'origine dati a cui si vuole aggiungere la parametrizzazione. Ad esempio, se nel form i dati sono visualizzati in un controllo <xref:System.Windows.Forms.DataGridView>, selezionarlo. Se i dati del form sono visualizzati in controlli singoli, selezionare qualsiasi controllo associato a dati.

3. **Nell'area Seleziona tabella origine dati** selezionare la tabella a cui si desidera aggiungere la parametrizzazione.

4. Digitare un nome nella casella **Nuovo nome query** se si intende creare una nuova query.

     -oppure-

     Selezionare una query nella casella **Nome query esistente**.

5. Nella casella **Testo** query digitare una query che accetta parametri.

6. Selezionare **OK**.

     Un controllo per l'immissione del parametro e un pulsante **Carica** verranno aggiunti al form in un controllo <xref:System.Windows.Forms.ToolStrip>.

### <a name="query-for-null-values"></a>Eseguire una query per i valori Null

È possibile assegnare valori Null ai parametri TableAdapter quando si desidera eseguire una query per i record che non hanno alcun valore corrente. Si consideri, ad esempio, la query seguente con `ShippedDate` un parametro nella `WHERE` clausola :

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Se si trattasse di una query su un TableAdapter, è possibile eseguire una query per tutti gli ordini che non sono stati spediti con il codice seguente:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb" id="Snippet8":::

Per consentire a una query di accettare valori Null:

1. Nel **Progettazione DataSet** selezionare la query TableAdapter che deve accettare valori di parametro Null.

2. Nella finestra **Proprietà** **selezionare Parametri**, quindi fare clic sul pulsante con i puntini di sospensione (**...**) per aprire Editor **raccolta parametri**.

3. Selezionare il parametro che consente valori Null e impostare la **proprietà AllowDbNull** su `true` .

## <a name="see-also"></a>Vedi anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
