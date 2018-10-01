---
title: 'Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O-R Designer) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a211048e287bd3ef3e45625022f7389e06358e32
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529545"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O-R Designer)](https://docs.microsoft.com/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer).  
  
  
È possibile aggiungere a Progettazione relazionale oggetti stored procedure ed eseguirle come metodi <xref:System.Data.Linq.DataContext> tipici. Possono inoltre essere utilizzati per sostituire il valore predefinito [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] comportamento di runtime che esegue i comandi di inserimento, aggiornamento ed eliminazione durante il salvataggio delle modifiche dalle classi di entità in un database (ad esempio, quando si chiama il <xref:System.Data.Linq.DataContext.SubmitChanges%2A> (metodo)).  
  
> [!NOTE]
>  Se le stored procedure restituiscono valori che devono essere inviati al client, ad esempio valori calcolati nelle stesse stored procedure, creare parametri di output all'interno di esse. Se non è possibile usare parametri di output, è preferibile scrivere l'implementazione di un metodo parziale anziché basarsi sugli override generati da Progettazione relazionale oggetti. I membri con mapping ai valori generati dal database devono essere impostati su valori appropriati dopo il completamento delle operazioni INSERT o UPDATE. Per altre informazioni, vedere [responsabilità di sviluppatore nell'override del comportamento predefinito](http://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] gestisce automaticamente i valori generati dal database per le colonne identity (incremento automatico) e rowguidcol (GUID generato dal database) e timestamp. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno dei seguenti valori: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Configurazione del comportamento di aggiornamento di un classe di entità  
 Per impostazione predefinita, la logica per aggiornare un database (comandi di inserimento, aggiornamento ed eliminazione) con le modifiche apportate ai dati nelle classi di entità [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] viene fornita dal runtime [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Nel runtime vengono creati comandi di inserimento, aggiornamento ed eliminazione predefiniti basati sullo schema della tabella (informazioni sulla colonna e sulla chiave primaria). Quando non si desidera utilizzare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento assegnando stored procedure specifiche per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione necessari per modificare i dati nella tabella. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Infine, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Per assegnare stored procedure per l'override del comportamento predefinito di una classe di entità  
  
1.  Aprire il **LINQ to SQL** file nella finestra di progettazione. (Fare doppio clic sul file. dbml in **Esplora soluzioni**.)  
  
2.  Nelle **Esplora Server**/**Database Explorer**, espandere **Stored Procedures** e individuare le stored procedure che si desidera utilizzare per l'inserimento, aggiornamento, e/o eliminare i comandi della classe di entità.  
  
3.  Trascinare la stored procedure in Progettazione relazionale oggetti.  
  
     La stored procedure viene aggiunta al riquadro dei metodi come metodo <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Selezionare la classe di entità per cui si desidera usare la stored procedure per eseguire gli aggiornamenti.  
  
5.  Nel **delle proprietà** finestra, selezionare il comando per eseguire l'override (**Inserisci**, **Update**, o **eliminare**).  
  
6.  Fare clic sui puntini di sospensione (...) accanto alle parole **Usa fase di esecuzione** per aprire il **Configura comportamento** nella finestra di dialogo.  
  
7.  Selezionare **personalizzare**.  
  
8.  Selezionare la stored procedure desiderata nel **Personalizza** elenco.  
  
9. Esaminare l'elenco delle **gli argomenti del metodo** e **proprietà della classe** per verificare che il **gli argomenti del metodo** mappa appropriato **proprietà della classe**. Eseguire il mapping degli argomenti di metodo originali (Original _*NomeArgomento*) alle proprietà originali (*PropertyName* (Original)) per i comandi Update e Delete.  
  
    > [!NOTE]
    >  Per impostazione predefinita, viene eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se non vi è più corrispondenza tra i nomi modificati nella tabella e nella classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui la finestra di progettazione non sia in grado di determinare il mapping corretto.  
  
10. Fare clic su **OK** oppure **applicare**.  
  
    > [!NOTE]
    >  È possibile continuare a configurare il comportamento per ogni combinazione classe/comportamento purché faccia clic su **applica** dopo ogni modifica apportata. Se si modifica la classe o un comportamento prima di fare clic **applica**, una finestra di dialogo di avviso che fornisce un'opportunità per applicare eventuali modifiche verrà visualizzati.  
  
     Per ripristinare l'uso della logica di runtime predefinito per gli aggiornamenti, fare clic sui puntini di sospensione accanto a Insert, Update, o eliminare i comandi nel **delle proprietà** finestra e quindi selezionare **usare runtime** nel  **Configurare il comportamento** nella finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Procedura dettagliata: Creazione di aggiornamento Stored procedure per la tabella Customers Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Operazioni di inserimento, aggiornamento ed eliminazione](http://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)

