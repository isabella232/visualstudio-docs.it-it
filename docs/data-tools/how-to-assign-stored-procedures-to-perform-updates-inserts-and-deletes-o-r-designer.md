---
title: Usare stored procedure in LINQ to SQL per aggiornare i dati
description: Usare le stored procedure in LINQ to SQL Object Relational Designer (O/R Designer) per eseguire aggiornamenti, inserimenti ed eliminazioni di dati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 51cdb3f5af6f77d67cdcd9342e39aca6a5dcf24730cb9565ce5b0404b24e1543
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347168"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (Object Relational Designer)

È possibile aggiungere stored procedure a **Object Relational Designer** ed eseguirle come metodi <xref:System.Data.Linq.DataContext> tipici. Possono anche essere usati per eseguire l'override del comportamento di LINQ to SQL run-time predefinito che esegue inserimenti, aggiornamenti ed eliminazioni quando le modifiche vengono salvate dalle classi di entità in un database , ad esempio quando si chiama il <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodo .

> [!NOTE]
> Se le stored procedure restituiscono valori che devono essere inviati al client, ad esempio valori calcolati nelle stesse stored procedure, creare parametri di output all'interno di esse. Se non è possibile usare parametri di output, è preferibile scrivere l'implementazione di un metodo parziale anziché basarsi sugli override generati da Progettazione relazionale oggetti. I membri con mapping ai valori generati dal database devono essere impostati su valori appropriati dopo il completamento delle operazioni INSERT o UPDATE. Per altre informazioni, vedere [Responsabilità dello sviluppatore in Override del comportamento predefinito](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL gestisce automaticamente i valori generati dal database per le colonne identity (incremento automatico), rowguidcol (GUID generato dal database) e timestamp. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente su true e su uno dei valori <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>  <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> seguenti: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)o [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Configurare il comportamento di aggiornamento di una classe di entità

Per impostazione predefinita, la logica per aggiornare un database (inserimenti, aggiornamenti ed eliminazioni) con le modifiche apportate ai dati nelle classi di entità LINQ to SQL viene fornita dal runtime di LINQ to SQL. Nel runtime vengono creati comandi INSERT, UPDATE, and DELETE predefiniti basati sullo schema della tabella (informazioni sulla colonna e sulla chiave primaria). Quando non si vuole usare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento assegnando stored procedure specifiche per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione necessari per modificare i dati nella tabella. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Infine, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Per assegnare stored procedure per l'override del comportamento predefinito di una classe di entità

1. Aprire il file **LINQ to SQL** nella finestra di progettazione. (Fare doppio clic sul file **.dbml** in **Esplora soluzioni**.)

2. In **Esplora server** o **Esplora database** espandere **Stored procedure** e individuare le stored procedure che si vuole usare per i comandi di inserimento, aggiornamento e/o eliminazione della classe di entità.

3. Trascinare la stored procedure in **Object Relational Designer**.

     La stored procedure viene aggiunta al riquadro dei metodi come metodo <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Selezionare la classe di entità per cui si desidera usare la stored procedure per eseguire gli aggiornamenti.

5. Nella finestra **Proprietà** selezionare il comando di cui eseguire l'override (**Insert**, **Update** o **Delete**).

6. Fare clic sui puntini di sospensione (...) accanto alle parole **Usa fase di esecuzione** per aprire la finestra di dialogo **Configura comportamento**.

7. Selezionare **Personalizza**.

8. Selezionare la stored procedure desiderata nell'elenco **Personalizza**.

9. Controllare l'elenco di **Argomenti metodo** e **Proprietà classe** per verificare che venga eseguito il mapping degli **Argomenti metodo** alle **Proprietà classe** appropriate. Eseguire il mapping degli argomenti del metodo originali ( `Original_<ArgumentName>` ) alle proprietà originali ( ) per i comandi e `<PropertyName> (Original)` `Update` `Delete` .

    > [!NOTE]
    > Per impostazione predefinita, viene eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se non vi è più corrispondenza tra i nomi modificati nella tabella e nella classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui la finestra di progettazione non sia in grado di determinare il mapping corretto.

10. Fare clic su **OK** o su **Applica**.

    > [!NOTE]
    > È possibile continuare a configurare il comportamento per ogni combinazione di classe e comportamento, purché si fa clic su Applica **dopo** aver apportato ogni modifica. Se si modifica la classe o il comportamento prima di fare clic **su Applica**, viene visualizzata una finestra di dialogo di avviso che offre la possibilità di applicare le modifiche.

Per ripristinare l'uso della logica di runtime predefinita per gli aggiornamenti, fare clic sui puntini di sospensione accanto al comando **Insert**, **Update** o **Delete** nella finestra **Proprietà** e quindi selezionare **Usa fase di esecuzione** nella finestra di dialogo **Configura comportamento**.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Operazioni di inserimento, aggiornamento ed eliminazione (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
