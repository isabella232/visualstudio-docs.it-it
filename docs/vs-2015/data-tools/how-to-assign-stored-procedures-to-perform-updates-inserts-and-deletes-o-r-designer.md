---
title: 'Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2054a55f0633d5d4add51fee2e933d9f4d829fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609973"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiungere a Progettazione relazionale oggetti stored procedure ed eseguirle come metodi <xref:System.Data.Linq.DataContext> tipici. Possono inoltre essere utilizzati per eseguire l'override del [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] comportamento di runtime predefinito che esegue inserimenti, aggiornamenti ed eliminazioni quando le modifiche vengono salvate dalle classi di entità in un database, ad esempio quando si chiama il <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodo.

> [!NOTE]
> Se le stored procedure restituiscono valori che devono essere inviati al client, ad esempio valori calcolati nelle stesse stored procedure, creare parametri di output all'interno di esse. Se non è possibile usare parametri di output, è preferibile scrivere l'implementazione di un metodo parziale anziché basarsi sugli override generati da Progettazione relazionale oggetti. I membri con mapping ai valori generati dal database devono essere impostati su valori appropriati dopo il completamento delle operazioni INSERT o UPDATE. Per altre informazioni, vedere [responsabilità dello sviluppatore nell'override del comportamento predefinito](https://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] gestisce automaticamente i valori generati dal database per le colonne identity (incremento automatico) e rowguidcol (GUID generato dal database) e timestamp. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno dei seguenti valori: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Configurazione del comportamento di aggiornamento di un classe di entità
 Per impostazione predefinita, la logica per aggiornare un database (comandi di inserimento, aggiornamento ed eliminazione) con le modifiche apportate ai dati nelle classi di entità [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] viene fornita dal runtime [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Il runtime crea comandi di inserimento, aggiornamento ed eliminazione predefiniti basati sullo schema della tabella (la colonna e le informazioni sulla chiave primaria). Quando non si desidera utilizzare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento assegnando stored procedure specifiche per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione necessari per modificare i dati nella tabella. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Infine, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Per assegnare stored procedure per l'override del comportamento predefinito di una classe di entità

1. Aprire il file **LINQ to SQL** nella finestra di progettazione. (Fare doppio clic sul file .dbml in **Esplora soluzioni**.)

2. In **Esplora server** / **Esplora database**espandere **stored procedure** e individuare le stored procedure che si desidera utilizzare per i comandi di inserimento, aggiornamento e/o eliminazione della classe di entità.

3. Trascinare la stored procedure in Progettazione relazionale oggetti.

     La stored procedure viene aggiunta al riquadro dei metodi come metodo <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Selezionare la classe di entità per cui si desidera usare la stored procedure per eseguire gli aggiornamenti.

5. Nella finestra **Proprietà** selezionare il comando di cui eseguire l'override (**Insert**, **Update** o **Delete**).

6. Fare clic sui puntini di sospensione (...) accanto alle parole **Usa fase di esecuzione** per aprire la finestra di dialogo **Configura comportamento**.

7. Selezionare **Personalizza**.

8. Selezionare la stored procedure desiderata nell'elenco **Personalizza**.

9. Controllare l'elenco di **Argomenti metodo** e **Proprietà classe** per verificare che venga eseguito il mapping degli **Argomenti metodo** alle **Proprietà classe** appropriate. Eseguire il mapping degli argomenti del metodo originali (Original_*ArgumentName*) alle proprietà originali (*PropertyName* (originale)) per i comandi Update e DELETE.

    > [!NOTE]
    > Per impostazione predefinita, viene eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se non vi è più corrispondenza tra i nomi modificati nella tabella e nella classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui la finestra di progettazione non sia in grado di determinare il mapping corretto.

10. Fare clic su **OK** o su **Applica**.

    > [!NOTE]
    > È possibile continuare a configurare il comportamento per ogni combinazione di classe/comportamento purché si faccia clic su **Applica** dopo ogni modifica apportata. Se si modifica la classe o il comportamento prima di fare clic su **applica**, viene visualizzata una finestra di dialogo di avviso che consente di applicare le modifiche apportate.

     Per ripristinare l'utilizzo della logica di runtime predefinita per gli aggiornamenti, fare clic sui puntini di sospensione accanto al comando di inserimento, aggiornamento o eliminazione nella finestra **Proprietà** , quindi selezionare **utilizza Runtime** nella finestra di dialogo **Configura comportamento** .

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [metodi DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [procedura dettagliata: creazione di classi LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [operazioni di inserimento, aggiornamento ed eliminazione](https://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)
