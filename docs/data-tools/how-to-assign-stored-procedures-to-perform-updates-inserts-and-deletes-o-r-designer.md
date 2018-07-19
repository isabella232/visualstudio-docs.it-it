---
title: Usa stored procedure per eseguire l'aggiornamento, inserimento ed eliminazione in Linq to SQL O/R Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7fd690997b7d7b58f8d1c1f84ea7f471d4fe496
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089776"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)

Le stored procedure possono essere aggiunti al **O/R Designer** ed eseguito come tipico <xref:System.Data.Linq.DataContext> metodi. Possono inoltre essere utilizzati per sostituire il valore predefinito LINQ al comportamento di runtime SQL che esegue i comandi di inserimento, aggiornamento ed eliminazione durante il salvataggio delle modifiche dalle classi di entità in un database (ad esempio, quando si chiama il <xref:System.Data.Linq.DataContext.SubmitChanges%2A> (metodo)).

> [!NOTE]
> Se le stored procedure restituiscono valori che devono essere inviati al client, ad esempio valori calcolati nelle stesse stored procedure, creare parametri di output all'interno di esse. Se non è possibile usare parametri di output, è preferibile scrivere l'implementazione di un metodo parziale anziché basarsi sugli override generati da Progettazione relazionale oggetti. I membri con mapping ai valori generati dal database devono essere impostati su valori appropriati dopo il completamento delle operazioni INSERT o UPDATE. Per altre informazioni, vedere [responsabilità di sviluppatore nell'override del comportamento predefinito](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL gestisce i valori generati dal database automaticamente per identity (incremento automatico), rowguidcol (GUID generato dal database) e colonne di tipo timestamp. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> al **true** e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> a uno dei seguenti: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert ](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), oppure [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Configurare il comportamento di aggiornamento di una classe di entità

Per impostazione predefinita, la logica per aggiornare un database (inserimenti, aggiornamenti ed eliminazioni) con le modifiche apportate ai dati nelle query LINQ alle classi di entità SQL avviene tramite il runtime LINQ to SQL. Il runtime crea l'impostazione predefinita i comandi INSERT, UPDATE e DELETE che sono basati sullo schema della tabella (colonna e informazioni sulla chiave primarie). Quando il comportamento predefinito non è necessaria, è possibile configurare il comportamento di aggiornamento assegnando stored procedure specifiche per l'esecuzione di comandi di inserimento, aggiornamenti ed eliminazioni necessarie per modificare i dati nella tabella. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Infine, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Per assegnare stored procedure per l'override del comportamento predefinito di una classe di entità

1.  Aprire il **LINQ to SQL** file nella finestra di progettazione. (Fare doppio clic il **dbml** del file in **Esplora soluzioni**.)

2.  Nelle **Esplora Server** oppure **Esplora Database**, espandere **Stored procedure** e individuare le stored procedure che si desidera utilizzare per l'inserimento, aggiornamento e/o eliminazione comandi della classe di entità.

3.  Trascinare la stored procedure nel **O/R Designer**.

     La stored procedure viene aggiunta al riquadro dei metodi come metodo <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Selezionare la classe di entità per cui si desidera usare la stored procedure per eseguire gli aggiornamenti.

5.  Nel **delle proprietà** finestra, selezionare il comando per eseguire l'override (**Inserisci**, **Update**, o **eliminare**).

6.  Fare clic sui puntini di sospensione (...) accanto alle parole **Usa fase di esecuzione** per aprire il **Configura comportamento** nella finestra di dialogo.

7.  Selezionare **personalizzare**.

8.  Selezionare la stored procedure desiderata nel **Personalizza** elenco.

9. Esaminare l'elenco delle **gli argomenti del metodo** e **proprietà della classe** per verificare che il **gli argomenti del metodo** mappa appropriato **proprietà della classe**. Eseguire il mapping degli argomenti di metodo originali (`Original_<ArgumentName>`) alle proprietà originali (`<PropertyName> (Original)`) per il `Update` e `Delete` comandi.

    > [!NOTE]
    > Per impostazione predefinita, viene eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se non vi è più corrispondenza tra i nomi modificati nella tabella e nella classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui la finestra di progettazione non sia in grado di determinare il mapping corretto.

10. Fare clic su **OK** oppure **applicare**.

    > [!NOTE]
    >  È possibile continuare a configurare il comportamento per ogni combinazione classe e il comportamento, purché si fa clic su **applica** dopo ogni modifica apportata. Se si modifica la classe o un comportamento prima di fare clic **applica**, una finestra di dialogo di avviso viene visualizzato e offre la possibilità di applicare le modifiche.

Per ripristinare l'uso della logica di runtime predefinito per gli aggiornamenti, fare clic sui puntini di sospensione accanto al **inserire**, **Update**, o **Elimina** comando il **proprietà**  finestra e quindi selezionare **usare runtime** nel **Configura comportamento** nella finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Inserire, aggiornare ed eliminare operazioni (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)